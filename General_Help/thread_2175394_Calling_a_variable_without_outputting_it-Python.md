---
title: "Calling a variable without outputting it-Python"
date: 2013-09-19
forum: General Help
---

### Post by blackout2 on 2013-09-19
I am comparing whether a "random" number equals some user input.

this is my pseudo-code.

I want to call randint, but I don't want to show it.

```


randint=random.randrange(1, 50)

if randint == somevariable:
            do foo


```


To clarify, I want to test whether or not randint equals somevariable, but, randint doesn't "run" random.randrange(1, 50) until I use the print command or something similar.

I tried 

```


"randint='%s'" % (randint)

```
 This doesn't call it either.
Any ideas?

^ That is just pseudo code, not my actual code, but you should get the idea.

---

### Post by Vaphell on 2013-09-19
you messed something up, again ;-)
= makes right side evaluate and assigns the value to the left side. You need value to execute assignment line

post the shortest possible snippet that showcases the problem, including input handling.
My suspicion is that you compare string to int, which wont fly, or something similarly sloppy

```
>>> rnd = random.randrange(1,10)
>>> rnd
4  [COLOR="#0000FF"]# value is already there[/COLOR]
>>> input = '4'
>>> if ( rnd == input ): print "true"
... 
>>> input = 4
>>> if ( rnd == input ): print "true"
... 
true

```

---

### Post by blackout2 on 2013-09-19
Is there anyway to to make a variable be of the int type, like in C++? I think because I have raw_input going into my comparison variable, it is a string type. 
Keep in mind my this is my second script written in python, and programming with bash, C++, powershell, and batch, things get a little mixed up sometimes.
I think the problem is I'm comparing a string, to an int, that's my problem. I will google around, and if I find the answer before you reply, than we're good.

almost forgot :

```


compare=raw_input()

if compare == randint:
               foo(bar)

```

---

### Post by blackout2 on 2013-09-19
Okay, I'm back, I have figured it out, and I am good to go, thanks for pointing me in the right direction Vaphell...

---

