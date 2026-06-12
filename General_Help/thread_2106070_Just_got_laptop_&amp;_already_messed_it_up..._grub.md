---
title: "Just got laptop &amp; already messed it up... grub&gt;"
date: 2013-01-17
forum: General Help
---

### Post by mechelle69 on 2013-01-17
I just got my Dell Vostro 2520 with Ubuntu preloaded. I know nothing about operating systems. I wanted to try something different. Now my husband is pissed. I forgot my password...or did I set one up? Anyway, I was trying to reset it. I ended up with a black screen like dos. It had a place to set system, admin, and hdd passwords. I did this but I can't get out of this black screen hell. I have a message about minimal BASH line editing and a grub> prompt. My husband is on our other computer burning a new copy of the Ubuntu program. 

Please tell me that there is something simple that I have missed...

And, no, I am not a blonde!

Help, 
Mechelle

---

### Post by mechelle69 on 2013-01-18
I just got my Dell Vostro 2520 with Ubuntu preloaded. I know nothing about operating systems. I wanted to try something different. Now my husband is pissed. I forgot my password...or did I set one up? Anyway, I was trying to reset it. I ended up with a black screen like dos. It had a place to set system, admin, and hdd passwords. I did this but I can't get out of this black screen hell. I have a message about minimal BASH line editing and a grub> prompt. My husband is on our other computer burning a new copy of the Ubuntu program. 

I swear I am not a blonde. Lol.

---

### Post by mörgæs on 2013-01-18
Please don't double-post. 
Merged.

---

### Post by MG&amp;TL on 2013-01-18
Eh...usually that happens when the bootloader can't find the operating system. Not sure what you were doing while "resetting your password" (note no blonde jokes, hope you're impressed ;) ), but I imagine you managed to remove or resize a partition somehow. If you only just got the lappy (i.e. no data) and your husband is burning a disc anyway, it's probably easier just to reinstall.

---

### Post by sdowney717 on 2013-01-18
I agree, Easy to fix by just reinstall the OS.
Otherwise you try boot repair.
First boot the computer using a live usb.
Install and run boot repair.
It fixes grub issues

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2013-01-18
>  It had a place to set system, admin, and hdd passwords.

What had a place to set these things? Ubuntu? I do not think so. I think that you were in the BIOS (or should that be UEFI?) set up program.

Unless of course Ubuntu was installed with hard disk or the Home folder/partition encrypted.

So, Ubuntu was pre-installed? The seller should have provided you with the User name and passwords that were set up during the installation of Ubuntu.

You would then need to change those settings to a User name and password of your choosing.

Do you see a Grub Menu? If Ubuntu is the only OS, then press either Shift or Esc during boot.

If you get a Grub menu Select Recovery Mode. And then Resume. Please make a note of any error messages. Especially those that indicate why Grub cannot boot the Linux kernel.

It is possible to set a password for Grub (boot loader). You may be at a point where you need to put in a password to continue booting.

[https://help.ubuntu.com/community/Grub2/Passwords]("https://help.ubuntu.com/community/Grub2/Passwords")

We do not know what security methods the retailer has put on this machine. Did the machine come with instructions from the retailer?

Regards.

---

### Post by alphaamanitin on 2013-01-18
When I got my System76 it did not come with a username and password, I don't think grahammechinacal is right about that.  I suspect Dell would ship just like System76; turn on your computer and the Ubuntu GUI installation is what pops up.  

I would guess that you got into the BIOS or UEFI, likely UEFI settings if there is an HDD password.  If the computer is brand new and you haven't done anything with it than I strongly suggest you reset the BIOS or UEFI and reinstall Ubuntu.

AlphaA

---

