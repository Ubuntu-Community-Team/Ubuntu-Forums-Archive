---
title: "i used scanModem. i need to get my winmodem working now."
date: 2006-10-17
forum: General Help
---

### Post by fakie_flip on 2006-10-17
Please help with using a WinModem in Ubuntu 6.06 Linux. Thanks for reading. Here is the file created by running scanModem.

```
--------------------------  System information ----------------------------
 Ubuntu Linux Dapper Drake 6.06
Kernel 
Linux version 2.6.9-5 (bhcompile@decompose.build.ubuntu.com) (gcc version 3.4.3 20041212 (Ubuntu 3.4.3-9.EL4)) #1 Wed Jan 5 19:22:18 EST 2005
 scanModem update of:  2006_September_19


USB modem not detected by lsusb

 Modem or host audio card candidates have firmware information:
 PCI ID     Subsystem  Name
 ---------- ---------  -----------------
 11c1:0442  144d:2104  Communication controller: Agere Systems 

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev.tdb

 The kernel was compiled with gcc version 3.4.3 and a compiler is not installed

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	gcc-3.4  kernel-source-2.6.9-5


Checking pppd properties:
	-r-xr-xr-x  1 root root 251008 Nov  2  2004 /usr/sbin/pppd
To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
         chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	 chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
lock


 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:

     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
```

---

### Post by towsonu2003 on 2006-12-05
is this the modemdata.txt?

---

### Post by fakie_flip on 2006-12-05
yes

---

### Post by towsonu2003 on 2006-12-05
the whole thing? I can't see any mention of a modem... If the above is the whole thing, you might want to email linmodems people with this at [email]discuss@linmodems.org[/email].

But it's weird, because modemdata.txt also has instructions on how to contact them, apart from instructions to make a modem work. 

PS. my google search indicates this is an lucent modem. while contacting them you could ask that too. For lucent modems, see 
1. [https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent) to setup the modem
2. Section two at [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) to set up the dialer

---

