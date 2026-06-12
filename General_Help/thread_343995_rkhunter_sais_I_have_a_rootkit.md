---
title: "rkhunter sais I have a rootkit"
date: 2007-01-22
forum: General Help
---

### Post by pmark on 2007-01-22
I installed rkhunter through apt-get. A few days ago, I got this messege (through /var/mail/pmark)

```
From root@ubuntu Fri Jan 19 13:50:30 2007
Return-path: <root@ubuntu>
Envelope-to: root@ubuntu
Delivery-date: Fri, 19 Jan 2007 13:50:30 +0200
Received: from root by ubuntu with local (Exim 4.62)
	(envelope-from <root@ubuntu>)
	id 1H7sGM-0005RX-0u
	for root@ubuntu; Fri, 19 Jan 2007 13:50:30 +0200
Subject: [rkhunter] Daily run
Message-Id: <E1H7sGM-0005RX-0u@ubuntu>
From: root <root@ubuntu>
Date: Fri, 19 Jan 2007 13:50:30 +0200

Line: 
-e   [ Warning! ]
-----------------------------------------------------------------

Found warnings:
[13:50:28] WARNING, found:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

-----------------------------------------------------------------

If you're unsure about the results above, please contact the author of
Rootkit Hunter. Fill in contact form: http://www.rootkit.nl/contact/
Some errors has been found while checking. Please perform a manual check on this machine ubuntu

From root@ubuntu Sat Jan 20 14:32:20 2007
Return-path: <root@ubuntu>
Envelope-to: root@ubuntu
Delivery-date: Sat, 20 Jan 2007 14:32:20 +0200
Received: from root by ubuntu with local (Exim 4.62)
	(envelope-from <root@ubuntu>)
	id 1H8FON-0005QS-CC
	for root@ubuntu; Sat, 20 Jan 2007 14:32:19 +0200
Subject: [rkhunter] Daily run
Message-Id: <E1H8FON-0005QS-CC@ubuntu>
From: root <root@ubuntu>
Date: Sat, 20 Jan 2007 14:32:19 +0200

Line: 
-e   [ Warning! ]
-----------------------------------------------------------------

Found warnings:
[14:32:17] WARNING, found:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

-----------------------------------------------------------------

If you're unsure about the results above, please contact the author of
Rootkit Hunter. Fill in contact form: http://www.rootkit.nl/contact/
Some errors has been found while checking. Please perform a manual check on this machine ubuntu

From root@ubuntu Sun Jan 21 15:06:22 2007
Return-path: <root@ubuntu>
Envelope-to: root@ubuntu
Delivery-date: Sun, 21 Jan 2007 15:06:22 +0200
Received: from root by ubuntu with local (Exim 4.62)
	(envelope-from <root@ubuntu>)
	id 1H8cOr-0005Sg-Cf
	for root@ubuntu; Sun, 21 Jan 2007 15:06:21 +0200
Subject: [rkhunter] Daily run
Message-Id: <E1H8cOr-0005Sg-Cf@ubuntu>
From: root <root@ubuntu>
Date: Sun, 21 Jan 2007 15:06:21 +0200

Line: 
-e   [ Warning! ]
-----------------------------------------------------------------

Found warnings:
[15:06:19] WARNING, found:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

-----------------------------------------------------------------

If you're unsure about the results above, please contact the author of
Rootkit Hunter. Fill in contact form: http://www.rootkit.nl/contact/
Some errors has been found while checking. Please perform a manual check on this machine ubuntu

From root@ubuntu Mon Jan 22 00:17:41 2007
Return-path: <root@ubuntu>
Envelope-to: root@ubuntu
Delivery-date: Mon, 22 Jan 2007 00:17:41 +0200
Received: from root by ubuntu with local (Exim 4.62)
	(envelope-from <root@ubuntu>)
	id 1H8l0O-0005Up-R1
	for root@ubuntu; Mon, 22 Jan 2007 00:17:40 +0200
Subject: [rkhunter] Daily run
Message-Id: <E1H8l0O-0005Up-R1@ubuntu>
From: root <root@ubuntu>
Date: Mon, 22 Jan 2007 00:17:40 +0200

Line: 
-e   [ Warning! ]
-----------------------------------------------------------------

Found warnings:
[00:17:40] WARNING, found:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

-----------------------------------------------------------------

If you're unsure about the results above, please contact the author of
Rootkit Hunter. Fill in contact form: http://www.rootkit.nl/contact/
Some errors has been found while checking. Please perform a manual check on this machine ubuntu
```

Does this mean that I have a rootkit? Should I do something? Should I try to just delete /dev/.static, /dev/.udev, and /dev/.initramfs?

---

### Post by evilghost on 2007-01-22
False positive, consider using ossec-hids instead of rkhunter.

---

### Post by bodhi.zazen on 2007-01-22
Link: [OSSEC HIDS - Open Source HIDS](http://www.ossec.net/)

>  OSSEC is an Open Source Host-based Intrusion Detection System. It performs log analysis, integrity checking, Windows registry monitoring, rootkit detection, time-based alerting and active response.

It runs on most operating systems, including **Linux, OpenBSD, FreeBSD, MacOS, Solaris** and Windows.

---

### Post by evilghost on 2007-01-22
Here's a howto for use with Ubuntu, I'm using it and have good results...

[http://ubuntuforums.org/showthread.php?t=213445&highlight=ossec-hids](http://ubuntuforums.org/showthread.php?t=213445&highlight=ossec-hids)

---

### Post by pmark on 2007-01-22
evilghost and bodhi.zazen, thank you, both. You have saved me from a great deal of anxiousness.

---

### Post by bodhi.zazen on 2007-01-22
evilghost deserves all the thanks as I learned from both of his posts :p

---

### Post by arijarot on 2007-09-17
> **evilghost said:**
> Here's a howto for use with Ubuntu, I'm using it and have good results...

[http://ubuntuforums.org/showthread.php?t=213445&highlight=ossec-hids](http://ubuntuforums.org/showthread.php?t=213445&highlight=ossec-hids)

Thanks for the info and help:) had same issue as above.

---

