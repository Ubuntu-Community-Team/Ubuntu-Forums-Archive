---
title: "Booting Ubuntu on an External Harddrive"
date: 2008-02-13
forum: General Help
---

### Post by Mitchlb on 2008-02-13
Trying to keep this post alive

[http://ubuntuforums.org/showthread.php?p=4324633&posted=1#post4324633](http://ubuntuforums.org/showthread.php?p=4324633&posted=1#post4324633)

---

### Post by Mitchlb on 2008-02-13
Here's my question:

I just got a 500gb external harddrive. Can i install ubuntu on the harddrive?? So, rather than needing to dual boot, I can just plug in the harddrive whenever i wanted to use ubuntu??? If i can, how can i do this. If i can't, well, let me know. If at all possible, can i install ubuntu on 250gb rather than all 500??

It would function like Ubuntu normally would right?? Would it even be password protected??? And if i only did it on 250gb, when i plugged it into a computer using my usb port, would a "boot linux ubuntu 7.10" option come up? Because i also want to use it to transfer things from xp computer to xp computer.... Or would i, when i log into the computer itself, have to chose boot from external harddrive??? And if i didn't chose it, then i could transfer files????

And in regards to this [http://www.pendrivelinux.com/2007/11...sb-hard-drive/](http://www.pendrivelinux.com/2007/11...sb-hard-drive/)
How could I do it without removing the internal hardrives???

Thank you!

---

### Post by skippi90 on 2008-02-13
As I said in your other thread, I still am no further in achieving an external boot but for the internal hard drives question, simply exclude them from the boot order in your BIOS.

---

### Post by Mitchlb on 2008-02-13
How?

---

### Post by Mitchlb on 2008-02-13
I have a laptop and i don't really care if it gets wipped, is there a way this would help me do it easier? Would i still get 250gb?? And how would they operate (boot on start up or boot upon usb entry?)

---

### Post by Mitchlb on 2008-02-13
Is there no way, short of pulling my internal harddrive out, that i can install ubuntu 7.10 on 250gb of external hard drive??

---

### Post by Redeyes_Gambit on 2008-02-13
Ok, let me make sure I understand what you want to do before I even try to "help" :) . You want to:

1: Install Ubuntu to a 500 GB External USB hard drive
2: You would like ubuntu to use ONLY 250 GB of the external HDD
3: You want to be able to boot to Ubuntu or to Windows on whatever machine you plug the USB HDD into.

You also have these questions which I can answer right now :D :

Q1: What would happen if you plugged the USB HDD into a computer running Windows?

A1: Depends on whether we format the whole drive to use Ubuntu, or just a portion of it. Since you indicated you want to use only 250 gigs for Ubuntu, what would happen is pretty much what would happen with a "normal" USB hard drive. You plug in the drive, and Windows sees a drive with 250 Gigs of free space. Windows will only see 250 gigs of free space (the 250 that DOESN'T contain Ubuntu) because Windows can't normally understand the Linux filesystem. No, you will not be presented with an option to boot to Ubuntu, because as far as Windows know all you have is an average, run-of-the-mill USB hard drive. To boot to Ubuntu you would have to restart the computer and instruct your BIOS to boot off of the USB drive before the Internal HDD. This setting is ususally persistent, which means the order of HDDs your computer tries to boot to "sticks" after a reboot, or even shutting down the PC. In other words, you would set up your BIOS to try and boot to USB HDDs first, and then try the Internal HDD.



Q2: Would Ubuntu act the same installed on an external drive when compared to being installed on an internal drive?

A2: This answer is complicated. For all intensive purposes yes. To you, everything would appear to function the same, but underneath some things happen a little different. The main difference is during boot up, because when Ubuntu is installed on an external HDD it has to check what kind of hardware (CPU, Graphics card, etc.) it's sitting on.



Q3: Would Ubuntu be password protected? 

A3: As I said earlier, when you plug this HDD into Windows, you can't even see the Ubuntu data. That doesn't make the data safe, just hidden. When you boot to Ubuntu, yes, you can make it ask for a password just like if it were installed on an internal HDD. If you really want to make all the Ubuntu data secure we can talk partition-level encryption, but that's a WHOLE 'nother post :) .

---

