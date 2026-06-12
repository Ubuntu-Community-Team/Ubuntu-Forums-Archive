---
title: "Portable Hard drive booting issues"
date: 2007-11-07
forum: General Help
---

### Post by Tyke91 on 2007-11-07
OK: My mission is to install Ubuntu 7.10 on an 80 gig portable USB hard drive so that I can boot it on my friends' computers and show off the marvel of Ubuntu linux, the huge repositories, the Desktop effects, and the speed/virus freeness.

I've hit a roadblock in my mission in that in order to boot from this hard drive, I must create an entry in GRUB for it. Most of my friends use exclusive windows, so this will not work well. I'm trying to get a setup like DSL where you can just plug the thing into a computer, boot from the usb drive, and go. how can I achieve this?


So far I've just done a standard install of gutsy onto this hard drive.

---

### Post by neilengineer on 2007-11-08
Why don't you just use the Ubuntu livecd??

---

### Post by MrFSL on 2007-11-08
Well, you could try installing Grub on the USB drive instead of the internal drive (as long as the BIOS supports booting from USB Disk.)

---

### Post by Tyke91 on 2007-11-08
how would I do that?

I know the config file for the hard drive is on (hd0,4) and the one for the usb file is (hd1,0)

so would It be

root (hd1,0)

setup (hd1) 
?

I'm not using the live CD because I would like to have persistance.

---

### Post by atlfalcons866 on 2007-11-08
does your computer support booting from a usb drive?

---

### Post by Tyke91 on 2007-11-08
yes, and so do the computers that I plan to boot on. 

I've done this before with Damn Small Linux, but unfortunately, a thief broke into my dorm room and stole it, along with $5 in quarters (laundry money) and a few other trinkets..

I'd like to do something similar (but bigger and flashier) with ubuntu.

---

### Post by logos34 on 2007-11-08
> **Tyke91 said:**
> I know the config file for the hard drive is on (hd0,4) and the one for the usb file is (hd1,0)

so would It be

root (hd1,0)

setup (hd1) 
?

yep, you have the right idea.

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
(-->post #502)

you then need to change the 'root' (and 'groot') lines on the USB /boot/grub/menu.lst from (hd1,0) to (hd**0**,0)

---

### Post by Tyke91 on 2007-11-08
Good news and bad news.

good news, it now boots on my computer

bad news, it won't boot on any OTHER computer... which kind of defeats the whole point.

anything else I could be missing?

---

### Post by MrFSL on 2007-11-08
When your computer boots the first section of the disk drive or partition is examined for boot information.

When you use Grub you have to tell it when to install this boot information. It sounds like you have elected to install Grub on you local HDD. This is necessary if your computer does allow for booting from usb (most older BIOS do not allow this). Now when you take this usb drive to another system you are missing this "bootsector" information.

If you want (and your computer supports booting from USB -- AND you have supported USB device that your BIOS recognizes) you can try to install this bootsector information to the USB drive itself. HOWEVER, this is problematic because you will have to configure grub to boot from this device. When moving to another computer,with different hardware, and a different BIOS / configuration you more then likely would have to reconfigure GRUB to support this new computers disk layout etc.

---

### Post by Tyke91 on 2007-11-09
ouch... 

then how does DSL do it? I was able to boot from a pen drive just fine. If it means changing distros, that's OK. I'd like to try most distros at least once (even though Ubuntu will probably remain my favorite) I'd prefer something debian based like knoppix or DSL tho... RPM gives me headaches :/

---

### Post by MrFSL on 2007-11-09
There is no magic behind DSL. If you installed DSL to a usb drive and it worked on various machines, then those machines supported booting from USB in their BIOS and the bootsector information was contained on the USB disk. You were just lucky that these machines usb devices / serial drives matched that of the original computer enough that you didn't have to edit menu.lst.

---

### Post by Tyke91 on 2007-11-09
ok, that makes alot of sense. I tested dsl on alot of computers that were the same make/brand. 

I guess i can just try it out on random computers to see if it works.

---

### Post by MrFSL on 2007-11-10
Had a thought... perhaps I am wrong. If DSL (which I admit I don't use) is like Knoppix (which I have used) then it probably doesn't use GRUB at all.

it probably uses syslinux / isolinux / or a derivative of those. If I remember right, Knoppix allows you to save information to a drive, and then when it boots, a simple kernel is loaded that scans for the files Knoppix needs to load and boot from.

I'll have to check out DSL and get back to ya.

EDIT:
Yeah just checked out the instructions at DSL:
[http://damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive](http://damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive)

It seems that by default the boot record is stored to the usb disk and syslinux is used to make the drive bootable. It goes on and explains how to use Grub but:
>  Alternative I: Using GRUB as boot loader

Note: This method has been reported not to work under certain conditions 

---

