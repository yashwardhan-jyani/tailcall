---
check_identity: true
---

# test-custom-types

```graphql @server
schema @server @upstream(baseURL: "http://jsonplaceholder.typicode.com") {
  query: Que
  mutation: Mut
}

input PostInput {
  body: String
  title: String
  userId: Int
}

type Mut {
  insertPost(input: PostInput): Post @http(body: "{{args.input}}", method: "POST", path: "/posts")
}

type Post {
  body: String
  id: Int
  title: String
  userId: Int
}

type Que {
  posts: [Post] @const(data: [{id: 1}])
}
```
