# Types

Venus is made of objects and functions.

All objects in Venus are of a type:

- `10` is of type `int`
- `'c'` is of type `char`
- `true` is of type `bool`
- `"Hello"` is of type `string`

Types are called `struct` or `class` in D and other languages.
To make things clear, we unify all these concepts into one `type`.


You can make your own custom types by defining a new `type`.


```d
type Node {
	int id
	int depth
	string name
}
```

Here we define a new type called 'Node', it might be a node in a tree.
The node type has four fields:
- id, of type `int`
- depth, also of type `int`
- name, of type `string`

You can see that there is no limit for fields, you can define any of them

Now to create a new instance of the type 'Node', you can use `create` function:

```d
val node = Node.create // creates a new Node object
```

## Object initialization

When an object is created, each field is initialized with an default value of its type.

You can get the initial value of a type with `init` property:

```d
val a = int.init // int.init == 0

val n = Node.create

assert (n.id == 0)
assert (n.depth == 0) 
assert (n.name == "") // string.init = ""
```

If you want to control the default value of a field, you need a constructor

```d
import std.counter
type Node {
	int id
	int depth
	string name

	public create(int id, int depth, int name) {
		this.id = id
		this.depth = depth
		this.name = name
	}
}
```

## In Depth: Field alignment

In C, you can specify the alignment of each field in a struct, to make the whole data more align in the memory, thus increase efficiency.