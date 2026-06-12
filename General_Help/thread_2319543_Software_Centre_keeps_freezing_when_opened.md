---
title: "Software Centre keeps freezing when opened"
date: 2016-04-05
forum: General Help
---

### Post by Corey_Robertson on 2016-04-05
When I open Software Centre it loads then freezes a few seconds after, it then comes responsive and when I try install Steam it freezes causing me to have to cancel installation.
Please Help

---

### Post by RobGoss on 2016-04-05
Hello and welcome, when posting here at the forum it's helps to provide what version of Ubuntu you're using a long with the specs so people know how to approach and advise you on a fix for your machine.

---

### Post by Bucky Ball on 2016-04-05
> **RobGoss said:**
> Hello and welcome, when posting here at the forum it's helps to provide what version of Ubuntu you're using a long with the specs so people know how to approach and advise you on a fix for your machine.

^^^
This. 

Welcome Also, open a terminal and paste this in then hit return (you will be asked for your password; it will be invisible and this is normal):

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Post back (copy/paste) the exact error message between code tags, please (see the link in my signature at the bottom of this post for how to use code tags).

---

### Post by Corey_Robertson on 2016-04-05
[ATTACH=CONFIG]268191[/ATTACH]I done it and then I got this at the end...

---

### Post by Bucky Ball on 2016-04-05
Yep, looks like you've added the dl.google ppa. Open Software and Updates> Other Software and untick or remove that PPA. 

We asked for other information. Please provide it as hard to help you much further without it. Help us help you. ;)

---

### Post by Corey_Robertson on 2016-04-05
[ATTACH=CONFIG]268192[/ATTACH]The machine is quite old, although runs pretty well. 
And how do I remove that other thing

---

### Post by howefield on 2016-04-05
Try 

```
sudo mv /etc/apt/sources.list.d/get.deb.bck ~/Documents/
```

which will move the file to your Documents folder in case you want to keep it.

PS. It is usually best to copy and paste terminal output and place it between [code tags]("http://ubuntuforums.org/misc.php?do=bbcode"), rather than attach an image of your terminal.

---

### Post by Bucky Ball on 2016-04-05
See post #5 and #6. Looks like the get.deb as howefield mentioned, but if you post the output of:

> nano /etc/apt/sources.list/

... we can be specific.

---

### Post by Corey_Robertson on 2016-04-05
"No such file or directory"

---

### Post by RobGoss on 2016-04-05
Is this a new installation of Ubuntu 14.04?

It seems like you have sufficient Ram to run Ubuntu but your processor may not be able to handle some of Ubuntu functions

It's recommend to use a lightweight disto on older machines for better performance, like Lubuntu Lubuntu or Xbuntu. I have older machines that can't handle Ubuntu 14.04 as well.

---

### Post by Bucky Ball on 2016-04-05
> **RobGoss said:**
> 
It seems like you have sufficient Ram to run Ubuntu but your processor may not be able to handle some of Ubuntu functions

It's recommend to use a lightweight disto on older machines for better performance, like Lubuntu Lubuntu or Xbuntu. I have older machines that can't handle Ubuntu 14.04 as well.

OP states OS is running fine. Issue is with SCentre and think we've identified that problem. ;)

Try:

> nano /etc/apt/sources.list

---

### Post by RobGoss on 2016-04-05
Is it something that's installed on his system that maybe be causing the software center to slow down?

---

### Post by Bucky Ball on 2016-04-05
Yes. The get.deb repository probably, but waiting to see the sources.list file.

Have a look at the bottom of the output in the pic in post #4.

---

### Post by RobGoss on 2016-04-05
Yeah I see the one that says ignored source.list

So if this is corrected will the software center load properly?

Sorry for jumping in like the is but I'm also interested in learning all I can about Ubuntu Linux in general. Thanks

---

### Post by deadflowr on 2016-04-05
The getdeb is the least of the worries.
The real problem is the Google Chrome

As you are using a 32-bit version of Ubuntu you need to disable, and unfortunately, remove Google Chrome.
As it is no longer supported on 32-bit Linux systems.

---

### Post by RobGoss on 2016-04-05
> **deadflowr said:**
> The getdeb is the least of the worries.
The real problem is the Google Chrome

As you are using a 32-bit version of Ubuntu you need to disable, and unfortunately, remove Google Chrome.
As it is no longer supported on 32-bit Linux systems.

I'm curious to know how this would interfere with the software Center?

When we use the Software center is the apps being downloaded from Chrome?

If he is using a 32-bit system he's going to have to install Chromium in its place

 thanks

---

### Post by deadflowr on 2016-04-05
The google repo is problematic because the repository no longer exists for those packages (the i386 packages)

This is causing a flux and confusion in the system's ability to understand what packages are available.
And as such is causing the entire apt/software center fiasco to persist.

The same thing would happen if you try to add a ppa for a dead ppa.

> [COLOR=#000000]When we use the Software center is the apps being downloaded from Chrome?[/COLOR]
Only the Google Chrome package, but how the package manager works is, if one source is busted then the package management system is busted as a whole.

---

### Post by RobGoss on 2016-04-05
**Deaddflower** thanks so much for explaining it much appreciated

---

