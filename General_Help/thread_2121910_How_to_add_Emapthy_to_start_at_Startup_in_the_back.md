---
title: "How to add Emapthy to start at Startup in the background"
date: 2013-03-03
forum: General Help
---

### Post by tlotr on 2013-03-03
Hi All,

Need some help in adding Empathy to start at startup in the background. There is an option for Startup Application in Applications > Systen Tools > Preference but I am not sure what should I enter in it. I am attaching the screenshot of the Startup Applications. Please help me in adding the commands in it so that Empathy can open on startup automatically in the background rather me clicking on it evertime I login.

---

### Post by gordintoronto on 2013-03-03
It would help if you said what version of Ubuntu you are using,

If you run Menu Editor, which might not be part of your system, and look at the Internet portion of it, you should be able to determine the command needed to run Empathy. Obviously, the Name is Empathy, and you don't need a comment.

---

### Post by kostkon on 2013-03-03
Name: it can be anything, for example just give
```
Empathy
```
Command: 
```
empathy
```
or if you want it to start minimised, then
```
empathy -h
```
Comment: anything...........

---

### Post by tlotr on 2013-03-04
Hi [**[COLOR=#000000]kostkon[/COLOR]**]("http://ubuntuforums.org/member.php?u=17209"),

Thanks for the reply. I have tried it and now Empathy starts automatically on start up in the backgroud. Thank You.

---

