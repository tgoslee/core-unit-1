# Iterating Over Dictionaries

## Learning Goals

- Practice using for loops to iterate through a dictionary

## Introduction

The overall concept for iterating over dictionaries is the same as iterating over lists. We can use `for` loops to iterate over **each key-value pair in a dictionary.**

However, because dictionaries are key-value pairs, there are a few differences to pay attention to.

## `for` Loops for Keys and Values Need `.items()`

To iterate over a dictionary, we can use the following syntax:

```python
for my_key, my_value in my_dict.items():
    print(my_key, my_value)
```

| Piece of Code              | Notes                                                                                                                                                        |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `for`                      | `for` is a reserved keyword in Python. Python recognizes `for` as the beginning of a `for` loop.                                                             |
| `my_key`                   | **Replace this** part with a name that represents what each key is. This local variable represents the _key_ in each key-value pair, one at a time.          |
| `my_value`                 | **Replace this** part with a name that represents what each value is. This local variable represents the _value_ in each key-value pair, one at a time.      |
| `in`                       | `in` is a reserved keyword in Python. It separates the name of the `my_element` variable and the list we're iterating on.                                    |
| `my_dict`                  | **Replace this** part with the desired list to iterate over. This can be a variable that holds a list, a list literal, or any expression that becomes a list |
| `.items()`                 | `.items()` is a method that dictionaries have. It returns a view of the dictionary, or a version of the dictionary's key-value pairs that are iterable.      |
| `:`                        | This colon begins the `for` loop's body                                                                                                                      |
| ` print(my_key, my_value)` | **Replace this** with any code that should execute during each loop. This is the loop's body.                                                                |

### About `.items()`

The most unique part about iterating over dictionaries is that we should call `.items()` next to each dictionary when starting the for loop.

Python is unable to iterate over dictionaries as is; `.items()` lets us use the `for` loop with it. If we neglect to add `.items()`, we'll likely get this error:

```bash
ValueError: too many values to unpack (expected 2)
```

### About `my_key` and `my_value`

As dictionaries iterate over key-value pairs, the values of `my_key` and `my_value` change with each iteration.

1. In the first iteration, the value of `my_key` will be the key of a key-value pair, and the value of `my_value` will be the value of that same key-value pair.
2. In the second iteration, the value of `my_key` will be the key of a different key-value pair, and the value of `my_value` will be the value of that same key-value pair.
3. ... etc., until there are no more key-value pairs in the list.

We should change `my_key` and `my_value` to have variable names appropriate to the context of the dictionary.

### About the Loop Body

Similar rules about the `for` loop that we stated for arrays also apply to looping over dictionaries:

1. Loop bodies must be indented.
1. All Python logic and syntax still apply inside the loop!

### Examples

Follow these steps for each example:

1. Read through the code. What is the list? What is each element? What do we name each element? How do we use each element in the loop?
2. Predict what will print
3. Run the code and check your prediction

```python
menu = {
    "appetizer": "Brussels Sprouts",
    "beverage": "Fancy Lemonade"
}

for dish, food in menu.items():
    print(f"The special {dish} for tonight is the {food}.")
```

```python
menu = {
  "Brussels Sprouts": 18.99,
  "Fancy Lemonade": 56.00
}

for food, price in menu.items():
    taxed_price = price * 1.101
    print(f"The cost of {food} is {taxed_price}")

print("That sure was a meal!")
```

## More Examples

Our loop logic can be more complex, and include conditionals, calculations, and function calls.

```python
menu = {
  "Brussels Sprouts": 18.99,
  "Fancy Lemonade": 56.00,
  "Summer Salad": 48.50,
  "Tomato Soup": 18.50
}

for food, price in menu.items():
    taxed_price = price * 1.101
    if taxed_price > 20:
        print(f"{food} costs more than $20.")
    else:
        print(f"{food} costs less than $20")

print("That sure was a meal!")
```

Loops will often live in functions. We can use a `for` loop on a list that was passed into a function, too!

