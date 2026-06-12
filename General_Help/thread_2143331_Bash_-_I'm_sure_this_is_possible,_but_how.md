---
title: "Bash - I'm sure this is possible, but how?"
date: 2013-05-08
forum: General Help
---

### Post by CaptainMark on 2013-05-08
In this example:```
t=60
for i in t; do
    if [ \$$i -eq 60 ]; then
        echo "the number is $i"
    else
        echo fail
    fi
done
```This results is an error "Integer expression expected" The if statement is comparing the literal string of "$t" to 60 and obviously equates to false, how can i get bash to compare the result of the variable and compare 60 to 60 and equate to true,

Thanks for any help
Mark

---

### Post by papibe on 2013-05-08
Hi CaptainMark.

Just remove the '\$':
```
...
if [ $i -eq 60 ]; then
...
```
Let us know how it goes.
Regards.

---

### Post by steeldriver on 2013-05-08
I think maybe another problem is

```
t=60
for i in [COLOR=#ff0000]t[/COLOR]; do
```

which means the [ $i -eq 60 ] is trying to test the string value "t" instead of the integer value **of** variable t ("$t") i.e.

```

$ t=60; [COLOR=#ff0000]for i in t[/COLOR]; do echo $i; if [ $i -eq 60 ]; then echo "True"; else echo "False"; fi; done
t
bash: [COLOR=#ff0000][: t: integer expression expected[/COLOR]
False
$
$ t=60; [COLOR=#ff0000]for i in "$t"[/COLOR]; do echo $i; if [ $i -eq 60 ]; then echo "True"; else echo "False"; fi; done
60
True

```

What is the purpose of the for .. in construct here?

---

### Post by markbl on 2013-05-08
It's not clear what you are wanting OP, but I suspect you are trying to work out how to use indirect variables in bash? E.g:
```

$ t=60
$ i=t
$ echo ${!i}
60

```
Here, ! is the bash indirection expansion operator.

---

### Post by CaptainMark on 2013-05-09
I figured it out eventually, I simply wasn't using the correct terminology, once I discovered the term 'recursive variable substitution' I was away, I made use of the eval command as seen in my other post here [http://ubuntuforums.org/showthread.php?t=2143690](http://ubuntuforums.org/showthread.php?t=2143690)

---

