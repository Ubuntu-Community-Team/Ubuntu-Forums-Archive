---
title: "Problem with installing other things"
date: 2007-04-24
forum: General Help
---

### Post by j.miller565 on 2007-04-24
I tried to install Opera today, but it didn't go very well. Firstly, it couldn't install and secondly, when I want to install or upgrade through the Terminal, this message comes up:

BTW,  Opera is a .deb GDebi file.

```
simon@simon-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package opera needs to be reinstalled, but I can't find an archive for it.
```

What can I do?

---

### Post by j.miller565 on 2007-04-24
anyone know?

---

### Post by DoktorSeven on 2007-04-24
Try doing

sudo apt-get -f install

It will likely uninstall Opera, and you can just download and install the Ubuntu deb package for Opera from their site again afterwards.

---

### Post by Ziggy72 on 2007-04-24
If you haven't done it already, I suggest you download Automatix from [ http://www.getautomatix.com/wiki/index.php?title=Installation]( http://www.getautomatix.com/wiki/index.php?title=Installation). Automatix allows a Ubuntu user to download and set up a number of very useful programs, plugins and codecs, including Opera, very easily indeed. Whenever I do a fresh install, Automatix is one of the first dowloads I make to assist me in setting up the OS.

---

### Post by j.miller565 on 2007-04-24
I tried 
```
sudo apt-get -f install
```

But the same message comes up

```
simon@simon-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package opera needs to be reinstalled, but I can't find an archive for it.
```

Is there anything else I can do?


I'll try Automatix once I resolve this unfortunate problem. It sounds like a good program.

---

### Post by j.miller565 on 2007-04-24
I really need to solve this out very soon. Is there anything else I can do?

Is there anyway how I can uninstall it?

---

### Post by j.miller565 on 2007-04-25
Why would it be -f install when  -f  is to "Attempt to continue if the integrity check fails" when I'm sure the integrity was fine. I tried -m install since -m is to " Attempt to continue if archives are unlocatable", but that doesn't work. 

Is there anything else I can do?

---

### Post by j.miller565 on 2007-04-25
anyone please?

---

### Post by Sef on 2007-04-25
Have you reinstalled Opera?

---

### Post by j.miller565 on 2007-04-25
I'm not going to try it now even though I've found the solution for my problem at [http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it/](http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it/)

Thanks for the help guys

---

