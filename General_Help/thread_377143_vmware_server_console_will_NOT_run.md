---
title: "vmware server console will NOT run"
date: 2007-03-05
forum: General Help
---

### Post by Snail Wins! on 2007-03-05
Hi, this is my first new topic. I've been pulling my hair out since I did a distribution upgrade from Dapper to Edgy (through the built in GUI updater, not command line). 

My vmware server console does not want to work with the new kernel (2.6.17-11). I've run vmware-config.pl multiple times, uninstalled vmware completely and reinstalled it, etc. etc. But no matter what I do, running 'vmware' from the command line completely hangs the program. Nothing appears.

I don't know where the log files are located and I know that would help, but does anyone have any advice for me?

---

### Post by llamakc on 2007-03-05
The logs are in /var/log/vmware

Try tailing the log in one pty as you start it in another.

---

### Post by Snail Wins! on 2007-03-05
I got it to work by running vmware with this command at the command prompt:

LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware

Found it on this blog:
[http://blog.bz2.nl/2006/10/27/vmware-server-console-on-ubuntu-610-edgy-eft-hangs/](http://blog.bz2.nl/2006/10/27/vmware-server-console-on-ubuntu-610-edgy-eft-hangs/)

Thanks!

---

### Post by jkugler on 2008-06-19
> **Snail Wins! said:**
> 
LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware


This gets vmware-server-console running as well on Hardy. Strange.

---

