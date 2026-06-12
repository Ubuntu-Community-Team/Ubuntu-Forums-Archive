---
title: "Need program to change start up order of dual boot system"
date: 2015-10-25
forum: General Help
---

### Post by norm-thom-g on 2015-10-25
I've just added ubuntu 15.10 to my dell inspiron 1545.  in the past I've been able to change the startup OS from Ubuntu to Windows by using a
Grub program that would help me ( obviously I don't remember the name)  but I could not find this or a similar program on 15.10.
Can anybody recomend a program that would do this

Thanking you in advance

---

### Post by oldos2er on 2015-10-25
[Grub Customizer.]("https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer")

---

### Post by afz12 on 2015-10-25
Hi norm-thom-g

I looked into the grub text file using cd /etc/default from Ubuntu 15.10 in a terminal. Then sudo su and entered my password. Then gedit grub, to get this

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="noprompt persistent"

I think the first line gives an order of start-up preference - "0" is first, "1" is next and so on. I'm not sure about Windows ordering but in the past, adding any new Linux OS has automatically placed it first in the boot order. This notebook boots Ubuntu first, then Mint Cinnamon. It used to have Windows 10 but man was this OS "upgrade" from w8.1 continually problematic and flaky!

---

### Post by Cavsfan on 2015-10-25
Or check out my custom grub wiki. It's in the green link on the first post of the thread in my signature.

I managed to customize my grub in Arch Linux but also have Wily Xubuntu 15.10 and Windows 10.

I have it set to default boot to windows 10 default for my wife in case a reboot occurs.

You can have a nice background, the font colors of your desire for the top and bottom and different ones for the menu and the highlighted line
You choose the default OS and it will never change unless you change it.

Here is an earlier picture when I had a bunch of systems some of which I got rid of for simplicity:

[[IMG]http://www.zimagez.com/miniature/20150812111553.jpg[/IMG]]("http://www.zimagez.com/zimage/20150812111553.php")

It might look more difficult than it really is but check it out and post any questions you have in that thread and I will be happy to hook you up. :)

---

### Post by yancek on 2015-10-25
> GRUB_DEFAULT=0

The line above is what you need to modify.  It is the /etc/default/grub file so to open it and edit your need root privileges.  Open a terminal and type:  sudo gedit /etc/default/grub

You should then see the text file open and change the 0 to whatever you want.  Since counting here starts with zero, if you want the third menuentry in the grub menu (grub.cfg) file, then put a 2 there, save it and run sudo update-grub and it should change on reboot.

---

### Post by Cavsfan on 2015-10-26
> GRUB_DEFAULT=0

> **yancek said:**
> The line above is what you need to modify.  It is the /etc/default/grub file so to open it and edit your need root privileges.  Open a terminal and type:  sudo gedit /etc/default/grub

You should then see the text file open and change the 0 to whatever you want.  Since counting here starts with zero, if you want the third menuentry in the grub menu (grub.cfg) file, then put a 2 there, save it and run sudo update-grub and it should change on reboot.

Sudo gedit is wrong. gksudo gedit or gksu gedit is the correct use for GUI applications. You can damage your system using sudo.

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

