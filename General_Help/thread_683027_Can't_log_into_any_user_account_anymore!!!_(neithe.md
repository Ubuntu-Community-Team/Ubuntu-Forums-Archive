---
title: "Can't log into any user account anymore!!! (neither root nor normal users)"
date: 2008-01-30
forum: General Help
---

### Post by MacGeneral on 2008-01-30
Ok yesterday I had the "great" idea of setting up a LDAP Server on my old PC (with Ubuntu 7.10 Server Edition).

I followed **[this guide]("http://www.debuntu.org/ldap-server-and-linux-ldap-clients")** server and client side..

When I started my Notebook today (client) I had some weird **[bug]("https://launchpad.net/ubuntu/+source/libnss-ldap/+bug/51315") [(more info)]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=375077")** which made it unable for me to get Linux to start (it took down the start process). Short description of the bug would be "couldn't find the ldap server..." which was nothing unexpected because it tried to find it before the network interfaces were configured and (because my notebook mainly uses wlan) I thought there would be no hope to change it (Single User Mode didn't help because the script was in some low init.)

After several reboots I got the script killed with CTRL + C before it could start spamming me... and Debian booted up.

I thought it was clever to uninstall all LDAP stuff (including config files / all packages mentioned in the guide) so I logged in as root and typed:
```
#apt-get remove --purge libnss-ldap libpam-ldap nscd
```
it worked with no problems but when I rebooted

**I couldn't login at all anymore... Neither root, nor user accounts. As soon as I type the username and press Enter it says "Login incorrect". It doesn't even let me type the password.**

I booted my Notebook with the Ubuntu Server CD in Rescue Mode (note it has Debian 4 unstable installed but I just wanted to get into a Shell and couldn't find my Debian CDRW ;)) to check for my /etc/passwd files etc... everything was still there.

I can't check the file permissions because the rescue mode doesn't recognize ls -l | grep passwd (ls - small L) and without grep the list is too long so passwd is gone already (is there a way to scroll through it?)


I need your help fast, I don't want to reinstall Debian again (it works perfectly right now) and I just had to reinstall it some weeks ago when my old Notebook died on me...

Is there any way to recreate the user accounts (from the rescue mode cd) and then login? or do you think the ldap stuff might mixed something completely different up which blocks access to the passwords/useraccounts?? Note that I could login before uninstalling it and couldn't right after (but if I hadnt uninstalled it I couldnt use Debian either because of the LDAP bug...)


Thanks for your help


Edit:
can it have something to do with the **nsswitch.conf**? If yes, how would I get a fresh default copy of one? (I would have to type it manually with nano in the terminal but I wouldn't mind if that would fix it!!)


Edit 2: Ok that was a quick one... it was the **nsswitch.conf**... I set it back to something similar to [this]("http://www.debianforum.de/forum/viewtopic.php?p=581994&sid=542283be514d6312bab1652b58934da2")

Im sorry for posting this, but after trying to figure it out the past few hours and imagining to format my notebook again I thought it was best to post something here... I hope that this thread might help people with the same problem at least though :p

Thanks anyways

---

