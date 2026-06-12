---
title: "Remove System Startup Links (Gutsy)"
date: 2007-11-27
forum: General Help
---

### Post by myrice on 2007-11-27
I was trying to install the new ATi drive via [this tutorial]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") and I'm at this step:

> Now, make this run before gdm (which starts with sequence number 13)

sudo update-rc.d ati-module-fix defaults 12

It is possible that gdm sequence number is different. To find the gdm sequence number:

ls /etc/rc2.d/

And substitute 12 in the previous command with gdm sequence number - 1. 

I've realized that GDM on my system starts at S30, which means I need to adjust the number to 29.

Well, the problem here is I've already linked it to 12 accidentally (serves me right for not reading ahead...).

When I try to just retype the command with 29 in place, the terminal tells me that System Startup Links for /etc/init.d/ati-module fix already exist.

Is there a way to unlink it?

---

