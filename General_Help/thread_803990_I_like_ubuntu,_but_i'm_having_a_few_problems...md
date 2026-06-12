---
title: "I like ubuntu, but i'm having a few problems.."
date: 2008-05-22
forum: General Help
---

### Post by lhamil64 on 2008-05-22
I have had Ubuntu 7.10 installed on a spare computer as a dual-boot with xp pro. I have a few somewhat-irritating problems...

First,
when i turn on the computer, it just shows a blank screen after I select Ubuntu. I've tried this:
> 
1) Change the resolution in /etc/usplash.conf to 1280x800
2) Run "sudo update-initramfs -u -k `uname -r`"

But it didn't do anything.
I really want to know how to fix this issue once and for all.

Second,
When I log into my user account (I'm the only user) it attempts to connect to my wireless network and then prompts me for my network key. I have to set it to Hex and then type it in. I have a keyring setup (I guess) but it is still doing it. Once I type in the key and set it to Hex, it connects just fine (in fact, I'm typing this message on it right now!)
I would really like this issue fixed as well.

Thanks in advance for all help

---

### Post by NightwishFan on 2008-05-22
Disable usplash entirely.
```
sudo gedit /boot/grub/menu.lst
```
Delete "quiet splash"
Then save.

---

### Post by lhamil64 on 2008-05-22
Wow, thanks for the very quick reply. Of course, i just shut down my ubuntu box for the night but i will defiantly try it tomorrow.

---

### Post by NightwishFan on 2008-05-22
Good luck.

---

### Post by gfixler on 2008-05-22
> **NightwishFan said:**
> Disable usplash entirely.
```
sudo gedit /boot/grub/menu.lst
```
Delete "quiet splash"
Then save.

I had to do this in 7.10, but after an upgrade to 8.04, it's no longer a problem with quiet, and splash in there, and it's fun to see the splash screen at last. Just an FYI :)

---

