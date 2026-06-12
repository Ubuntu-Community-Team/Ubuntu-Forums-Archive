---
title: "Kernel Options problem"
date: 2007-02-16
forum: General Help
---

### Post by FamousAmos on 2007-02-16
Hi, I'm attempting to set up my USB PVR2(external TV card) in Dapper, using [this guide]("http://www.isely.net/pvrusb2/pvrusb2.html").  My problem starts [here]("http://www.isely.net/pvrusb2/setup.html#Prerequisites") (scroll down about 1/4 of the way to the section labeled "Kernel Configuration").  I cannot figure out how to enable these kernel options, or to check to see if they are enabled.  Any help you can give me would be appreciated.

---

### Post by FamousAmos on 2007-02-16
Bumping to see if anyone can help me :)

---

### Post by llamakc on 2007-02-16
Based on that link you would need to tell us which kernel version you are using.

Open a terminal and type:

uname -r

and cut/paste that here for starters.

---

### Post by FamousAmos on 2007-02-16
I'm using kernel version 2.6.15-28-386

---

### Post by FamousAmos on 2007-02-18
Also using Dapper, if that makes any difference.

---

### Post by llamakc on 2007-02-18
You can see what options the kernel image you're running are configured with by looking at the included file:

cat /boot/config-`uname -r` | less

(The kernel configuration files are in /boot and correspond to your kernel. The above command will let you look through the one for your running kernel.)

You could open the config file and search for the stuff that needs to be enabled as according to that page you linked to.

You may end up having to compile your own kernel.

---

