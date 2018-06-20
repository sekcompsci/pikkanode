# Pikkanode API routes

## POST /auth/signup

Sign up new user.

* Content-Type: application/json

```json
{
    "email": "test@example.com",
    "password": "password 1234 lol gg ezez!!!!",
}
```

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns the empty object.

```json
{}
```

### Example error response

* Status: 400
* Content-Type: application/json; charset=utf-8

Returns the error message if signup failed

```json
{
    "error": "email already used"
}
```

### Example error response

* Status: 400
* Content-Type: application/json; charset=utf-8

Returns the error message if email is invalid

```json
{
    "error": "invalid email"
}
```

---

## POST /auth/signin

Sign in user.

* Content-Type: application/json

```json
{
    "email": "test@example.com",
    "password": "password 1234 lol gg ezez!!!!"
}
```

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns the empty object.

```json
{}
```

### Example error response

* Status: 400
* Content-Type: application/json; charset=utf-8

Returns the error message if sign in failed

```json
{
    "error": "wrong email or password"
}
```

---

## POST /auth/signout

Sign out user.

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns the empty object.

```json
{}
```

---

## GET /pikka

list all pikkas

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns pikka list

```json
{
    pikkas: [
        {
            "id": 1,
            "caption": "หน้าตาอย่างน้อง ควรมีพี่เป็นเจ้าของนะครับ ☺️",
            "picture": "http://localhost:3000/-/images/d620cb37-797f-48b5-9b3c-865229921ac5",
            "createdAt": "2018-06-14T11:32:24.000Z",
            "commentCount": 12,
            "likeCount": 5
        },
        {
            "id": 2,
            "caption": "Pikkanode is the best",
            "picture": "http://localhost:3000/-/images/fca5f3cf-7f88-47a7-b42b-542d80a37d9d",
            "createdAt": "2018-06-19T12:32:14.000Z",
            "commentCount": 2,
            "likeCount": 10
        }
    ]
}
```

---

## POST /pikka

Create new pikka

* Content-Type: multipart/form-data

```
Content-Disposition: form-data; name="caption"

some caption

Content-Disposition: form-data; name="picture"; filename="test.png"
Content-Type: image/png

(content of the uploaded file test.png)
```

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns created pikka id and create time

```json
{
    "pikkaId": 43,
    "createdAt": "2018-06-19T10:33:12.000Z",
}
```

### Example error response

* Status: 401
* Content-Type: application/json; charset=utf-8

Returns the error message if user is not signed in

```json
{
    "error": "unauthorized"
}
```

---

## GET /pikka/:id

get pikka detail by given id

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns pikka detail

```json
{
    pikka: {
            "id": 2,
            "caption": "Pikkanode is the best",
            "picture": "http://localhost:3000/-/images/fca5f3cf-7f88-47a7-b42b-542d80a37d9d",
            "createdAt": "2018-06-19T12:32:14.000Z",
            "likeCount": 10,
            "comments": [
                {
                    "id": 221,
                    "text": "yeah!",
                    "createdAt": "2018-06-20T10:32:04.000Z"
                },
                {
                    "id": 229,
                    "text": "very good",
                    "createdAt": "2018-06-21T10:33:12.000Z"
                }
            ]
        }
}
```

---

## POST /pikka/:id/comment

create a new comment on given pikka id

* Content-Type: application/json

```json
{
    "text": "I love this pikka"
}
```

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns created comment id and create time

```json
{
    "commentId": 43,
    "createdAt": "2018-06-19T10:33:12.000Z",
}
```

### Example error response

* Status: 401
* Content-Type: application/json; charset=utf-8

Returns the error message if user is not signed in

```json
{
    "error": "unauthorized"
}
```

### Example error response

* Status: 400
* Content-Type: application/json; charset=utf-8

Returns the error message if pikka not exists

```json
{
    "error": "invalid request"
}
```

---

## PUT /pikka/:id/like

Like a pikka

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns the empty object

```json
{}
```

### Example error response

* Status: 401
* Content-Type: application/json; charset=utf-8

Returns the error message if user is not signed in

```json
{
    "error": "unauthorized"
}
```

### Example error response

* Status: 400
* Content-Type: application/json; charset=utf-8

Returns the error message if pikka not exists

```json
{
    "error": "invalid request"
}
```

---

## DELETE /pikka/:id/like

Unlike a pikka

===

### Example response

* Status: 200
* Content-Type: application/json; charset=utf-8

Returns the empty object

```json
{}
```

### Example error response

* Status: 401
* Content-Type: application/json; charset=utf-8

Returns the error message if user is not signed in

```json
{
    "error": "unauthorized"
}
```

### Example error response

* Status: 400
* Content-Type: application/json; charset=utf-8

Returns the error message if pikka not exists

```json
{
    "error": "invalid request"
}
```

---