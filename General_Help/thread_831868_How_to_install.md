---
title: "How to install?"
date: 2008-06-17
forum: General Help
---

### Post by highlyevolved on 2008-06-17
I'm very frustrated atm.

I'm completely new to linux and have no idea how to install .tar files.

Is there a complete dummies guide somewhere?

I don't want to have to go back to xp but I fear I may have to.

---

### Post by doorman on 2008-06-17
take a look at [my previous post]("http://ubuntuforums.org/showthread.php?p=5185023#post5185023")

---

### Post by HammerNJ on 2008-06-17
Hi:

What tar files are you trying to install? If you just want to know how un-tar tar files, here is a useful link:

[http://www.computerhope.com/unix/utar.htm](http://www.computerhope.com/unix/utar.htm)

HTH, Hammer

---

### Post by highlyevolved on 2008-06-17
Tried to follow those steps but got this

adam@adam-laptop:~$ tar -xvfz Firefox2.tar.gz
tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


Also trying to instal flash, audacious etc.

---

### Post by raedbenz on 2008-06-17
> **highlyevolved said:**
> I'm very frustrated atm.

I'm completely new to linux and have no idea how to install .tar files.

Is there a complete dummies guide somewhere?

I don't want to have to go back to xp but I fear I may have to.

check [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by bijeeshvs on 2008-06-17
leave the tar ball there thats not a good way to install, do one thing go to SYSTEM->ADMINISTRATION->SYNAPTIC PACKAGE MANGER 
SEARCH FOR YOUR DESIRED PROGRAM AND CLICK INSTALL IT WILL AUTOMATICALLY DOWNLOAD AND INSTALL THE PROGRAM FOR YOU

---

### Post by bijeeshvs on 2008-06-17
And If U Are Very Interested In Using The Tar Ball Way, Let Me Know Sure We Can Help You

---

### Post by doorman on 2008-06-17
> **highlyevolved said:**
> Tried to follow those steps but got this

adam@adam-laptop:~$ tar -xvfz Firefox2.tar.gz
tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


Thnx for pointing that out. Actually it's a spelling error - the command is:

```
tar -xzvf file.tar.gz
```

Cheers!

---

### Post by HammerNJ on 2008-06-17
> **highlyevolved said:**
> Tried to follow those steps but got this

adam@adam-laptop:~$ tar -xvfz Firefox2.tar.gz
tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


Also trying to instal flash, audacious etc.

I agree with the general consensus, if your are running Ubuntu Desktop, use the Synaptic Package Manager app and check off what you need and Synaptic will do the rest. As for me, I'm a command line guy so I do everything thru sudo apt-get install <whatever> from the command line. ;)

HTH, Hammer

---

### Post by Bablefish on 2008-06-17
But I will swear it is IMPOSSIBLE to install some tar files. I know I tried, that is why I get my programs precompiled. IE via [www.getdeb.net](www.getdeb.net) or through a Google search just add .deb to any program your looking for.

---

### Post by HammerNJ on 2008-06-17
> **Bablefish said:**
> But I will swear it is IMPOSSIBLE to install some tar files. I know I tried, that is why I get my programs precompiled. IE via [www.getdeb.net](www.getdeb.net) or through a Google search just add .deb to any program your looking for.

Hi:

I checked out [www.getdeb.net](www.getdeb.net), coll site, but they only have files for Hardy and Gutsy. No Feisty! AM I missing something? Seems rather limited. 

Thanks, H

---

### Post by highlyevolved on 2008-06-17
> **HammerNJ said:**
> I agree with the general consensus, if your are running Ubuntu Desktop, use the Synaptic Package Manager app and check off what you need and Synaptic will do the rest. As for me, I'm a command line guy so I do everything thru sudo apt-get install <whatever> from the command line. ;)

HTH, Hammer

But a program like audacious can that be installed via synaptic?

Also, when a site loads with flash I have to press play for it to work...is there a way to have it automatically load?

Like myspace layouts that are flash based don't even load after I've pressed play.

---

### Post by bijeeshvs on 2008-06-17
you can install everything from synaptic, for the flash problem first tell me which browser are you using and your os is 32bit or 64 bit

wht happened to you flash is probably you have installed gnash or something like that which is open source and not from adobe stable uninstall gnash or whatever u have first, and install "restricted extras" from synaptic it contain flash java and video and audio codecs

---

