---
title: PelotonZap API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the PelotonZap API
---

# Introduction

Welcome to the PelotonZap API documentation.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> Authorization header example:

```shell
curl "api_endpoint_here" \
  --header "Authorization: Bearer qwertyuiopasdfghjkl"
```

> Make sure to replace `qwertyuiopasdfghjkl` with your API key.

PelotonZap uses API keys to allow access to the API. An API key can be obtained by [registering](https://www.pelotonzap.io/register) for an account and creating a key.

PelotonZap expects the API key to be included in all API requests to the server in an `Authorization` header as a Bearer token:

`Authorization: Bearer qwertyuiopasdfghjkl`

<aside class="notice">
You must replace <code>qwertyuiopasdfghjkl</code> with your personal API key.
</aside>

# User

## Get Current User

```shell
curl --location --request GET 'https://api.pelotonzap.io/user' \
--header 'Authorization: Bearer 36|Krc1ED0YfBamYWmyH2aoueoxdCNzjVc4IEgfaiOy'
```

> The above command returns JSON structured like this:

```json
{
    "id": 21,
    "name": "Some User",
    "email": "someuser@email.com",
    "email_verified_at": null,
    "two_factor_secret": null,
    "two_factor_recovery_codes": null,
    "created_at": "2021-11-17T05:25:51.000000Z",
    "updated_at": "2021-12-16T05:09:15.000000Z"
}
```

Retrieve the current user (identified by API Key).

### HTTP Request

`GET https://api.pelotonzap.io/user`

# Workout

## Get Workouts

```shell
curl --location --request GET 'https://api.pelotonzap.io/api/v1/workouts' \
--header 'Accept: application/vnd.api+json' \
--header 'Content-Type: application/vnd.api+json' \
--header 'Authorization: Bearer 36|Krc1ED0YfBamYWmyH2aoueoxdCNzjVc4IEgfaiOy'
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "type": "workouts",
      "id": "181",
      "attributes": {
        "createdAt": "2021-12-17T05:40:41.000000Z",
        "updatedAt": "2021-12-17T05:40:41.000000Z",
        "pelotonId": "e43bfda89ab541ae97821f295a8b1903"
      },
      "links": {
        "self": "https://api.pelotonzap.io/api/v1/workouts/181"
      }
    },
    {
      "type": "workouts",
      "id": "182",
      "attributes": {
        "createdAt": "2021-12-17T05:40:41.000000Z",
        "updatedAt": "2021-12-17T05:40:41.000000Z",
        "pelotonId": "5c01724c4cca4bbf90bc2e0815360855"
      },
      "links": {
        "self": "https://api.pelotonzap.io/api/v1/workouts/182"
      }
    }
  ]
}
```

Retrieve all the workouts for the current user (identified by API Key).

### HTTP Request

`GET http://api.pelotonzap.io/api/v1/workouts`

## Queue Workout

```shell
curl --location --request POST 'https://api.pelotonzap.io/queue/181' \
--header 'Accept: application/vnd.api+json' \
--header 'Content-Type: application/vnd.api+json' \
--header 'X-XSRF-TOKEN: eyJpdiI6IlJ4VEtrUTlzemt6cktKSTRnUjZSTnc9PSIsInZhbHVlIjoiUG52eXlTNUJFUG43YlVlYm4wekpXTm5vRjZJUE8wSTlFRnBXK0NVZzZZeTFEdUxRWFhEWVRQclQ4UlVpbWNPVVJ0YTQxcENabHdWeGxubkU2U0hSNWFCa0drQm5MSVhlMXdrOEdJemw0emZLbzlNUXRsQXhSU2RVRTFRaXNYWmsiLCJtYWMiOiI0YTUwODgwMjk0OTg2YWU0Yzg4Yzc5NjE2ZjJmNDQ1M2U4M2Q0OWUxNmMyYjc3ZjM3NTIyMzQ2ZDMyZTM0M2YzIiwidGFnIjoiIn0=' \
--header 'Authorization: Bearer 36|Krc1ED0YfBamYWmyH2aoueoxdCNzjVc4IEgfaiOy'
```

> The above command returns JSON structured like this:

```json

```

Requeue a `workout` to be sent to Zapier.

Parameter | Required | Description
--------- |----------| -----------
id | true     | `workout` identifier

### HTTP Request

`POST https://api.pelotonzap.io/queue/{workout.id}`
