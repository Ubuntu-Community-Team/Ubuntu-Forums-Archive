---
title: "Need flex for 7.10... Also, VMware Tools"
date: 2008-04-23
forum: General Help
---

### Post by CannibalAngel666 on 2008-04-23
I don't know if this is the right place for this post... but here it goes.

I am an ubuntu noob. I have never really used any lenux distro before but i want to start. I am taking IT:SF classes now and i need to install SNORT on an ubuntu 7.10 Virtual Machine. I got it to the point where i compile the source code and it gives me an error saying i need flex. I need to know where to get flex and any commands/tips that i may need/be useful to me.

I would also like to know how to install VMWare Tools on this ubuntu machine.

Any help on this would be greatly appreciated.

---

### Post by CannibalAngel666 on 2008-04-23
BUMP... Please Help

---

### Post by bodhi.zazen on 2008-04-23
[http://howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10](http://howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10)

---

### Post by CannibalAngel666 on 2008-04-23
Ok... I found flex. I Download and run ./configure and get an error:
[I]
configure: error: GNU M4 1.4 is required[/I]

I go and download m4-1.4.9. I run ./configure with no problem. I then try to run make and i get this:

[I]Making all in .
make[1]: Entering directory `/home/robert/Desktop/m4-1.4.9'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/robert/Desktop/m4-1.4.9'
Making all in examples
make[1]: Entering directory `/home/robert/Desktop/m4-1.4.9/examples'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/robert/Desktop/m4-1.4.9/examples'
Making all in lib
make[1]: Entering directory `/home/robert/Desktop/m4-1.4.9/lib'
make  all-am
make[2]: Entering directory `/home/robert/Desktop/m4-1.4.9/lib'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/robert/Desktop/m4-1.4.9/lib'
make[1]: Leaving directory `/home/robert/Desktop/m4-1.4.9/lib'
Making all in src
make[1]: Entering directory `/home/robert/Desktop/m4-1.4.9/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/robert/Desktop/m4-1.4.9/src'
Making all in doc
make[1]: Entering directory `/home/robert/Desktop/m4-1.4.9/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/robert/Desktop/m4-1.4.9/doc'
Making all in checks
make[1]: Entering directory `/home/robert/Desktop/m4-1.4.9/checks'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/robert/Desktop/m4-1.4.9/checks'[/I]

I read the m4 web page and found out i need automake and autoconf. I downloaded **autoconf.texi.tar.gz** and **automake-1.10.1.tar.gz** and unziped them. I ran ./configure for automake and it said that i need autoconf first. 

**I now need to know how to install autoconf. All these downloads are on my Desktop (home/robert/Desktop).**

Any and all help would be greatly appreciated.

---

### Post by bodhi.zazen on 2008-04-23
The link I gave you give detailed step-by-step instructions.

Is there a reason you are compiling from source rather then installing from the Ubuntu repositories ?

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)


If you want to compile the dependencies from source, you first need to install build essential.

```
sudo apt-get install build-essential
```

Then see this post for compiling :

[http://ubuntuforums.org/showpost.php?p=4473168&postcount=5](http://ubuntuforums.org/showpost.php?p=4473168&postcount=5)

---

