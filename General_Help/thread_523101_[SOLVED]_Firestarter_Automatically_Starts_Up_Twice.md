---
title: "[SOLVED] Firestarter Automatically Starts Up Twice"
date: 2007-08-11
forum: General Help
---

### Post by Flashgordon20 on 2007-08-11
Following various threads, I was able to successfully configure firestarter to start automatically when I log in. However, it starts 2 instances of it instead of one. All I have to do is right click on one of them and select exit (in the panel). But its a bit annoying and would like just one instance to start instead of two. . Here is my /etc/sudoers

> # /etc/sudoers
# 
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

#Bug: [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/30291](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/30291)
# [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/47662](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/47662)
#Defaults !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"


Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

username ALL= NOPASSWD: /usr/sbin/firestarter

Any help would be appreciated. Thank You

---

### Post by capink on 2007-08-11
Actually you don't need to start firestarter at all. It just a frontend for iptables. So after configuring it the settings will be permanent because iptables is always running. 

Even after restarting it still activate the settings you have chosen via firestarter no matter if it is running or not.
These settings are lost only if you modified them in firestarter or used the command line to flush iptables rules.

---

### Post by kast on 2007-08-11
is there a reason you need the GUI to start up on boot?



[http://ubuntuforums.org/showpost.php?p=2088904&postcount=3](http://ubuntuforums.org/showpost.php?p=2088904&postcount=3)

---

### Post by ruibernardo on 2007-08-11
What capink is saying is true, but if you have two Firestarter instances starting, then you have either two firestarter calls in your "Sessions" preferences or you didn't run the Wizzard the first time you ran Firestarter. 

Close one of the Firestarter instances and click on the "Firewall" menu and then in "Wizzard". Check your sessions preferences too.

---

### Post by Flashgordon20 on 2007-08-11
> **epimeteo said:**
> What capink is saying is true, but if you have two Firestarter instances starting, then you have either two firestarter calls in your "Sessions" preferences or you didn't run the Wizzard the first time you ran Firestarter. 

Close one of the Firestarter instances and click on the "Firewall" menu and then in "Wizzard". Check your sessions preferences too.

The culprit was in the sessions preferences. It was configured to start twice. Also, Thanks to everyone for the info regarding the iptables. I was not aware it automatically started up.

---

