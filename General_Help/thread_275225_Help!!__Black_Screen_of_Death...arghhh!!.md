---
title: "Help!!  Black Screen of Death...arghhh!!"
date: 2006-10-11
forum: General Help
---

### Post by skygazer4k on 2006-10-11
Help!!:???: 
 My ATI card was listed as unknown so I was attempting to update my driver. I  followed the steps in the Ubuntu Dapper Installation Guide [HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29"). All I did was follow steps in part.1. got to the reboot part (sudo shutdown -r now) and when my box restarted it booted to a dead black screen. Nothing at all but blackness... How do I restore back to my previous setting that worked? I tried the recovery option but being a newbie at this I didn't know where to start?. Im running a dual boot HP Pavillion DV8000 MCE 17" Laptop. Grub loader and XP works fine as well as the Live-DVD im running now but I can't access the files on the drive from live mode or from XP.
Please Help.
Thank You'
Sky' 8) 

These are the exact commands that caused this Fudge-Mire:

[COLOR="Red"]sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now[/COLOR]

---

### Post by bigken on 2006-10-11
boot into single user mode and type sudo dpkg-reconfigure xserver-xorg
and select ati as your driver ;)

---

### Post by skygazer4k on 2006-10-11
Thank you BigKen.
 That worked like a charm. One thing to linux is that you definately learn something new every day. So it seems anyway. I really appreciate your fast help. One thing I would like to know is what could have caused such a problem? I mean I followed exactly the real ubunto directions. Not some posted trick or tweak. Is it typically this easy to inexplicably mess things up to a non-bootable condition? I would really like to see more support for current major hardware vendors driver upgrading fromm within ubuntu's auto update system. That would be nice. anyway, thanks again.
Sky' 8)

---

