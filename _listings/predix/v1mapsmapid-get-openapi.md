---
swagger: "2.0"
x-collection-name: Predix
x-complete: 0
info:
  title: Predix Intelligent Mapping Return map details
  description: |-
    For the specified map identifier, returns the map properties and an
    array of the associated layers. For each layer, the identifier, name and
    Uniform Resource Identifier (URI) are returned.
  version: 1.0.0
host: insights-api.data-services.predix.io
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /api/v2/config/orchestrations/artifacts:
    post:
      summary: Upload an artifact and attach it to an orchestration configuration
        entry.
      description: Upload a single artifact file in a multipart MIME structure and
        attach it to an orchestration configuration entry. The multipart MIME structure
        must have the orchestration entry id tagged as 'orchestrationEntryId',  the
        file contents tagged as 'file',  the artifact type tagged as 'type', and  the
        name of artifact tagged as 'name'.  A description (under 1024 characters)
        tagged as 'description' can be optionally specified. Artifact types can be
        either 'portToFieldMap', 'bpmn' or any.   If the artifact type is 'portToFieldMap',
        specify the orchestration step ID tagged as 'stepId'.   Otherwise, 'name'
        will be used as 'stepId'.  (See the documentation for more information regarding
        these files.)
      operationId: uploadOrchConfigArtifact
      x-api-path-slug: apiv2configorchestrationsartifacts-post
      parameters:
      - in: header
        name: Authorization
        description: Authorization
      - in: formData
        name: description
        description: Artifact description
      - in: formData
        name: file
        description: (Required) Artifact file
      - in: formData
        name: name
        description: (Required) Artifact name
      - in: formData
        name: orchestrationEntryId
        description: (Required) orchestration configuration entry id
      - in: header
        name: Predix-Zone-Id
        description: Predix-Zone-Id
      - in: formData
        name: stepId
        description: Orchestration Step ID
      - in: formData
        name: type
        description: (Required) Artifact type
      responses:
        2:
          description: Successful response
        200:
          description: Successful response
      tags:
      - Upload
      - Artifact
      - Attach
      - It
      - To
      - Orchestration
      - Configuration
      - Entry
  /api/v2/config/orchestrations/artifacts/{id}:
    put:
      summary: Update an artifact by id.
      description: Update the artifact of the orchestration configuration with the
        contents of the supplied multipart MIME structure. The multipart MIME structure
        may have new file contents tagged as 'file',  new artifact type tagged as
        'type',  new name of artifact tagged as 'name',  new description (under 1024
        characters) tagged as 'description', and  new value of the orchestration step
        id tagged as 'stepId.   Artifact types can be either 'portToFieldMap', 'bpmn'
        or any.  (See the documentation for more information regarding these files.)
      operationId: updateOrchConfigArtifact
      x-api-path-slug: apiv2configorchestrationsartifactsid-put
      parameters:
      - in: header
        name: Authorization
        description: Authorization
      - in: formData
        name: description
        description: Artifact description
      - in: formData
        name: file
        description: Artifact file
      - in: path
        name: id
        description: Artifact id
      - in: formData
        name: name
        description: Artifact name
      - in: header
        name: Predix-Zone-Id
        description: Predix-Zone-Id
      - in: formData
        name: stepId
        description: Orchestration Step ID
      - in: formData
        name: type
        description: Artifact type
      responses:
        2:
          description: Successful response
        200:
          description: Successful response
      tags:
      - Artifact
      - By
      - Id
  /api/v2/config/orchestrations/{id}/file:
    get:
      summary: Download an orchestration artifact file by orchestration id and artifact
        type.
      description: The file is downloaded as an octet-stream. If the type is bpmn,
        then then bpmn xml is downloaded. If the type is portToFieldMap, then the
        system expects analyticStepId to download the portToFieldMap for the given
        step
      operationId: downloadArtifactByType
      x-api-path-slug: apiv2configorchestrationsidfile-get
      parameters:
      - in: header
        name: Authorization
        description: Authorization
      - in: path
        name: id
        description: orchestration configuration entry id
      - in: query
        name: name
        description: artifact name (analytic step id)
      - in: header
        name: Predix-Zone-Id
        description: Predix-Zone-Id
      - in: query
        name: type
        description: artifact type (Ex
      responses:
        2:
          description: Successful response
        200:
          description: Successful response
      tags:
      - Download
      - Orchestration
      - Artifact
      - File
      - By
      - Orchestration
      - Id
      - Artifact
      - Type
  /v1/maps:
    post:
      summary: Create a map
      description: Creates a map with the specified name.
      operationId: creates-a-map-with-the-specified-name
      x-api-path-slug: v1maps-post
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Map
    get:
      summary: List all maps for a customer
      description: |-
        Returns an array of maps for the specified customer. The array contains
        the name and identifier for each map.
      operationId: returns-an-array-of-maps-for-the-specified-customer-the-array-containsthe-name-and-identifier-for-ea
      x-api-path-slug: v1maps-get
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - List
      - ""
      - Mapsa
      - Customer
  /v1/maps/{mapId}:
    get:
      summary: Return map details
      description: |-
        For the specified map identifier, returns the map properties and an
        array of the associated layers. For each layer, the identifier, name and
        Uniform Resource Identifier (URI) are returned.
      operationId: for-the-specified-map-identifier-returns-the-map-properties-and-anarray-of-the-associated-layers-for
      x-api-path-slug: v1mapsmapid-get
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Return
      - Map
      - Details
    delete:
      summary: Delete a map
      description: |-
        Deletes the map with the specified identifier. Any layers associated
        with the map are also deleted.
      operationId: deletes-the-map-with-the-specified-identifier-any-layers-associatedwith-the-map-are-also-deleted
      x-api-path-slug: v1mapsmapid-delete
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Map
    put:
      summary: Rename a map
      description: Updates the name of the map that has the specified identifier.
      operationId: updates-the-name-of-the-map-that-has-the-specified-identifier
      x-api-path-slug: v1mapsmapid-put
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Rename
      - Map
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---