---
title: "Libreoffice 4.2.x 64 bit does not work"
date: 2015-03-18
forum: General Help
---

### Post by Welly Wu on 2015-03-18
I have a Lenovo IdeaPad Y510P and I use Ubuntu 14.04.2 64 bit LTS GNU/Linux. Let me describe what is going on. Libreoffice is not working. Previously, I added the Libreoffice PPA by opening a terminal and typing in sudo apt-add-repository ppa:libreoffice/ppa. Next, I did a sudo apt-get remove --purge libreoffice*. Then, I did a sudo apt-get update && sudo apt-get install libreoffice. That worked. However, the Libreoffice 4.4.x 64 bit version displayed black text in the menus and I could not see anything but dark text to configure the Libreoffice suite. So, I did a sudo ppa-purge ppa:libreoffice/ppa and it disabled it and downgraded my software packages. Just to be careful, I did a sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove. I also did a sudo apt-get remove --purge libreoffice* after I used sudo ppa-purge ppa:libreoffice/ppa just to be extra careful. Then, I did a sudo apt-get install libreoffice.  The installation went fine, but Libreoffice won't start. I get these error messages in the terminal:


wellywu@IdeaPadY510P:~$ locate libjvmaccesslo.so
/usr/lib/ure/lib/libjvmaccesslo.so
wellywu@IdeaPadY510P:~$

wellywu@IdeaPadY510P:~$ libreoffice
Warning: failed to launch javaldx - java may not function correctly
/usr/lib/libreoffice/program/soffice.bin: error while loading shared libraries: libjvmaccesslo.so: cannot open shared object file: No such file or directory
wellywu@IdeaPadY510P:~$ sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).


  Selection    Path                                            Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-8-oracle/jre/bin/java          1073      auto mode
  1            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      manual mode
  2            /usr/lib/jvm/java-8-oracle/jre/bin/java          1073      manual mode


Press enter to keep the current choice
[*], or type selection number: 0
wellywu@IdeaPadY510P:~$


So, it looks like I have Oracle Java 8 and OpenJDK 7 and OpenJRE 7 installed, but I selected Oracle Java 8. I don't understand the javaldx and missing libjvmaccesslo.so shared object file issues.


Could you please look into this matter and help me to find a solution? Thank you.

---

### Post by Welly Wu on 2015-03-19
I re-added the libreoffice PPA again by opening the terminal and typing in sudo apt-add-repository ppa:libreoffice/ppa. I did a sudo apt-get update && sudo apt-get dist-upgrade and it worked. However, I use Ubuntu 14.04.x 64 bit LTS GNU/Linux and I have a nVidia Geforce GT 755M with 980 MHz 2.0 GB GDDR5 video RAM GPU and I get black menus:

1. [https://bugs.documentfoundation.org/show_bug.cgi?id=89011](https://bugs.documentfoundation.org/show_bug.cgi?id=89011)

How do I turn off OpenGL rendering by editing my user profile to fix this problem?

---

### Post by Welly Wu on 2015-03-19
SOLVED:


2. [https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)


I renamed my user to user-old and it created a new user profile. Now, Libreoffice 4.4.x 64 bit works again and I chose not to enable OpenGL for all rendering. The menus appear normally and I can use Libreoffice again.

---

### Post by Bucky Ball on 2015-03-19
> **Welly Wu said:**
> I re-added the libreoffice PPA again by opening the terminal and typing in sudo apt-add-repository ppa:libreoffice/ppa. I did a sudo apt-get update && sudo apt-get dist-upgrade and it worked. However, I use Ubuntu 14.04.x 64 bit LTS GNU/Linux and I have a nVidia Geforce GT 755M with 980 MHz 2.0 GB GDDR5 video RAM GPU and I get black menus:

1. [https://bugs.documentfoundation.org/show_bug.cgi?id=89011](https://bugs.documentfoundation.org/show_bug.cgi?id=89011)

How do I turn off OpenGL rendering by editing my user profile to fix this problem?

You should probably post a new thread regarding this new issue as it is unrelated to the original thread title and subject. Good luck.

* You beat me to it. Glad you solved it. Please mark thread accordingly (see second link in my signature, but you probably beat me to that too!). ;)

---

