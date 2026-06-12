---
title: "Master Record Boot Sector Has changed - Problem booting up my PC"
date: 2007-04-13
forum: General Help
---

### Post by jcroot on 2007-04-13
[LEFT]Hi!

I have a **Compaq Presario 5310US Desktop PC **and I installed Ubuntu 6.10 in this computer... But I have a problem, everytime I turn on the computer (start the computer) I see this error message with a black screen:

[B]Attempting to Boot from CD Room
Attempting to Boot from Floppy A
Attempting to Boot from Hard Drive C

1999 Master Record Boot Sector Has changed.

Press any key to enter setup and restore the MBR.[/B]

So if I press any key I see a little blue screen asking me for a password (I think this is the Bios password) so I just hit "Enter" and it takes me to the Bios Setup, I'm allow to see the configuration but not to change the configuration.

What should I do to fix this problem? I tried installing Windows XP Pro (before Ubuntu) in this computer but I have the same exact problem, so I installed Ubuntu 6.10 thinking it will solve this problem but it didn't work out.

Something strange... when I insert the Windows XP CD (having windows xp installed first) I didn't see the error message, but if I take out the Windows XP CD and try to restart the PC I see the error message above.

**This is what I tried so far:**

[LIST=1]
[*]Removing the COSMO Battery from my PC
[*]Running Windows XP Recovery Console and type fdisk /mbr at the command prompt, but when I do this it tells me that the command is not recognized.
[*]I tried changing the computer memory.[/LIST]**The Boot order is:**

CD ROOM = First
Floppy A = Second
Hard Drive = Third

Can any body please help me with this? I would love to have Ubuntu 6.10 in this PC.


[/LEFT]

---

### Post by NICU on 2007-04-13
Hi, do you already have Ubuntu installed on this PC?  Are you trying to dual boot Ubuntu and Windows or just one or the other?  Can you boot up using a LiveCD?  If so go to the partition editor on the live CD, and check out the partitions on your hard drive.  If you can let me know what partitions are there and what data or OS you think is on each partition we can help you make some progress.

---

### Post by ajgreeny on 2007-04-13
It sounds as if your bios is going crazy or something like that, so removing the battery should have put it back to default.  Anyway, here is a possible answer to your difficulty.

The command at the winXP recovery module is "fixmbr", not "fdisk /mbr".  Try that and see if it gets you back to windows, at least, then you can restore grub and hope that it doesn't go wierd on you again.

---

### Post by jcroot on 2007-04-13
> **NICU said:**
> Hi, do you already have Ubuntu installed on this PC?  Are you trying to dual boot Ubuntu and Windows or just one or the other?  Can you boot up using a LiveCD?  If so go to the partition editor on the live CD, and check out the partitions on your hard drive.  If you can let me know what partitions are there and what data or OS you think is on each partition we can help you make some progress.

Thank you for your reply... I'm not trying to to dual boot windows and Ubuntu, I just want Ubuntu to be install in this computer, Yes! I already have Ubuntu installed in this computer but is not booting up.

Yes, I'm able to boot my PC from the Live CD, can you please tell me how to get to the partition editor using the live CD?

---

### Post by jcroot on 2007-04-13
> **ajgreeny said:**
> **It sounds as if your bios is going crazy or something like that**, so removing the battery should have put it back to default.  Anyway, here is a possible answer to your difficulty.

The command at the winXP recovery module is "fixmbr", not "fdisk /mbr".  Try that and see if it gets you back to windows, at least, then you can restore grub and hope that it doesn't go wierd on you again.

I believe the same thing... well I tried the "fixmbr" using the Windows XP Recovery Module but is not working, it tells me that it did successfully restore my MBR but it didn't work. A friend of my told me to use the "fdisk /mbr" but that command doesn't existe in the windows recovery module.

I would like some help please. I think the problem is with my Bios, it has a password which I don't know, like I said before I'm able to enter the Bios Setup but I'm not able to make any changes here because of the password. I tried removing the battery cosmo battery I guess and it didn't work for me.

---

### Post by jcroot on 2007-04-13
Any help please?

---

### Post by NICU on 2007-04-13
I would suggest reinstalling GRUB using the LiveCD.  I followed this tutorial to dual boot my PC (I know you only want Ubuntu), and at the end it explains how to reinstall GRUB - [http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp](http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp)

To sum up use these commands in the command line:
```
sudo grub
find /boot/grub/stage1

``` It will return the location on your hard drive where GRUB is located, most likely (hd0,0).  Use that response in the next command:
```
root (hd0,0)
setup (hd0,0)
```
This should allow you to boot Ubuntu by default.  If that doesn't work let me know again.  Ignore the sections on installing Windows if you don't want it, just read over the GRUB sections.

---

### Post by K.Mandla on 2007-04-13
It might be a virus protection feature too. I used to have a motherboard (PCChips, I think?) that included a boot record virus scan option. It never behaved like that, but I can see where it might. Do you have anything like that in your BIOS? some way of turning off an on-board virus protection routine? 

Just a thought.

---

### Post by jcroot on 2007-04-13
> **NICU said:**
> I would suggest reinstalling GRUB using the LiveCD.  I followed this tutorial to dual boot my PC (I know you only want Ubuntu), and at the end it explains how to reinstall GRUB - [http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp](http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp)

To sum up use these commands in the command line:
```
sudo grub
find /boot/grub/stage1

``` It will return the location on your hard drive where GRUB is located, most likely (hd0,0).  Use that response in the next command:
```
root (hd0,0)
setup (hd0,0)
```
This should allow you to boot Ubuntu by default.  If that doesn't work let me know again.  Ignore the sections on installing Windows if you don't want it, just read over the GRUB sections.

Do you think reinstalling the GRUB might fix the problem? I really don't think so since my GRUB is not corrupted, but I will give it a try.

---

### Post by jcroot on 2007-04-13
> **K.Mandla said:**
> It might be a virus protection feature too. I used to have a motherboard (PCChips, I think?) that included a boot record virus scan option. It never behaved like that, but I can see where it might. Do you have anything like that in your BIOS? some way of turning off an on-board virus protection routine? 

Just a thought.

I don't think there is a way to turn off the virus protection option, I don't think there is option either...

---

### Post by jcroot on 2007-04-14
Any help please?:(

---

### Post by confused57 on 2007-04-14
I believe there must be a mbr restore in your bios setup...there "should" be a way to disable this feature.  Might take some searching in submenus to find it.

---

