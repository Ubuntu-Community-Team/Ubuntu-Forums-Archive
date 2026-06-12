---
title: "[SOLVED] Need urgent help restoring MBR on friends laptop"
date: 2007-11-09
forum: General Help
---

### Post by garethrv on 2007-11-09
Hi,

Alright, I just used a friends Vista laptop to install 7.10 onto an external usb drive.

Problem is the install put grub onto the laptops MBR (I didnt mean to touch the laptops internals at all.)

This is my friends laptop and now if the usb drive is not plugged in nothing will boot, I just get a grub error 21.

If the drive is plugged in I can select vista from the grub menu.

I really need to fix this laptop as my friend will freak if they think their laptop is broken.

I dont have any vista recovery disks. I need to restore the MBR, please please help.

Thank you all in advance.

---

### Post by JawsThemeSwimming428 on 2007-11-09
The only way I know of is to boot to the Vista Recovery Environment and restore the MBR. I destroyed mine by accident when I installed Fiesty. Can you get the disc?

---

### Post by garethrv on 2007-11-09
No I cant get the disk.

It was am OEM install of vista basic and the disk is at the parents house of my friend which is no where near us.

Please someome tell me there is a solution to this.

---

### Post by garethrv on 2007-11-09
Oh my god.... I was freaking out so much.

Thanks so much for your fast response Jaws the support was good, I was seriously sweating.

Anyway, I have fixed it. I found a little program which manages the bootloader in vista and I was able to restore it all to original. *Huge sigh.......*

All is well

---

### Post by Maestro23 on 2007-11-09
> **garethrv said:**
> Oh my god.... I was freaking out so much.

Thanks so much for your fast response Jaws the support was good, I was seriously sweating.

Anyway, I have fixed it. I found a little program which manages the bootloader in vista and I was able to restore it all to original. *Huge sigh.......*

All is well

Good deal.  If I were you or your friend, I would make those Vista Recovery/Repair discs like Uncle Bill suggestes you do when you 1st get your system.

*Especially if you go around trying to install a brand new OS that you are not famiiar with on the same system.:)

Just some friendly advice.:guitar:

---

### Post by inversekinetix on 2007-11-09
Good that you got it fixed.  Could you mark the thread as solved, using the thread tools?

---

### Post by garethrv on 2007-11-09
Hey,

Just so you know how I solved it all.

EasyBCD 1.7 was the solution. Also let me add ubuntu to the original vista bootloader.

Thanks again everyone, I am currently making restore disks for her now.

Cheers.

---

### Post by inversekinetix on 2007-11-09
Good Stuff

---

