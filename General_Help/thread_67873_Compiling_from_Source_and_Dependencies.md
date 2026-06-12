---
title: "Compiling from Source and Dependencies"
date: 2005-09-21
forum: General Help
---

### Post by megamartianca on 2005-09-21
Have been piddling around with Ubuntu again and tried to compile Postfix 2.2 from source.  The big problem is that I can't really get dependencies like **anacron** and **at** to recognize the compiled version as a mail server, and I either get complaints about dependencies when I use apt-get or Synaptic or I can't install these packages (and some others that apparently rely on a mail server on the system, though these two are essential to what I'm doing).

How can I get Ubuntu's packaging system to recognize a mail server compiled from source and allow it to work as a dependency to other packages?

---

### Post by John.Michael.Kane on 2005-09-21
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)
[http://www.postfix.org/INSTALL.html](http://www.postfix.org/INSTALL.html)


Hope this helps

---

### Post by megamartianca on 2005-09-21
[QUOTE=SD-Plissken][http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)
[http://www.postfix.org/INSTALL.html](http://www.postfix.org/INSTALL.html)


Hope this helps[/QUOTE]

I can compile it fine, the problem is that packages like anacron don't seem to accept that postfix exists and when you use Synaptic, apt seems to want to dump those packages because of unresolved dependencies.  Very very irritating, and I was hoping there was some way to let the packaging system know that a mail server was present.

---

### Post by fordfan753 on 2005-09-22
[QUOTE=megamartianca]I can compile it fine, the problem is that packages like anacron don't seem to accept that postfix exists and when you use Synaptic, apt seems to want to dump those packages because of unresolved dependencies.  Very very irritating, and I was hoping there was some way to let the packaging system know that a mail server was present.[/QUOTE]

You can force things to install with apt-get....unfortunately this is a flaw in the packaging system. All packaging systems I know of are flawed (RPMs anyone?), and the flaw with .debs and apt, is that it will not recognise anything that is not a .deb

---

### Post by megamartianca on 2005-09-22
[QUOTE=fordfan753]You can force things to install with apt-get....unfortunately this is a flaw in the packaging system. All packaging systems I know of are flawed (RPMs anyone?), and the flaw with .debs and apt, is that it will not recognise anything that is not a .deb[/QUOTE]

Alright, how can I force apt-get to ignore dependencies, and what are the effects of this on something like "apt-get update"?

---

### Post by mlomker on 2005-09-22
>  the effects of this on something like "apt-get update"?

**apt-get install --force-yes packagename**

**man apt-get** for the switch options, like most command-line applications.

I don't recommend it, generally speaking.  It's a lot better to look for the source of the problem.

If you want the package system to recognize compiled applications then you need to build a .deb package for it prior to installation.  The **checkinstall** package sometimes works and there are more time-consuming ways to build one by hand.

---

### Post by megamartianca on 2005-09-22
[QUOTE=mlomker]**apt-get install --force-yes packagename**

**man apt-get** for the switch options, like most command-line applications.

I don't recommend it, generally speaking.  It's a lot better to look for the source of the problem.

If you want the package system to recognize compiled applications then you need to build a .deb package for it prior to installation.  The **checkinstall** package sometimes works and there are more time-consuming ways to build one by hand.[/QUOTE]

Thanks for the advice.  I did try **checkinstall**, but the packaging system didn't see it as a legitimate dependency for anacron.

---

