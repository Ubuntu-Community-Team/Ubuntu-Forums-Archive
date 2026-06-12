---
title: "Dual-Boot Error when booting from USB"
date: 2007-11-01
forum: General Help
---

### Post by Ian505 on 2007-11-01
Okay, I had a perfectly fine dual boot system with Windows XP pro and Ubuntu 7.10. I then got a portable USB hard drive and installed xubuntu on that. I plugged it in and I got a grub error. (25 I think) I unpluged the external drive- same thing. I used a SuperGRUB disk that I burned this past July for a similar problem to try and revive GRUB- no luck. I got a new error message. (Error 21) What do I do? I only booted by using the GRUBdisk and even then it only worked on windows. What did I do wrong? How do I make it so I can boot off the external hard drive from any computer?

Thanks,
Ian

---

### Post by Ian505 on 2007-11-01
Okay, I figured out why it wouldn't boot. I had to have the USB drive plugged in for GRUB to give me the Boot Menu. It appears that the USB drive with xubuntu currently contains the 'primary' os or whatever. (The first thing on the boot menu.) How do I get rid of the USB drive from the boot menu/GRUB!? Also, how do I install Ubuntu on the drive without making it necessary for it to be plugged in at boot? I want to bring the drive to school so I can demonstrated a KDE application to everyone, but I want to put both Ubuntu and the App on the portable drive so I can plug it into the school machine, boot from USB and away I go- but I don't want anything modified on the school computer. Kind of like a writable LiveCD. (LiveDrive- that rhymes.) I have been trying to do this thing for more than a week and a half now, can someone PLEASE help me? 

Thanks.
Ian

EDIT- I poked around in the linux forums and I think that I need help with my **menu.lst** file as error 21 means selected disk does not exist... if that helps at all.

---

### Post by Krispy101 on 2008-02-20
Sorry to necro this thread, but I couldn't see the point of spamming up the forums...

I've got the same problem.

Except It's on my laptop, main HDD is 60Gb, split into a 40gb partition for windoze, and a 20gb for Ubuntu.

The Portable HDD is my friends, as he wants Ubuntu on it, and it's 40gb.

WHen I boot with portable HDD plugged in, I can boot from my internal HDD, if I unplug the portable HDD, GRUB shows the dreaded error 21 like the chap above me.

Any help anyone?

Thanks, Kris

P.S My Old Ubuntu partition is /dev/sda2 (On my internal HDD)

Thanks, again, Kris

---

### Post by Krispy101 on 2008-02-20
Dust? Anybody? No?

Bump xD

---

