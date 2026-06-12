---
title: "ia32-libs missing in printer install"
date: 2017-07-29
forum: General Help
---

### Post by PaulBx on 2017-07-29
I'm running Lubuntu 16.04LTS, trying to install a Brother HL-L2320D printer. Here is the website:
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128)

Here is my work with the Brother-supplied driver:
```

paul@len780:~/Downloads$ sudo bash linux-brprinter-installer-2.1.1-1
[sudo] password for paul: 
Input model name ->HL-L2320D

You are going to install following packages.
   hll2320dlpr-3.2.0-1.i386.deb
   hll2320dcupswrapper-3.2.0-1.i386.deb
OK? [y/N] ->y

Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Hit:3 https://s3-us-west-2.amazonaws.com/brave-apt xenial InRelease
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Fetched 306 kB in 3s (82.9 kB/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32ncurses5 lib32z1

E: Package 'ia32-libs' has no installation candidate
dpkg -x hll2320dlpr-3.2.0-1.i386.deb /
dpkg -x hll2320dcupswrapper-3.2.0-1.i386.deb /
(Reading database ... 180983 files and directories currently installed.)
Removing hll2320dcupswrapper:i386 (3.2.0-1) ...
lpadmin: Unable to connect to server: Bad file descriptor
Purging configuration files for hll2320dcupswrapper:i386 (3.2.0-1) ...
dpkg-deb: building package 'hll2320dlpr' in 'hll2320dlpr-3.2.0-1a.i386.deb'.
dpkg -b ./brother_driver_packdir hll2320dlpr-3.2.0-1a.i386.deb
dpkg-deb: building package 'hll2320dcupswrapper' in 'hll2320dcupswrapper-3.2.0-1a.i386.deb'.
dpkg -b ./brother_driver_packdir hll2320dcupswrapper-3.2.0-1a.i386.deb
dpkg -i --force-all hll2320dlpr-3.2.0-1a.i386.deb
(Reading database ... 180979 files and directories currently installed.)
Preparing to unpack hll2320dlpr-3.2.0-1a.i386.deb ...
Unpacking hll2320dlpr:i386 (3.2.0-1) over (3.2.0-1) ...
Setting up hll2320dlpr:i386 (3.2.0-1) ...
dpkg -i --force-all hll2320dcupswrapper-3.2.0-1a.i386.deb
Selecting previously unselected package hll2320dcupswrapper:i386.
(Reading database ... 180979 files and directories currently installed.)
Preparing to unpack hll2320dcupswrapper-3.2.0-1a.i386.deb ...
Unpacking hll2320dcupswrapper:i386 (3.2.0-1) ...
Setting up hll2320dcupswrapper:i386 (3.2.0-1) ...
lpinfo: Bad file descriptor
lpadmin -p HLL2320D -E -v usb://dev/usb/lp0 -P /usr/share/ppd/brother/brother-HLL2320D-cups-en.ppd
lpadmin: Unable to connect to server: Bad file descriptor
###############################ls: cannot access '/usr/share/ppd/*.ppd': No such file or directory
#
The security level of AppArmor has been lowered. (aa-complain cups)
aa-complain cupsd
Setting /usr/sbin/cupsd to complain mode.
lpinfo: Bad file descriptor

0 (I): Specify IP address.
1 (A): Auto. (usb://dev/usblp0)

select the number of destination Device URI. ->1

lpadmin -p HLL2320D -v usb://dev/usblp0 -E -P /usr/share/cups/model/brother-HLL2320D-cups-en.ppd
lpadmin: Unable to connect to server: Bad file descriptor
Test Print? [y/N] ->n

Hit Enter/Return key.
paul@len780:~/Downloads$ 



```

The first thing that looks bad is that complaint about ia32-libs. This does not show up in Synaptic. The verbiage there seemed to imply that installing either lib32ncurses5 or lib32z1 would do the trick. I installed lib32ncurses5 but there was no change.

Later on there is a complaint about a bad file descriptor in running lpinfo or lpadmin. Perhaps that is due to the ia32-libs problem?

I can see the printer with lsusb, dmesg, etc. Any suggestions will be appreciated.

---

### Post by kurt18947 on 2017-07-29
Does the printer print? I recall something about ia-32libs being deprecated but have 2 Brother printers installed with an earlier version of Brother's script and both work as expected.

---

### Post by PaulBx on 2017-07-29
The printer works on a Windows machine. The one time I tried the "test print" here I got an error with the lpr command; I assume I still need to install another package to get that.

Here's another bit of information that may be relevant. Some parts of it may be dated, though. For example the ppd file name is different.
[http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&comple=on&redirect=on#f00081](http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&comple=on&redirect=on#f00081)

---

### Post by PaulBx on 2017-07-29
Ah, I'm getting close. I restarted cups "sudo service cups stop && sudo service cups start"  and the script started behaving, no more complaints about bad file descriptor. Now lpstat gives me this:

```

paul@len780:~$ lpstat -t
scheduler is running
no system default destination
device for HLL2320D: usb://Brother/HL-L2320D%20series?serial=U63877D7N643149
HLL2320D accepting requests since Sat 29 Jul 2017 05:47:11 AM PDT
printer HLL2320D is idle.  enabled since Sat 29 Jul 2017 05:47:11 AM PDT
paul@len780:~$ 

```

I installed lpr too. When running the test print command I notice a light flashing on the printer but nothing prints.

Before I forget it, I should note that running the brother script worked better (in the beginning) when I did an apt-get update... just so others referencing this thread to install a printer know what I did to get things working.

---

### Post by PaulBx on 2017-08-06
Well, I guess everything is OK now. It just started working. I assume a reboot is why, or a power cycle of the printer.

---

