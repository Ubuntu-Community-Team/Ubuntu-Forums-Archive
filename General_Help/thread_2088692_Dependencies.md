---
title: "Dependencies?"
date: 2012-11-27
forum: General Help
---

### Post by Winter1337 on 2012-11-27
Hello everyone, i'm new to Ubuntu, I just installed my own Ubuntu 12.10 and whenever I tried to install anything from software center, it just pops up an error and show me this
error window message:

"
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time

The following packages have unmet dependencies:

openjdk-7-jre: Depends: openjdk-7-jre-headless (= 7u9-2.3.3-0ubuntu1~12.10.1) but 7u9-2.3.3-0ubuntu1~12.10.1 is to be installed
               Depends: libgif4 (>= 4.1.4) but it is not going to be installed
               Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is to be installed
               Depends: libpulse0 (>= 1:0.99.1) but 1:2.1-0ubuntu4 is to be installed
               Depends: libatk-wrapper-java-jni (>= 0.30.4-0ubuntu2) but it is not going to be installed
"

any solution? I just can't install anything with this error, I tried to surf the web, tried lots of solution, and still get back the same thing.

---

### Post by nothingspecial on 2012-11-27
Fixed thread title.

---

### Post by ibjsb4 on 2012-11-27
Hi Winter1337

Seems to be a lot of this going around.  Here's something to try.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

sudo apt-get update

sudo dpkg --configure -a

sudo apt-get dist-upgrade

Give that a shot.  Also, have you installed any packages outside of the software center, third party software/PPA's?

If you want to know more about these commands:

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Winter1337 on 2012-11-27
> **ibjsb4 said:**
> Hi Winter1337

Seems to be a lot of this going around.  Here's something to try.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

sudo apt-get update

sudo dpkg --configure -a

sudo apt-get dist-upgrade

Give that a shot.  Also, have you installed any packages outside of the software center, third party software/PPA's?

If you want to know more about these commands:

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)
Thanks for helping. But I've solved the problem now. :)

---

### Post by elliotn on 2012-11-27
in most cases updating repository fixes the problem

---

