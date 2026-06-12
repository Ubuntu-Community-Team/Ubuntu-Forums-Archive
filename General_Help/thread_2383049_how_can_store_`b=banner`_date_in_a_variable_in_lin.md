---
title: "how can store `b=banner` date in a variable in linux? Ask Question"
date: 2018-01-20
forum: General Help
---

### Post by ehfo0 on 2018-01-20
I have a problem with head command in linux when I assign a variable to it like a=date and then echo $a I do get the result ! but when i use a= he ad date and want to echo result it just go to A new line without any warning !why is it? how can I assign 2 command to be executed and stored in variable? like
b= `banner date`
echo $b

---

### Post by Frogs Hair on 2018-01-20
Hello and Welcome

Please use the paper-clip symbol to upload thumbnail images out of respect for other users bandwidth. You can also copy and paste a terminal output and enclose it in code tags by highlighting the pasted text and selecting the # symbol in the reply tool bar.

---

### Post by SeijiSensei on 2018-01-20
There's a very big difference between the two commands in the graphic.  The first is encased in backquotes which tells the bash shell to evaluate the contents of the string inside the quotes.  The backquotes have been deprecated in favor of the $() operator.  What I think you want to do is something like this:

```

$ date
Sat Jan 20 11:51:09 EST 2018
$ uname
Linux
$ b="$(date) $(uname)"
$ echo $b
Sat Jan 20 11:51:17 EST 2018 Linux

```
You must use double quotes to create the string assigned to b.  That assigns the string containing the result of "date" and the result of "uname" to the environment variable b.

If you use
```

$ b='$(date) $(uname)'

```
encasing the string in single quotes, you'd get this result
```

$ b='$(date) $(uname)'
$ echo $b
$(date) $(uname)

```
since single quotes tell bash to treat the string literally.

---

### Post by slickymaster on 2018-01-20
Thread moved to **General Help** for a better fit

---

