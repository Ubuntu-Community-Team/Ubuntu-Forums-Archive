---
title: "Big problem after hibernation:help"
date: 2007-06-18
forum: General Help
---

### Post by kilou on 2007-06-18
Hi,

my ubuntu install had been working quite fine until yesterday. I was running on battery and level became critically low. As I had set up the computer has completed hibernation processes correctly and then shut down correctly. This morning when I started the laptop, it went to the grub screen but then failed to boot displaying a error 29. I rebooted it but it didn-t want to boot Ubuntu, always displaying that error. I started to boot on XP since I-m dualbooting and  then again it failed to boot XP displaying error 29. Booting on the old kernel  (2.6.20-15) also produced the same error. The only way I could boot the computer was with the recovery kernel but then it loaded the hibernation image and booted on it. The computer was quite unstable and I immediatelz got a S.M.A.R.T error :(

I decided to reinstall from a backup. I booted on the LiveCD and wanted to reformat the different partitions but Gparted couldn-t do it and came with an error. Now there is a caution sign in front of some partitions on m drive in Gparted...

Anz clue what happened and how I can correct this? I-m really scared by this SMART notification.....

---

### Post by kilou on 2007-06-18
I must add it seems that all my partitions are locked because a lock icon appears next to every partitions of my disk in Gparted........

---

### Post by ukripper on 2007-06-18
SMART usually notifies if hard drive is going to die soon. But  I am not really aware of what SMART error is on your machine I could be wrong. But if I were you i would create latest backup as soon as possible, for such cases I have got ide to usb adapter which fakes drive to be usb when connected and you can easily backup.

---

