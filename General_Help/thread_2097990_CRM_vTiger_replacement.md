---
title: "CRM vTiger replacement ?"
date: 2012-12-25
forum: General Help
---

### Post by ELMIT on 2012-12-25
I used the past years vTiger. So far I did not dig to deep into it, but was good.

Recently upgrade of php broke the system and vTiger does not work anymore.

I am looking for a way to use a virtual machine, where I downgrade php to the level vTiger can work with (how do I do that?)

or

another CRM, that can work with the latest php version.

I am too small to use any paid (online) version, so that would not be a choice yet.

---

### Post by rtbarker on 2012-12-25
I ran into problems with PHP 5.4 and VTiger as well.  

I was trying to get a test setup of VTiger running under Xampp, but Xampp has PHP 5.4.  I later found out that there have been some changes to the PHP language between 5.3 and 5.4, these changes break VTiger.

I eventually used VirtualBox to setup a testing server running Debian Stable, which has PHP 5.3.  I believe that Ubuntu 12.04 LTS also has PHP 5.3, so that could be an option for you instead of Debian.

In addition, I found this thread, which may be of help with downgrading PHP: [http://ubuntuforums.org/showthread.php?t=2074178](http://ubuntuforums.org/showthread.php?t=2074178)

---

### Post by ELMIT on 2012-12-25
Thanks that was exactly what I was looking for. I will install it tomorrow and use Ubuntu 12.04 iso.

I need one more hint:
I have my database on my local host and I used to come into the system vial ssh and dyndns as well as localhost.

I want to keep that, just point to the virtual machine - I have never done that before. And I want to use my database on the localhost. So when later (maybe) vTiger is available for php 5.4.x I do not need to change anything.

---

### Post by rtbarker on 2012-12-30
Hi, sorry for the delayed reply.  

Just to check that I understand what you're doing.  You want the virtual machine to act as a "front end" with the Apache & PHP side on there.  You then want to forward the MySQL connection from the virtual machine to the MySQL DB on the physical machine?

You could try using either IPTables or SSH to do some port forwarding.  If you don't want to forward to the external address of the physical machine, you could try to setup an internal network in Virtualbox and forward via that?

---

### Post by ELMIT on 2013-01-08
Some of the vTiger user made a patch to address all changes in php and I hope it works. So, for the time being I don't need to get the VM talking to the host's mysql server.

---

