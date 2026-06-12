---
title: "System hangs up"
date: 2013-06-20
forum: General Help
---

### Post by theoderich on 2013-06-20
Hey there,
 

 I have a problem. I guess the bottom-line is that my new ubuntu 13.04 hangs up after a couple of minutes. But it has a story:
 

 I used ubuntu 12.04 and win7 in dualboot. Over time, win7 got pretty slow and infested with some nasty viruses. So I decided to drop it and just use ubuntu as my only os. But I had to reinstall win7 first, because I needed lightroom to get a job done (I'm currently working on my darktable skills). After formating and installing the new win7 in the very same partition of the old one, the ubuntu boot was gone. I tried GRUB but couldn't fix the problem. So I just got my job done and decided to clean the whole hard drive and set up Ubuntu 13.04 fresh and new. I used Killdisc to erase all previous data (and – so i hoped – my problems). But Killdisc hang up everytime. After a couple of minutes the screen went black and nothing worked but the reset button. After 3 or 4 attempts with both the erase and the recovery function I gave in and just set up Ubuntu 13.10. It all worked fine but my pc just hangs up after a certain time. The screen goes black, the lamp of the screen turns orange (that usually indicates hibernation) and nothing works.  
 

 Does anyone have an idea what might be wrong? To me it seems to be a memory problem or sth similar. Is there a way to find that out?  
 

 Help is highly appreciated

---

### Post by dino99 on 2013-06-20
It can be this or/and that sadly.  Is it a homemade system or a branded one ? Hope your bios (uefi ?) is not MS tatooed, making it unusable with something else but MS.
To grab some hints, boot with ubuntu from an usb stick (or cd), then load gparted (formatting tool) to check for possible error (red triangle warning). If you cant find something usefull, then continue using ubuntu from the cd/usb, then glance at the logs : /home/user/.xsession-errors (ctrl+h to unhide it) and /var/log/dmesg.

The other question is about a stable/unstable electric psu or provider

---

### Post by Supercomputerpower on 2013-06-20
maybe it is a mixup between desktop and laptop version. my laptop broke i plugged harddisc without any changes in to my desktop everything works exept hibernation then it freezes maybe this link helps out [http://ubuntuforums.org/showthread.php?t=1632953](http://ubuntuforums.org/showthread.php?t=1632953)

---