```python
def consider_specials(specials):
    for dish, special in specials.items():
        print(f"For the special {dish}, why not consider the {special} tonight?")

menu = {
    "appetizer": "Brussels Sprouts",
    "beverage": "Fancy Lemonade"
}

consider_specials(menu)
```

## `for` Loops With Only Keys Doesn't Need `.items()`

When we need to iterate over a dictionary and we **don't** need a reference to the value for each key-value pair, we can use this alternative syntax:

```python
for my_key in my_dict:
    print(my_key)
```

This syntax only names a local variable `my_key`, which will be each key, and does not require us to call `.items()` on our dictionary.

We can see in this example, our code does not raise a `ValueError` when we use this syntax! Of course, we can access the keys and values.

```python
menu = {
    "appetizer": "Brussels Sprouts",
    "beverage": "Fancy Lemonade"
}

for dish in menu:
    print(f"The special {dish} for tonight is the {menu[dish]}.")
```

### !callout-info

## Loop Styles

If this syntax accomplishes the same thing, which `for` loop style should we prefer? It is always up to the developer, but most Python developers prefer having keys and values available and iterating with `.items()`.

### !end-callout

## Iterating With `.keys()` or `.values()`

Dictionaries have a method `.keys()`, which returns a list of every key in the dictionary.

If we wanted to iterate over all the keys in a dictionary, we could call `.keys()` on it, and then iterate over it as an array.

Consider this example:

```python
menu = {
    "appetizer": "Brussels Sprouts",
    "beverage": "Fancy Lemonade"
}

print("What are the categories on the menu tonight?")
categories = []

for category in menu.keys():
    categories.append(category)

print(categories)
```

### !callout-info

## Loop Patterns

For this example, alternatively, we could have printed the categories inside the for loop. We thought it would be nice to see this pattern again, as it accomplishes something slightly different.

### !end-callout

Dictionaries also have a method `.values()`, which returns a list of every value in the dictionary!

We can iterate over every value by calling `.values()` on the dictionary, and iterating it as an array.

Consider this example:

```python
menu = {
    "appetizer": "Brussels Sprouts",
    "beverage": "Fancy Lemonade"
}

print("What are the special dishes on the menu tonight?")
special_dishes = []

for special_dish in menu.values():
    special_dishes.append(special_dish)

print(special_dishes)
```

## Check for Understanding

<!-- Question 1 -->

<!-- prettier-ignore-start -->
### !challenge
* type: checkbox
* id: 6c3bc24e-e25e-4d85-8e8e-868cb4baa41f
* title: Iteration Practice 1

##### !question

Which option will print the keys of this menu dictionary?

```python
drink_menu = {
    "hot": "coffee",
    "cold": "iced tea"
}
```

##### !end-question

##### !options

*
```python
for drink_type in drink_menu.keys():
  print(drink_type)
```

*
```python
for drink_type in drink_menu.values():
  print(drink_type)
```

*
```python
for drink_type, drink in drink_menu.items():
  print(drink)
```

##### !end-options

##### !answer

*
```python
for drink_type in drink_menu.keys():
  print(drink_type)
```
##### !end-answer

### !end-challenge
<!-- prettier-ignore-end -->

<!-- Question 2 -->

<!-- prettier-ignore-start -->
### !challenge

* type: checkbox
* id: c5a6748a-ad7e-4f50-93d4-f8d72e9f0f2a
* title: Iteration Practice 2

##### !question

Which option will print the values of this menu dictionary?

```python
dessert_menu = {
    "ice cream": "Vanilla Bean",
    "cake": "Chocolate Lava Cake",
    "pie": "Apple Pie"
}
```
##### !end-question

##### !options

*
```python
for dessert in dessert_menu.values():
  print(dessert)
```
*
```python
for category, dessert in dessert_menu.items():
  print(dessert)
```

##### !end-options

##### !answer

*
```python
for dessert in dessert_menu.values():
  print(dessert)
```
*
```python
for category, dessert in dessert_menu.items():
  print(dessert)
```

##### !end-answer

### !end-challenge
<!-- prettier-ignore-end -->