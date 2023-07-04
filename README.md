# Spring-RESTfulApisWith-HATEOS-HAL
This is a hobby project(6) to learn Java-Spring Boot and RESTful-API's conforming to the standards of HATEOS by creating `Payroll+Orders app`.

I built REST API's using Spring MVC + Spring HATEOAS app with HAL representations of each resource.
This project is based on [Building REST services with Spring course](https://spring.io/guides/tutorials/rest/)


## Whats used?
Java + Spring Boot



## Objectives

Create a nonREST API's — Simple Spring MVC app with no hypermedia

Make the API's RESTful — Spring MVC + Spring HATEOAS app with HAL representations of each resource

Introduce backward compactability — REST app where a field is evolved but old data is retained for backward compatibility

Add conditional link in responses. — REST app where conditional links are used to signal valid state changes to clients

## How to run the program?

`$ git clone https://github.com/rasi5050/Spring-RESTfulApisWith-HATEOS-HAL`

`$ cd Spring-RESTfulApisWith-HATEOS-HAL`

`$  ./mvnw clean spring-boot:run`

## Endpoints

### General Error Response

```json
{
    "timestamp": "2023-07-04T17:58:07.991+00:00",
    "status": 404,
    "error": "Not Found",
    "path": "/employees/76"
}
```

### `GET localhost:8080/employees`

#### Success Response Body

```json
{
    "_embedded": {
        "employeeList": [
            {
                "id": 1,
                "firstName": "Bilbo",
                "lastName": "Baggins",
                "role": "burglar",
                "name": "Bilbo Baggins",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/employees/1"
                    },
                    "employees": {
                        "href": "http://localhost:8080/employees"
                    }
                }
            },
            {
                "id": 2,
                "firstName": "Frodo",
                "lastName": "Baggins",
                "role": "thief",
                "name": "Frodo Baggins",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/employees/2"
                    },
                    "employees": {
                        "href": "http://localhost:8080/employees"
                    }
                }
            }
        ]
    },
    "_links": {
        "self": {
            "href": "http://localhost:8080/employees"
        }
    }
}
```

### `GET localhost:8080/employees/1`

#### Success Response Body

```json
{
    "id": 1,
    "firstName": "Bilbo",
    "lastName": "Baggins",
    "role": "burglar",
    "name": "Bilbo Baggins",
    "_links": {
        "self": {
            "href": "http://localhost:8080/employees/1"
        },
        "employees": {
            "href": "http://localhost:8080/employees"
        }
    }
}
```

### `POST localhost:8080/employees`

#### Request Body

```json
{
    "name": "Alfred Hitchcock",
    "role": "filmmaker"
}
```

#### Success Response Body

```json
{
    "id": 3,
    "firstName": "Alfred",
    "lastName": "Hitchcock",
    "role": "filmmaker",
    "name": "Alfred Hitchcock",
    "_links": {
        "self": {
            "href": "http://localhost:8080/employees/3"
        },
        "employees": {
            "href": "http://localhost:8080/employees"
        }
    }
}
```

### `PUT localhost:8080/employees/3`

#### Request Body

```json
{
    "name": "Samwise Gamgee",
    "role": "ring bearer"
}
```

#### Success Response Body

```json
{
    "id": 3,
    "firstName": "Samwise",
    "lastName": "Gamgee",
    "role": "ring bearer",
    "name": "Samwise Gamgee",
    "_links": {
        "self": {
            "href": "http://localhost:8080/employees/3"
        },
        "employees": {
            "href": "http://localhost:8080/employees"
        }
    }
}
```
### `DELETE localhost:8080/employees/3`

#### Success Response 

204 No Content



### `GET localhost:8080/orders`

#### Success Response Body

```json
{
    "_embedded": {
        "orderList": [
            {
                "id": 1,
                "description": "MacBook Pro",
                "status": "COMPLETED",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/orders/1"
                    },
                    "orders": {
                        "href": "http://localhost:8080/orders"
                    }
                }
            },
            {
                "id": 2,
                "description": "iPhone",
                "status": "IN_PROGRESS",
                "_links": {
                    "self": {
                        "href": "http://localhost:8080/orders/2"
                    },
                    "orders": {
                        "href": "http://localhost:8080/orders"
                    },
                    "cancel": {
                        "href": "http://localhost:8080/orders/2/cancel"
                    },
                    "complete": {
                        "href": "http://localhost:8080/orders/2/complete"
                    }
                }
            }
        ]
    },
    "_links": {
        "self": {
            "href": "http://localhost:8080/orders"
        }
    }
}
```

### `DELETE localhost:8080/orders/2/cancel`

#### Success Response Body

```json
{
    "id": 2,
    "description": "iPhone",
    "status": "CANCELLED",
    "_links": {
        "self": {
            "href": "http://localhost:8080/orders/2"
        },
        "orders": {
            "href": "http://localhost:8080/orders"
        }
    }
}
```
#### Failure Response Body
```json
{
    "title": "Method not allowed",
    "detail": "You can't cancel an order that is in CANCELLED status"
}
```
### `PUT localhost:8080/orders/2/complete`

#### Success Response Body

```json
{
    "id": 2,
    "description": "iPhone",
    "status": "COMPLETED",
    "_links": {
        "self": {
            "href": "http://localhost:8080/orders/2"
        },
        "orders": {
            "href": "http://localhost:8080/orders"
        }
    }
}
```
#### Failure Response Body
```json
{
    "title": "Method not allowed",
    "detail": "You cant complete an order that is in CANCELLED status"
}
```

## Screenshots
<img width="1512" alt="Screenshot 2023-07-04 at 14 40 57" src="https://github.com/rasi5050/Spring-RESTfulApisWith-HATEOS-HAL/assets/12760472/7a419af3-03c8-42d5-9bb2-028fa682c143">
<img width="1512" alt="Screenshot 2023-07-04 at 14 43 40" src="https://github.com/rasi5050/Spring-RESTfulApisWith-HATEOS-HAL/assets/12760472/02b9f87f-d19a-40ab-b6b7-7a534d602c74">


## Thanks!
