# πAPI λͺμΈμπ

- version 1.0.0
- sever
  - local server : http://localhost:3000/api
  - deploy sever : http://www.makevalue.net:3000/api

<br/>

## πλͺ©μ°¨
- μ¬μ©μ API
- κ²μν API
- λκΈ, λλκΈ API

<br/>

## π²μ¬μ©μ API
> ### νμ κ°μ `GET` /signup

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|userId, password, userName| string, string, string| μ¬μ©μκ° μμ΄λ, λΉλ°λ²νΈ, μ΄λ¦μΌλ‘ νμκ°μμ μ§νν©λλ€.|

```json
body {
   userId
   userPw
   userName
}
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```POST```|```201:Created```<br/>```409:Conflict```|νμκ°μμ μ±κ³΅νμ΅λλ€.<br>μ΄λ―Έ μ‘΄μ¬νλ IDμλλ€.|

```json
{
   success:true
   statusCode: 201,
   message:"νμκ°μμ μ±κ³΅νμ΅λλ€."
   token: "bearer sdkjfndskjaf ..."
}
```

<br/><br/>

> ### λ‘κ·ΈμΈ(JWTλ°κΈ) `POST` /signin

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|userId, password|string, string|μ¬μ©μκ° μμ΄λ, λΉλ°λ²νΈλ‘ λ‘κ·ΈμΈμ μ§ννκ³ , κ³ μ  JWTν ν°μ λ°κΈλ°μ΅λλ€.|

```json
body {
   userId
   userPw
}
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```POST```|```200:OK```<br/>```404:NotFound```|λ‘κ·ΈμΈμ μ±κ³΅νμ΅λλ€.<br>μ‘΄μ¬νμ§ μλ IDμλλ€.|

```json
{
   success:true
   statusCode: 200,
   message:"λ‘κ·ΈμΈμ μ±κ³΅νμ΅λλ€."
   token: "bearer sdkjfndskjaf ..."
}
```

<br/><br/>

## π²κ²μν API
> ### κ²μκΈ μμ± `POST` /board

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|title, contents, categoryCode | string, string, string| λ‘κ·ΈμΈ ν μ¬μ©μκ° κ²μκΈμ μμ±ν©λλ€. |

```json
header: {
    Authorization: "bearer eyJhbGciOi6IkpX ..."
}

body {
    title
    contents
    categoryCode
}
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```POST```|```201:Created```<br/>```401:Unathorized```|κ²μκΈμ΄ λ±λ‘λμμ΅λλ€.<br>λ‘κ·ΈμΈμ΄ νμν©λλ€.|

```json
{
   success:true
   statusCode: 201,
   message:"κ²μκΈμ΄ λ±λ‘λμμ΅λλ€."
}
```

<br/><br/>

> ### κ²μκΈ μμ  `PATCH` /board/:boardId

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|boardId, title, contents, categoryCode |number, string, string, string| ν΄λΉ κ²μκΈμ μμ±ν μ¬μ©μκ° κ²μκΈμ μμ ν©λλ€. |

```json
header: {
    Authorization: "bearer eyJhbGciOi6IkpX ..."
}

params : boardId

body: {
    title
    contents
    categoryCode
}
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```POST```|```200:OK```<br/>```403:Forbidden```<br/>```404:NotFound```|κ²μκΈμ΄ μμ λμμ΅λλ€.<br/>κΆνμ΄ μμ΅λλ€.<br/>μ‘΄μ¬νμ§ μλ κ²μκΈμλλ€.|

```json
{
   success:true
   statusCode: 200,
   message:"μμ λμμ΅λλ€."
   data: {
      κ²μκΈ μμ  λ°μ΄ν°
   }
}
```

<br/><br/>

> ### κ²μκΈ μ­μ  `DELETE` /board/:boardId

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|boardId|number| ν΄λΉ κ²μκΈμ μμ±ν μ¬μ©μκ° κ²μκΈμ μ­μ ν©λλ€. |

```json
header: {
    Authorization: "bearer eyJhbGciOi6IkpX ..."
}

params : boardId
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```POST```|```200:OK```<br/>```403:Forbidden```<br/>```404:NotFound```|κ²μκΈμ΄ μ­μ λμμ΅λλ€.<br/>κΆνμ΄ μμ΅λλ€.<br/>μ‘΄μ¬νμ§ μλ κ²μκΈμλλ€.|

```json
{
   success:true
   statusCode: 200,
   message:"μ­μ λμμ΅λλ€."
}
```

<br/><br/>

> ### κ²μκΈ λ΄μ© κ°μ Έμ€κΈ° `GET` /board/:boardId

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|boardId|number| ν΄λΉ κ²μκΈ μμΈ λ΄μ©μ κ°μ Έμ΅λλ€. |

```json
params : boardId
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```GET```|```200:OK```<br/>```404:NotFound```|μ±κ³΅νμ΅λλ€.<br/>μ‘΄μ¬νμ§ μλ κ²μκΈμλλ€.|

```json
{
   success:true
   statusCode: 200,
   message:"μ±κ³΅νμ΅λλ€."
   data: {
      κ²μκΈ μ λ³΄
   }
}
```

<br/><br/>

> ### κ²μκΈ λͺ©λ‘ κ°μ Έμ€κΈ° `GET` /board/?page=0

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|page|number| ν΄λΉ κ²μκΈμ λͺ¨λ  λͺ©λ‘μ κ°μ Έμ΅λλ€. |

