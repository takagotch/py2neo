### py2neo
---
https://py2neo.org/2.0/

```py
alice.properties["age"] = 33
bob.properties["age"] = 44
alice.push()
bob.push()

from py2neo import watch
watch("httpstream")
alice.push()
bob.push()

graph.push(alice, bob)

graph.cypher.execute("CREATE (c:Person {name:{N}}) RETURN c", {"N": "Carol"})

for record in graph.cypher.execute("CREATE (d:Person {name:'Dave'}) RETURN d"):

for record in graph.cypher.execute("MATCH (p:Person) RETURN p.name AS name"):
  print(record.name)

tx = graph.cypher.begin()
statement = "MATCH (a {name:{A}}), (b {name:{B}}) CREATE (a)-[:KNOWS]->(b)"
for person_a, person_b in [("Alice", "Bob"), ("Bob", "Dave"), ("Alice", "Carol")]:
  tx.append(statement, {"A": person_a, "B": person_b})
tx.commit()

graph.schema.create_uniqueness_constraint("Person", "email")

xavier = graph.merget_one("Person", "email", "charles@x.men")

alice = graph.merge_one("Person", "email", "alice@example.com")
bob = graph.merget_one("Person", "email", "bob@email.net")
graph.create_unique(Relationship(alice, "KNOWS", bob))

carol = graph.merge_one("Person", "email", "carol@foo.us")
dave = graph.merge_one("Person", "email", "dave@dave.co.uk")
graph.create_unique(Path(aice, "KNOWS", bob, "KNOWS", carol, "KNOWS", dave))
```

```sh
cypher -p N Alice "MATCH (p:Person {name:{N}}) RETURN p"
```

```
```

