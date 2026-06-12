---
title: "Intalling applications"
date: 2006-12-25
forum: General Help
---

### Post by achill3z on 2006-12-25
Ok, so I've read on the Monkyblog site about how to install applications and I'm trying to install Firefox 2.0. Yes I've searched on the forums, but I guess either A) My issue is different, or B) I don't understand what is being said in this post [http://ubuntuforums.org/showthread.php?t=324712&highlight=%2A%2A%2ANo+targets+specified+no+makefile+found]("http://ubuntuforums.org/showthread.php?t=324712&highlight=%2A%2A%2ANo+targets+specified+no+makefile+found")
I go into the terminal and type ./configure - no directory, no big deal, I moved on to "make"...now I get ***No targets specified and no makefile found. Stop.  
One more question...
 Is manually installing (ie. through the terminal) the most common/best way to install apps in Ubuntu?(yes I'm primarily a Windoze user and I'm used to easy installs, but want to expand my knowledge)
Thanks for the help guys and gals!

---

### Post by taurus on 2006-12-25
If you want to install firefox, here's a guide...

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Vox754 on 2006-12-25
Firefox 2.0 comes installed in Ubuntu, you don't have to manually install it.

The "make" instructions are for compiling and more advanced stuff.

The basic procedure to install things is to have active "repositories" from which you download ready-to-install packages.
The path "Applications -> Add/Remove..." is as easy as Windows.

The installation from the terminal usually is
"aptitude install <package_name>" or
"apt-get install <package_name>"

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

Try it. Install different packages just to get yourself comfortable with it.

---

### Post by taurus on 2006-12-25
> **Vox754 said:**
> Firefox 2.0 comes installed in Ubuntu, you don't have to manually install it.

Only if you run Edgy since Dapper still uses firefox 1.5!

---

### Post by stalkingwolf on 2007-01-16
Ok I am completely new to Ubuntu and its associated distros.  Do the install processes
described above apply to Xubuntu also?

---

### Post by aysiu on 2007-01-16
This Firefox script will work on Ubuntu, Xubuntu, and Kubuntu:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Even though Firefox comes as .tar.gz, it is not source--it's a precompiled binary. The script integrates that with your system.

---

