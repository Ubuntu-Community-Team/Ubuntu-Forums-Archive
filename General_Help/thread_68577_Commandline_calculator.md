---
title: "Commandline calculator"
date: 2005-09-23
forum: General Help
---

### Post by Nasso on 2005-09-23
Hi yall.
I want a calculator for the console. I hate opening xcalc or google just because i want to divide something and so on.

I want it basic. if i type 
"xyz 1+2"
it should just print out 3

if i type 
"xzy (1+1)^2*2"
it should just return 8.

I have been searching the repos but cant find anything. You got any tips for me? :)

---

### Post by bsussman on 2005-09-23
```
bos@Dillon:~$ bc
bc 1.06
Copyright 1991-1994, 1997, 1998, 2000 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'.
2 * 2
4
```

Any other numbers ya want multiplied while I got the window open??

[http://www.linuxfocus.org/English/January2004/article319.shtml](http://www.linuxfocus.org/English/January2004/article319.shtml) has lots of stuff you might want to look at.

I have a feeling this is waaay to thorough an answer....:-\"

---

### Post by Nasso on 2005-10-07
> **bsussman]```
bos@Dillon:~$ bc
bc 1.06
Copyright 1991-1994, 1997, 1998, 2000 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'.
2 * 2
4
```

Any other numbers ya want multiplied while I got the window open??

[http://www.linuxfocus.org/English/January2004/article319.shtml](http://www.linuxfocus.org/English/January2004/article319.shtml) has lots of stuff you might want to look at.

I have a feeling this is waaay to thorough an answer....:-\"[/QUOTE]

oooh, that is how bc works :) well. it wasnt what i asked for, i wanted to give the " 1 * 2" in the arguments of the command. but this is way better then nothing  said:**
> 
nasso@nassolaptop:~$ bc 1*2
File 1*2 is unavailable.


---

### Post by mcduck on 2005-10-08
Python also works as a nice commandline calculator, with all the features you could ever want..

---

### Post by PMO6022 on 2005-10-08
Qalc will do just what you suggest:> pmorris@ubuntu:~ $ qalc 2+2
2 + 2 = 4  I'm not sure it is available in a ubuntu repo - I installed a .deb from debian stable with no problems.  I already had all the dependencies installed from my base ubuntu install. See  [http://packages.debian.org/stable/gnome/qalc]("http://packages.debian.org/stable/gnome/qalc")

---

### Post by mpat on 2005-10-08
Besides **bc** another good one might be **"Mathomatic"**. It can also solve equations. ;-)

[http://mathomatic.orgserve.de/math/](http://mathomatic.orgserve.de/math/)

---

