---
title: "How can I get first argument using {}"
date: 2014-07-23
forum: General Help
---

### Post by CkDGTAT on 2014-07-23
Hi,

Given the manual, $1 is supposely equivalent to ${a:1:1}. 

```

$a="a b c
echo ${a:1:1}

[nothing]




```

Thank you

---

### Post by sotiris2 on 2014-07-23
What manual are you using? The code you wrote seems a bit wrong. First of all $1 is a positional parameter/variable. You do not define in your script when you write it but get it from the user when he runs your script. For example if script.sh is your script and you run it like this:
```
script.sh test
```

   When your very first line would run $1 would already be set as test. 
$a does not any special relation to $1. Maybe the example you show in the manual set $a to be $1 itself and you misundestood this as to be a feature?

 Also if you want to set a variable named **a** to a value (or string) of **a b c** the syntax is 
```
a="a b c"
``` Meaning you don't use $ when you want to set a variable normally.

  Further on the expressions [${a:1} and ${a:1:1}]("http://tldp.org/LDP/abs/html/string-manipulation.html") (search for** Substring Extraction**) or more generally ${a:x:y} where a is a variable $a , and x and y interger numbers will give you the a **part** of the variable $a. What part? The part beginning from the character after x and going on for y characters. Since I definetely suck at explanations please test the following in a terminal. 

```
a=123456789
echo ${a:3:2}
```
and try different numbers on the echo command, you will easily understand what it does.

---

