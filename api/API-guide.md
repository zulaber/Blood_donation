# REST API documentation

> All endpoints explained

## Login

Use API as admin:

login: admin

password: admin

Token: d5c46c545a579513e88456bd8a85aee36e7a646f

## Endpoints

| URI                                  | GET                                                                | POST                   | PUT                | DELETE             |
| ------------------------------------ | ------------------------------------------------------------------ | ---------------------- | ------------------ | ------------------ |
| [/api/v1/](#URIs_list)               | Returns a list of links to the other available URIs                | N/A                    | N/A                | N/A                |
| [/api/get-token](#Token)             | N/A                                                                | Returns token for user | N/A                | N/A                |
| [/api/v1/public/](#Public)           | Returns informations about current state of bloods in all branches | N/A                    | N/A                | N/A                |
| [/api/v1/public/{branch}](#Public)   | Returns informations about current state of bloods in branch       | N/A                    | N/A                | N/A                |
| [/api/v1/users/](#Users)             | Returns a list of users                                            | N/A                    | N/A                | N/A                |
| [/api/v1/users/{id}](#Users)         | Returns a user                                                     | N/A                    | N/A                | N/A                |
| [/api/v1/patients/](#Patients)       | Returns a list of patients                                         | Creates a new patient  | N/A                | N/A                |
| [/api/v1/patients/{id}](#Patients)   | Returns the details of a single patient                            | N/A                    | Updates a patient  | Deletes a patient  |
| [/api/v1/donations/](#Donations)     | Returns a list of donations                                        | Creates a new donation | N/A                | N/A                |
| [/api/v1/donations/{id}](#Donations) | Returns the details of a single donation                           | N/A                    | Updates a donation | Deletes a donation |

### URIs_list

#### Single example:

```
{
    "patients": "https://blood-dontaion.herokuapp.com/api/v1/patients/",
    "donations": "https://blood-dontaion.herokuapp.com/api/v1/donations/",
    "users": "https://blood-dontaion.herokuapp.com/api/v1/users/",
    "public": "https://blood-dontaion.herokuapp.com/api/v1/public/"
}
```

| URI        | Method     | **GET** |
| ---------- | ---------- | ------- |
| `/api/v1/` | Permission | All     |

> GET

Returns list of avalible URIs.

### Token

#### Single example:

```
{
    "token": "dee9a966e4fe39abf1e59b9e950d28632e4454f6"
}
```

#### Permissible Fields

| Element / Attribute | POST     |
| ------------------- | -------- |
| **username**        | Required |
| **password**        | Required |

| URI              | Method     | **POST** |
| ---------------- | ---------- | -------- |
| `/api/get-token` | Permission | All      |

> POST

Returns token for user.

### Public

#### Single example:

```
{
    "Branch": "Lublin",
    "percentage_blood_share": {
        "A Rh+": 34.69,
        ...
        "B Rh-": 0.86
    },
    "state_of_blood_supply": {
        "A Rh+": 100,
        ...
        "B Rh-": 6.88
    }
}
```

| URI               | Method     | **GET** |
| ----------------- | ---------- | ------- |
| `/api/v1/public/` | Permission | All     |

> GET

Returns informations about current state of bloods in all branches.

| URI                       | Method     | **GET** |
| ------------------------- | ---------- | ------- |
| `/api/v1/public/{branch}` | Permission | All     |

> GET

Returns informations about current state of bloods in branch.

### Users

#### Single example:

```
{
    "id": 12,
    "username": "c",
    "first_name": "Amine",
    "last_name": "Rutkowski",
    "email": "dtzfawwbd@123mail.cl",
    "position": "habilitated doctor",
    "branch": "Radom",
    "image": "https://blood-donation-live.s3.eu-west-2.amazonaws.com/profile_image/c.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVGRKEV6O54SLRAVI%2F20200609%2Feu-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200609T125348Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=c5fdf899436a2e178ed70742d1b7c81929e445a333bd8a22afdf57ee17873919"
}
```

#### Sortable Fields

| Filter        | Type    | lookups          | Description                                                      |
| ------------- | ------- | ---------------- | ---------------------------------------------------------------- |
| **search**    | String  | SearchFilter     | Search given value in: username, last_name, email, branch        |
| **fields**    | String  | Selective fields | Returns only selected fields                                     |
| **omit**      | String  | Selective fields | Returns all fields except omitted ones                           |
| **page**      | Integer | Pagination       | Returns page                                                     |
| **page_size** | Integer | Pagination       | Returns number of records on page (default=50, max_page_size=500 |

| URI              | Method     | **GET** |
| ---------------- | ---------- | ------- |
| `/api/v1/users/` | Permission | Users   |

> GET

Returns list of users with branch, position and image.

| URI                  | Method     | **GET** |
| -------------------- | ---------- | ------- |
| `/api/v1/users/{id}` | Permission | Users   |

> GET

Returns informations about user.

### Patients

#### Single example:

```
{
    "id": 32,
    "first_name": "Tatiana",
    "last_name": "Michalak",
    "pesel": 80122570223,
    "blood_group": "0 Rh+",
    "gender": "female",
    "email": "ff@caltanet.it",
    "phone_number": "+48774526954",
    "date_of_register": "1998-12-26",
    "registered_by": {
        "id": 17,
        "username": "eciw",
        "first_name": "Lara",
        "last_name": "Michalska",
        "email": "bguyleiy@mailchoose.co",
        "position": "habilitated doctor",
        "branch": "Radom",
        "image": "https://blood-donation-live.s3.eu-west-2.amazonaws.com/profile_image/eciw.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVGRKEV6O54SLRAVI%2F20200610%2Feu-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200610T093658Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=806ab15b536c2bf0129e3d153c2fe52adc72969207dc9269e566bd53044bbe6b"
    },
    "can_donate": false,
    "donation_set": [
        {
            "id": 1117,
            "date_of_donation": "1998-12-26",
            "accept_donate": true,
            "refuse_information": null,
            "medical_staff": 5
        },
        ...
    ]
}
```

#### Permissible Fields

| Element / Attribute  | PUT       | POST      |
| -------------------- | --------- | --------- |
| **id**               | Forbidden | Forbidden |
| **first_name**       | Required  | Required  |
| **last_name**        | Required  | Required  |
| **pesel**            | Required  | Required  |
| **blood_group**      | Required  | Required  |
| **gender**           | Required  | Required  |
| **email**            | Allowed   | Allowed   |
| **phone_number**     | Allowed   | Allowed   |
| **date_of_register** | Forbidden | Forbidden |
| **can_donate**       | Forbidden | Forbidden |
| **registered_by**    | Forbidden | Forbidden |

#### Sortable Fields

| Filter               | Type                                                                     | lookups                                              | Description                                                              |
| -------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------------------ |
| **id**               | Integer                                                                  | exact, in                                            | Django’s built-in lookup                                                 |
| **first_name**       | String                                                                   | exact, icontains                                     | Django’s built-in lookup                                                 |
| **last_name**        | String                                                                   | exact, icontains                                     | Django’s built-in lookup                                                 |
| **pesel**            | Integer(BigIntegerField)                                                 | exact, icontains                                     | Django’s built-in lookup                                                 |
| **blood_group**      | String(chocies: 0 Rh+, A Rh+, B Rh+, AB Rh+, 0 Rh-, A Rh-, B Rh-, B Rh-) | exact, icontains                                     | Django’s built-in lookup                                                 |
| **gender**           | String(chocies: male, female)                                            | exact                                                | Django’s built-in lookup                                                 |
| **email**            | String(EmailField)                                                       | exact, icontains                                     | Django’s built-in lookup                                                 |
| **phone_number**     | Integer(PhoneNumberField)                                                | exact, icontains                                     | Django’s built-in lookup                                                 |
| **date_of_register** | Date                                                                     | exact, icontains, gt, gte, lt, lte, year, month, day | Django’s built-in lookup                                                 |
| **can_donate**       | BooleanField                                                             | exact                                                | Django’s built-in lookup                                                 |
| **registered_by**    | Integer                                                                  | exact                                                | Django’s built-in lookup                                                 |
| **search**           | String                                                                   | icontains                                            | Search given value in: first_name, last_name, pesel, email, phone_number |
| **fields**           | String                                                                   | Selective fields                                     | Returns only selected fields                                             |
| **omit**             | String                                                                   | Selective fields                                     | Returns all fields except omitted ones                                   |
| **page**             | Integer                                                                  | Pagination                                           | Returns page                                                             |
| **page_size**        | Integer                                                                  | Pagination                                           | Returns number of records on page (default=200, max_page_size=1000       |

| URI                 | Method     | **GET** | **POST** |
| ------------------- | ---------- | ------- | -------- |
| `/api/v1/patients/` | Permission | Users   | Users    |

> GET

Returns list of Patients with all of their donations and medical employee responsible for register, also there is added dynamic field which returns information if the current Patient can donate

> POST

Adds new Patient (date_of_register and registered_by are done automatically)

| URI                     | Method     | **GET** | **PUT** | **DELETE**  |
| ----------------------- | ---------- | ------- | ------- | ----------- |
| `/api/v1/patients/{id}` | Permission | Users   | Users   | Admin/staff |

> GET

Returns detaiil information about Patient with all of his/her donations and medical employee responsible for register, also there is added dynamic field which returns information if the Patient can donate.

> PUT

Updates Patient.

> DELETE

Deletes Patient.

### Donations

#### Single example:

```
{
    "medical_staff": {
        "id": 66,
        "username": "qv",
        "first_name": "Daniil",
        "last_name": "Malinowski",
        "email": "txum@mail2norway.com",
        "position": "doctor",
        "branch": "Warszawa",
        "image": "https://blood-donation-live.s3.eu-west-2.amazonaws.com/profile_image/qv.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVGRKEV6O54SLRAVI%2F20200610%2Feu-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200610T094219Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=0a8181aa95dc65351f5b8fcd1c41d993a5e6b77a28f8761b2640ce3f03fd03f1"
    },
    "patient": {
        "id": 906,
        "first_name": "Tuankiet",
        "last_name": "Stępień",
        "blood_group": "0 Rh+",
        "phone_number": "+48869751946",
        "registered_by": 30
    },
    "date_of_donation": "1948-11-25",
    "accept_donate": true,
    "refuse_information": null
}
```

#### Permissible Fields

| Element / Attribute    | PUT       | POST      |
| ---------------------- | --------- | --------- |
| **id**                 | Forbidden | Forbidden |
| **medical_staff**      | Forbidden | Forbidden |
| **patient**            | Required  | Required  |
| **date_of_donation**   | Forbidden | Forbidden |
| **accept_donate**      | Required  | Required  |
| **refuse_information** | Allowed   | Allowed   |

#### Sortable Fields

| Filter                 | Type         | lookups                                              | Description                                                        |
| ---------------------- | ------------ | ---------------------------------------------------- | ------------------------------------------------------------------ |
| **id**                 | Integer      | in                                                   | Django’s built-in lookup                                           |
| **medical_staff**      | Integer      | exact                                                | Django’s built-in lookup                                           |
| **patient**            | Integer      | exac                                                 | Django’s built-in lookup                                           |
| **date_of_donation**   | Date         | exact, icontains, gt, gte, lt, lte, year, month, day | Django’s built-in lookup                                           |
| **accept_donate**      | BooleanField | exact                                                | Django’s built-in lookup                                           |
| **refuse_information** | String       | icontains                                            | Django’s built-in lookup                                           |
| **fields**             | String       | Selective fields                                     | Returns only selected fields                                       |
| **omit**               | String       | Selective fields                                     | Returns all fields except omitted ones                             |
| **page**               | Integer      | Pagination                                           | Returns page                                                       |
| **page_size**          | Integer      | Pagination                                           | Returns number of records on page (default=250, max_page_size=2000 |

| URI                  | Method     | **GET** | **POST** |
| -------------------- | ---------- | ------- | -------- |
| `/api/v1/donations/` | Permission | Users   | Users    |

> GET

Returns list of Donations.

> POST

Adds new Donation (date_of_donation and medical_staff are done automatically)

| URI                      | Method     | **GET** | **PUT**     | **DELETE**  |
| ------------------------ | ---------- | ------- | ----------- | ----------- |
| `/api/v1/donations/{id}` | Permission | Users   | Admin/staff | Admin/staff |

> GET

Returns detaiil information about Donation, patient and medical employee.

> PUT

Updates Donation.

> DELETE

Deletes Donation.
