---
title: "scrip on ubuntu startut"
date: 2015-05-13
forum: General Help
---

### Post by mouitido on 2015-05-13
Rev:
Ubuntu 14.04
Hello,
I'm trying to take my head, and probably for ********.

Let me explain

For the test I would like firefox starts when ubuntu starts.
For the moment I made 3 attempts only 1 working.

Detail
First attempts succeeded.

In preference to applications start-->Add

Name: firefox
Command: bash Documents / start_firefox.sh

(Detail sh)
firefox
exit 0
--------------------------------------------
2nd hand trying rat etc / init.d
Following the method of

[http://www.nuleninfo.com/tutoriels/amat](http://www.nuleninfo.com/tutoriels/amat) ... ge-ubuntu /
[http://blog.cheztoi.net/2009/08/30/ajou](http://blog.cheztoi.net/2009/08/30/ajou) ... u Service /

Here I wanted launched through /etc/init.d

I created a file
sudo gedit /etc/init.d/mon_service

Inside I put
#! / Bin / sh
firefox

Executed
sudo chmod + x /etc/init.d/mon_service

added to boot

sudo update-rc.d mon_service defaults 80

NOTHING BUT THE FINAL
----------------------------------------
3rd rat tries from /etc/rc.local

I edited
rc.local

#! / Bin / sh -e
#
Rc.local #
#
# This script is Executed at the end of Each multiuser runlevel.
# Make sour que la script will "exit 0" on success or Any Other
# Value on error.
#
# In order to enable or disable this script just change the execution
# Bits.
#
# By default this script Does Nothing.
firefox
exit 0

But nothing either
----------------------------------------------------------
I think going through /etc/rc.local would be easier for my tests

Thank you in advance for your time and help


for the 3
when a tape
/etc/rc.local start

the scrip is working, but not when ubuntu start

---

### Post by dino99 on 2015-05-13
[http://stackoverflow.com/questions/7221757/run-automatically-program-on-startup-under-linux-ubuntu](http://stackoverflow.com/questions/7221757/run-automatically-program-on-startup-under-linux-ubuntu)

---

