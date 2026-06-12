---
title: "Installing J2SE"
date: 2007-03-12
forum: General Help
---

### Post by ppatalano on 2007-03-12
I'm trying to install J2SE Runtime Environment (JRE) v6.0 with Plug-in for Mozilla Firefox and when I run ```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

I get an output of

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-jre
```

Should I just be using version 5 instead of 6 or did I type it in wrong.

---

### Post by ComputerGuy56 on 2007-03-12
[http://www.java.com/en/download/](http://www.java.com/en/download/)

I went on the main Firefox website and I found this. It's a plugin thingy for firefox that "should" be Java and it "should" work.

---

### Post by closetpirate on 2007-03-12
The most likely problem is the repositories.

Try this:

open for edit the /etc/apt/sources.list file

delete every instance of "##" from the lines containing the 'deb' 
save it

try again

oh and another thing which version of ubuntu do you have?

---

### Post by ppatalano on 2007-03-12
Thanks a lot for your help but I figured I can install 5.0 with the add/remove programs application in Ubuntu. :)

edit(didn't see the new post): I will try that closetpirate and I am running 6.10

---

### Post by ppatalano on 2007-03-12
I am currently installing software, so I will wait until that is done to try the install of java6 again. I uncommented the sources for the repositories. Thanks for the help.

---

### Post by ppatalano on 2007-03-12
I took away the comments from the sources but im still getting
```
peter@peter-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-jre
```


edit: I got it working now, thanks a lot

---

### Post by mrvertigo on 2007-04-28
[CENTER]hey, home boy i am having the same issue!!!!!! please help how did you fix this error?[/CENTER]

---

