---
title: "Ubuntu 7.04 taking forever to boot"
date: 2007-06-20
forum: General Help
---

### Post by gregorygreg on 2007-06-20
ubuntu is taking an excruciatingly long time to boot on my dual core intel laptop.  what exactly can I do to diagnose and solve this problem?

thanks in advance,
greg

---

### Post by Ayuthia on 2007-06-21
You might take out the splash screen and see what is being loaded and see if it stalling anywhere.

---

### Post by gregorygreg on 2007-06-21
yeah that is what I would like to do. how do I disable the boot screen?

---

### Post by Crafty Kisses on 2007-06-21
> **gregorygreg said:**
> ubuntu is taking an excruciatingly long time to boot on my dual core intel laptop.  what exactly can I do to diagnose and solve this problem?

thanks in advance,
greg

You might want to boot into verbose mode and see where it stops. just a thought.

---

### Post by Ayuthia on 2007-06-21
When the grub menu comes up to select your operating system, select ubuntu and instead of pressing enter, press 'e'.  This will bring up another list of items and you will need to highlight the kernel line and press 'e'.  You will need to erase 'quiet' and 'splash'.  This will remove the boot splash and show more information.  Once you remove these two items, press enter and then 'b' to boot.

---

### Post by gregorygreg on 2007-06-21
ok I took care of that and when I updated grub and rebooted I saw that it was taking the longest in the "configuring network devices" phase.  can this be troubleshooted?

---

### Post by Silenus on 2007-06-21
Do you have a wired network, or wireless? Usually that is where it is detecting connection. Does it list out like a ping time like it is trying to locate?

---

### Post by Ayuthia on 2007-06-21
I had a similar issue like that.  I can't remember where I got it from ([www.ubuntugeek.com](www.ubuntugeek.com) possibly), but you could try and edit /etc/network/interfaces and comment out your wireless entry.  An example of what it should look like (eth1 as wireless):
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
##iface eth1 inet dhcp

---

### Post by gregorygreg on 2007-06-21
yep that fixed it!~

thanks!

---

### Post by arijarot on 2007-06-24
how do you get a "verbose mode" at boot up?

---

