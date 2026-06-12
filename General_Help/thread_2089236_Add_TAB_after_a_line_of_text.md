---
title: "Add TAB after a line of text"
date: 2012-11-28
forum: General Help
---

### Post by Thorlightningpower on 2012-11-28
Ok so I need to know how to add a tab space after the end of multiple lines in a text file besides manually doing it. I have probably 14000 lines and doing that by hand would kill me. Any hep would be fantastic!

---

### Post by rai4shu2 on 2012-11-28
I would suggest using Python. See [http://www.python.org/doc/](http://www.python.org/doc/)

---

### Post by lykwydchykyn on 2012-11-28
something like this would work:

```

sed -i 's/$/\t/g' myfile

```

Adds a tab character to then end of every line in "myfile".

---

### Post by Thorlightningpower on 2012-11-28
Well I dislike Python (never had any luck getting it right ever) and Lyk That's close, that is adding a new line I'm saying something like "Hi     "
Edit: well it works....just not on that text file...I'll try again and let you know

---

### Post by Vaphell on 2012-11-28
file created in windows? i suspect carriage return (\r)

try this
```
sed -i 's/\r$/\t/g' myfile
```

---

### Post by Thorlightningpower on 2012-11-28
I will try this And let you know, and yes it was From windows.
Edit Thanks everyone for the help!
Edit 2: WHat is I needed to add 2 or more tabs or add multiple of the same thing at the end of the file?

---

### Post by Vaphell on 2012-11-28
s/$/\t/ adds \t at the end of line (replaces end-of-line with \t)
s/\r$/\t/ expression replaces *\r(end-of-line)* with *\t*

obiously you can write s/$/\t\t\t\t\t/ or s/\r$\t\t\t\t\t/
> WHat is I needed to add 2 or more tabs or add multiple of the same thing at the end of the file?
any more specific examples? it depends

either way if you need to modify text files in automated way, you should read a bit about *sed*, *awk* and regular expressions in general

---

### Post by Thorlightningpower on 2012-11-28
then what's wrong with this? I must be missing something
```
sed 's/\r$/\t/t/t/' log.txt
```
I see my error I hope.

---

### Post by steeldriver on 2012-11-28
you're just mixing up the forward slashes and the backslashes I think - you want to replace \r$ with \t\t\t so that's

```
's/\r$/[COLOR=Red]\[/COLOR]t[COLOR=Red]\[/COLOR]t[COLOR=Red]\[/COLOR]t/'
```EDIT: fwiw you don't have to use forward slashes for the separators in a sed substitute expression - sometimes these things are easier to read if you use a different character e.g.

```
's#\r$#[COLOR=Red]\[/COLOR]t[COLOR=Red]\[/COLOR]t[COLOR=Red]\[/COLOR]t#'
```or

```
's|\r$|[COLOR=Red]\[/COLOR]t[COLOR=Red]\[/COLOR]t[COLOR=Red]\[/COLOR]t|'
```

---

### Post by rai4shu2 on 2012-11-28
Yes. Let us know what score you got on this assignment, too. ;)

---

