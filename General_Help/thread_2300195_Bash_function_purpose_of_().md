---
title: "Bash function: purpose of ()?"
date: 2015-10-24
forum: General Help
---

### Post by vasa1 on 2015-10-24
Both ```
function hw1()
{ 
echo "hello world"
}

```
and
```
function hw2
{ 
echo "hello world"
}
```work. So why do most Bash functions have the ***()*** as in the first code?

Bumbling on ...
```
hw3
{ 
echo "hello world"
}
```
^^^ doesn't work; system thinks **hw3** maybe a command but 

```
hw3()
{ 
echo "hello world"
}
```
and
```
function hw3
{ 
echo "hello world"
}
```
both work so I get the impression that either ***Function*** or ***()*** are sufficient to prevent the function from being confused with a command.

But I see examples with both ***function*** and ***()***? So is it just good coding practice or are there technical reasons for having both ***function*** and ***()***?

---

### Post by The Cog on 2015-10-24
Good question.
According to this page, both methods of defining functions are valid.
[http://tldp.org/LDP/abs/html/functions.html](http://tldp.org/LDP/abs/html/functions.html)

I also found by trial that this works:
```

function hw4 () {
   echo Hello World 4
}
hw4

```

---

### Post by vasa1 on 2015-10-24
> **The Cog said:**
> Good question.
According to this page, both methods of defining functions are valid.
[http://tldp.org/LDP/abs/html/functions.html](http://tldp.org/LDP/abs/html/functions.html)
...
Thanks for the link!

---

### Post by vasa1 on 2015-10-24
If I had RTFM'ed first, I would have seen this in **man bash**:> function name [()] compound-command [redirection]
              This defines a function named name.  **The reserved word function is optional.  If the function reserved word is supplied, the parentheses are optional.**
...

---

### Post by tgalati4 on 2015-10-24
I think it is left over from FORTRAN so that it is easier to tell the difference between a function, a constant, and a variable.  The compiler doesn't care, nor does the running binary, but humans need all the help they can get.

---

### Post by sudodus on 2015-10-24
I think function definitions in sh use () instead of the word 'function'.

```
#!/bin/sh

hej () {

echo "Hello World"
}

hej

```

while bash uses the word function

```
#!/bin/bash

function hej  {

echo "Hello World"
}

hej

```

and **function hej ()** is also an accepted syntax in bash

---

### Post by vasa1 on 2015-11-15
And here's one more comment: > but one quibble -- the function keyword is a needless incompatibility with POSIX. Just leave it off: xx() { ...from [http://stackoverflow.com/questions/20111063/bash-alias-command-with-both-single-and-double-quotes#comment29967940_20111135](http://stackoverflow.com/questions/20111063/bash-alias-command-with-both-single-and-double-quotes#comment29967940_20111135)

---