```json
params : page
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```GET```|```200:OK```<br/>```404:NotFound```|μ±κ³΅νμ΅λλ€.<br/>μ‘΄μ¬νμ§ μλ νμ΄μ§μλλ€.|

```json
{
   success:true
   statusCode: 200,
   message:"μ±κ³΅νμ΅λλ€.",
   data: {
      κ²μκΈ λͺ©λ‘ μ λ³΄
   }
}
```

<br/><br/>

## π²λκΈ/λλκΈ API
> ### λκΈ μμ±νκΈ° `POST` /comment

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|boardId, contents, depth|number, string, number| λ‘κ·ΈμΈ ν μ¬μ©μκ° ν΄λΉ κ²μκΈμ λκΈμ μμ±ν©λλ€. |

```json
header: {
    Authorization: "bearer eyJhbGciOi6IkpX ..."
}

body: {
    "boardId": "", 
    "contents":"",
     depth:  1
}
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```POST```|```201:Created```<br/>```401:Unauthorized```|λκΈμ΄ λ±λ‘λμμ΅λλ€.<br/>κΆνμ΄ μμ΅λλ€.|

```json
{
   success:true
   statusCode: 201,
   message:"λκΈμ΄ λ±λ‘λμμ΅λλ€.",
   "data": {
       λκΈ μ λ³΄...
   }
}
```

<br/><br/>

> ### λκΈ μ½κΈ° `GET` /comment?boardId&pageNo=0

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|boardId, pageNo|number, string, number|ν΄λΉ κ²μκΈμ λκΈ λͺ©λ‘μ κ°μ Έμ΅λλ€. |

```json
query : boardId, pageNo
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```GET```|```200:OK```<br/>```404:NotFound```|μ±κ³΅νμ΅λλ€.<br/>μ‘΄μ¬νμ§ μλ νμ΄μ§μλλ€.|

```json
{
   success:true
   statusCode: 200,
   message:"μ±κ³΅νμ΅λλ€.",
   "data": {
       λκΈ μ λ³΄...
   }
}
```

<br/><br/>

> ### λκΈ μ­μ  `DELETE` /comment/:boardId

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|commentId|number|ν΄λΉ λκΈμ μμ±ν μ¬μ©μκ° λκΈμ μ­μ ν©λλ€. |

```json
header: {
    Authorization: "bearer eyJhbGciOi6IkpX ..."
}

params : commentId
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```GET```|```200:OK```<br/>```403:Forbidden<br/>```404:NotFound```|μ­μ λμμ΅λλ€.<br/>κΆνμ΄ μμ΅λλ€.<br/>μ‘΄μ¬νμ§ μλ λκΈμλλ€.|

```json
   success:true,
   statusCode: 200,
   message:"λκΈμ΄ μ­μ λμμ΅λλ€.",
```

<br/><br/>

> ### λκΈ μμ  `PATCH` /comment/:boardId

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|commentId, contents|number, string|ν΄λΉ λκΈμ μμ±ν μ¬μ©μκ° λκΈμ μμ ν©λλ€. |

```json
header: {
    Authorization: "bearer eyJhbGciOi6IkpX ..."
}

params : commentId

body {
    contents
}
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```GET```|```200:OK```<br/>```403:Forbidden<br/>```404:NotFound```|μμ λμμ΅λλ€.<br/>κΆνμ΄ μμ΅λλ€.<br/>μ‘΄μ¬νμ§ μλ λκΈμλλ€.|

```json
body { 
  success:true,
  statusCode: 200,
  message:"λκΈμ΄ μμ λμμ΅λλ€.",
  contents,
  "data": {
       λκΈ μ λ³΄...
   }
}
```

<br/><br/>

> ### λλκΈ μ½κΈ° `GET` /comment/recomment?parentId&page=0

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|boardId, contents, parentId, depth|number, string, number, number| ν΄λΉ λκΈμ λ¬λ¦° λλκΈμ κ°μ Έμ΅λλ€. |

```json
query : boardId, parentId, pageNo, pageSize
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```GET```|```200:OK```<br/>```404:NotFound```|μ±κ³΅νμ΅λλ€.<br/>μ‘΄μ¬νμ§ μλ λκΈμλλ€.|

```json
{
   success:true,
   statusCode: 200,
   message:"μ±κ³΅νμ΅λλ€.",
   data: {
      λκΈ μ λ³΄...
   }
}
```

<br/><br/>

> ### λλκΈ μμ±νκΈ° `POST` /comment/recomment

## `Request`
|**Input**|**Type**|**Description**|
|--|--|--|
|boardId, contents, parentId, depth|number, string, number, number| ν΄λΉ λκΈμ λ¬λ¦° λλκΈμ κ°μ Έμ΅λλ€. |

```json
header: {
    Authorization: "bearer eyJhbGciOi6IkpX ..."
}

body: {
    "boardId": "", 
    "content": "",
    parentId,
    depth:2
}
```

## `Response`
|**HTTP Method**|**HTTP Status Code**|**Description**|
|--|--|--|
|```POST```|```201:Created```<br/>```401:Unathorized```|μ±κ³΅νμ΅λλ€.<br/>λ‘κ·ΈμΈμ΄ νμν©λλ€.|

```json
{
   success:true
   statusCode: 201,
   message:"λκΈμ΄ λ±λ‘λμμ΅λλ€."
   data: {
      λκΈ μ λ³΄...
   }
}
```
