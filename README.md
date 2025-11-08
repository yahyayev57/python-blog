<p align="center">
<img src="https://github.com/yahyayev57/python-blog/blob/main/image.jpg?raw=true">
</p>

<div align="center">



<h1>🧠 Introduction </h1>
<p>In Python, everything is an object — numbers, strings, lists, even functions. Every object has an id, a type, and a value. Understanding how Python stores and manages objects helps you write better and more predictable code. This post explains what mutable and immutable objects are, how Python handles them differently, and why that matters when passing arguments to functions.</p>

</div>

<h2>1. 🪪 id and type</h2>
<h3>Every object in Python has:</h3>
<li>
  id() → its unique memory address (location)
</li>
<li>
  type() → what kind of object it is (int, list, str, etc.)
</li>
<pre>code>a = 10
b = 10
print(id(a))   # Same id as b (because of int caching)
print(id(b))
print(type(a)) # <class 'int'>
</code></pre>
<p>Even though a and b look like two variables, they may point to the same object in memory if the values are identical and immutable.</p>

<h2>2. 🧱 Mutable objects</h2>
<h3>Mutable means you can change the value without changing the object’s id.
Examples: <code>list, dict, set, bytearray</code>:</h3>
<pre>code>x = "Hello"
print(id(x))
x += " World"
print(x)
print(id(x))  # different id — a new string object was created
</code></pre>
<p>So modifying an immutable object actually makes a new one, leaving the old object untouched.</p>

<h2>3. ⚖️ Why it matters</h2>
<h3>Mutable and immutable objects affect memory usage, performance, and unexpected bugs.
Examples:</h3>
<pre><code>a = [1, 2, 3]
b = a
b.append(4)
print(a)  # [1, 2, 3, 4] → both a and b changed!
</code></pre>
<p>Because lists are mutable, both a and b point to the same memory reference.</p>
<p>But with immutable: </p>
<pre><code>a = 5
b = a
b += 1
print(a)  # 5
print(b)  # 6
</code></pre>
<p>Here b creates a new object because integers are immutable.</p>

<h2>4. 🧩 Function arguments and mutability</h2>
<p>When you pass objects to functions, Python passes references to the objects, not copies.</p>
<br>
<p>If you pass a mutable object, the function can change it in-place:</p>
<pre><code>def modify_list(lst):
    lst.append(100)

nums = [1, 2, 3]
modify_list(nums)
print(nums)  # [1, 2, 3, 100]
</code></pre>
<p>But if you pass an immutable object, Python can’t modify it directly:</p>
<pre><code>def modify_number(n):
    n += 10

x = 5
modify_number(x)
print(x)  # 5 (unchanged)
</code></pre>
<p>That’s why understanding mutability is important — it affects how data behaves when passed into functions.</p>

