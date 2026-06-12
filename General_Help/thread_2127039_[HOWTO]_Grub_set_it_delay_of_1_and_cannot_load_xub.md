---
title: "[HOWTO:] Grub set it delay of 1 and cannot load xubuntu to fix it!"
date: 2013-03-18
forum: General Help
---

### Post by JoshuaMiller0 on 2013-03-18
Hi, I was messing with my grub a few weeks ago and I decided to set the delay to 1 which would give me enough time to quickly press an arrow and interfere with the timer. Unfortunately 1 might as well be 0 and my Grub which has Xubuntu and windows will always load windows. I am unable to run xubuntu and it had important files on it. Holding down either or both shifts or pressing escape will not do anything. No matter what, I cannot seem to load xubuntu. I have a usb with Xubuntu 12.04 boot thingo on it and I tried booting with xubuntu and modifying it. It did not work. I cannot access my files on xubuntu and I badly need them soon.

Please help me as soon as possible.

Thanks for any help,
Josh.


Thread has been solved!
Here is the quote/tutorial that helped me:
> **steeldriver said:**
> You would need to chroot into your installed system in order to update-grub from a live cd, I think:

[http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd)

Otherwise even if you mount your installed system and modify its /etc/default/grub, that change wont be written into the bootloader

Thanks a lot to all who helped, I hope this thread helps others in the future!

Thanks,
Josh

---

### Post by ibjsb4 on 2013-03-18
What happens if you hold down the "Down Arrow" key during boot?

You could also mount your HDD partition and edit /etc/default/grub using the live CD.

[http://ubuntuforums.org/showthread.php?t=1650021](http://ubuntuforums.org/showthread.php?t=1650021)

---

### Post by JoshuaMiller0 on 2013-03-19
> **ibjsb4 said:**
> What happens if you hold down the "Down Arrow" key during boot?

You could also mount your HDD partition and edit /etc/default/grub using the live CD.

[http://ubuntuforums.org/showthread.php?t=1650021](http://ubuntuforums.org/showthread.php?t=1650021)

Holding down up or down arrow or hitting it at about 3 presses per seconds did not work. Nor did holding down shift while doing it, or any combination of anything.

I used the live usb (cd) to "just boot" and I when I opened /etc/default/grub it had an unchanged version of the file with the delay set to the default of 10. Modifying this (with sudo update-grub) did not change anything.

Bump.

---

### Post by Moose on 2013-03-19
Delete the original file and then just edit the current file?

---

### Post by JoshuaMiller0 on 2013-03-19
> **Moose said:**
> Delete the original file and then just edit the current file?

I cannot find the original file (the one with the 1 second delay). When I type /etc/default/grub (or whatever) it opens a different grub config (with the default - 10 second delay.)

Please tell me how I can find and delete or modify the original file (1 delay)

---

### Post by ibjsb4 on 2013-03-19
And you did mount your HDD/partition in Nautilus and went to default/grub?

---

### Post by JoshuaMiller0 on 2013-03-19
> **ibjsb4 said:**
> And you did mount your HDD/partition in Nautilus and went to default/grub?

Umm, I have no idea. Originally I opened the grub file using terminal and modified it and did sudo update-grub.

I then did the same thing with nothing happening on xubuntu running off my usb. I don't know if I mounted anything, so I doubt it.

Bump.

---

### Post by steeldriver on 2013-03-19
You would need to chroot into your installed system in order to update-grub from a live cd, I think:

[http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd)

Otherwise even if you mount your installed system and modify its /etc/default/grub, that change wont be written into the bootloader

---

### Post by JoshuaMiller0 on 2013-03-19
> **JoshuaMiller0 said:**
> Umm, I have no idea. Originally I opened the grub file using terminal and modified it and did sudo update-grub.

I then did the same thing with nothing happening on xubuntu running off my usb. I don't know if I mounted anything, so I doubt it.

Bump.

That looks like exactly what I need. Thanks, I will try this and get back to you (mark as solved hopefully...) as soon as I get home.

Edit: Hopefully I can figure out where xubuntu is... (sda3...)

---

### Post by deadflowr on 2013-03-20
I wouldn't normally recommend this, but if you haven't tried [boot repair]("https://help.ubuntu.com/community/Boot-Repair") , you could try editing the grub.cfg file directly.
Run a live session and mount the 'buntu partition.
Then open up the file located in /boot/grub/grub.cfg.
Look for the line at the end of the first section (00_Header) set timeout = , and see what the time is set at.
It'll be the last one and not the first one ( the first will mention recordfail, ignore it, and look at the entry following 'else' .

Since this file is what is read at boot, and includes the enties listed in the /etc/default/grub as well as the entries in etc/gub.d/*, running update-grub would not be needed.
But as I stated before, normally, I advise against doing any editing of this file.

---

### Post by GameX2 on 2013-03-20
You could also use "Super GRUB2 Disk", it's really easy:
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

Download the ISO, you could burn to a CD(RW); there's also a USB download, but I haven't tried it.
You'll want to boot from the CD/USB, then choose the option "Detect any OS".  It'll detect and list the different boot options, like Linux and Windows.

Using this will allow you to boot from your installed Ubuntu, and you'll be able to revert the changes you've made to the GRUB files.  Try the software "GRUB-Customizer" if you want a GUI.

Super GRUB2 Disk is extremely useful, when GRUB get replaced by another bootloader.

---

### Post by JoshuaMiller0 on 2013-03-20
> **steeldriver said:**
> You would need to chroot into your installed system in order to update-grub from a live cd, I think:

[http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd)

Otherwise even if you mount your installed system and modify its /etc/default/grub, that change wont be written into the bootloader

I gave this a shot and you wouldn't believe the bad luck I was having.

[LIST=1]
[*]I could not find my usb with xubuntu boot-loader on it
[*]I found a usb with Ubuntu boot-loader on it so I plugged it into the computer and got a xubuntu boot-loader installer running
[*]As I waited patiently I found that I was using an ancient USB 2.0 device in a USB 3.0 port: can you get any slower?!
[*]It finally finished and I booted my computer with it.
[*]I hit ctrl + alt + t and the explorer process broke
[*]My faulty USB shifted slightly and it disconnected, stopping the process from restarting or anything from working.
[*]I tried to shut down the computer safely and it ended up in an endless loop.
[*]I was forced to hold the power button down until it went off.
[*]The bootloader was then broken.
[/LIST]

I guess I better give this another shot...
But USB is such a slow connection...

---

### Post by GameX2 on 2013-03-21
With a Super GRUB 2 Disk, you could boot into Ubuntu even when GRUB is wiped - then you'll be able to use Boot-Repair to fix the bootloader.  Just a suggestion I find really easy.
Good luck.

---

### Post by JoshuaMiller0 on 2013-03-21
> **GameX2 said:**
> You could also use "Super GRUB2 Disk", it's really easy:
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

Download the ISO, you could burn to a CD(RW); there's also a USB download, but I haven't tried it.
You'll want to boot from the CD/USB, then choose the option "Detect any OS".  It'll detect and list the different boot options, like Linux and Windows.

Using this will allow you to boot from your installed Ubuntu, and you'll be able to revert the changes you've made to the GRUB files.  Try the software "GRUB-Customizer" if you want a GUI.

Super GRUB2 Disk is extremely useful, when GRUB get replaced by another bootloader.

Does this mean I can use the universal usb startup disk installer to install "Super GRUB2 Disk" and then boot xubuntu and simply modify the grub file manually?


And once I do one of these things (which ever I chose) and I modify the grub file, what is the safe delay I can set it to? Grub delay of 0 is obviously near instant, Grub delay of 1 seems like it is nearly instant and for some reason in the time you cannot modify anything. Is Grub delay of 3 safe? Would holding down the up arrow, or spamming it, or just a fast reflex press be fast enough before the computer boots automatically.

---

### Post by GameX2 on 2013-03-21
> **JoshuaMiller0 said:**
> Does this mean I can use the universal usb startup disk installer to install "Super GRUB2 Disk" and then boot xubuntu and simply modify the grub file manually?


And once I do one of these things (which ever I chose) and I modify the grub file, what is the safe delay I can set it to? Grub delay of 0 is obviously near instant, Grub delay of 1 seems like it is nearly instant and for some reason in the time you cannot modify anything. Is Grub delay of 3 safe? Would holding down the up arrow, or spamming it, or just a fast reflex press be fast enough before the computer boots automatically.

I don't know about the Universal USB Installer, sorry.  I would recommend you to simply burn the ISO file on a CD-RW (There's also a Floppy image availible), using a program such as InfraRecord or IMGBurn for Windows, or Brasero for Linux.  There's also a way to install it on a USB drive (Assuming your PC support booting from USB), but I haven't tried it.

As for the delay, I guess 3 seconds is OK, but.. try it? ;)
Honnestly, with the Super GRUB2 Disk, when GRUB get wiped or innacessible, there's absolutely no reason to panic anymore. ;)  I find it extremely useful (Even for a 1.44 MB ISO!).

When you've booted in Ubuntu, install BootRepaire, then choose the first option (Quick fix, something similar).  Tell us how it goes!

```
sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

Good luck

---

### Post by JoshuaMiller0 on 2013-03-23
> **steeldriver said:**
> You would need to chroot into your installed system in order to update-grub from a live cd, I think:

[http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](http://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd)

Otherwise even if you mount your installed system and modify its /etc/default/grub, that change wont be written into the bootloader

I finally got a working livecd and followed this tutorial. It didn't entirely work, but when I restarted the computer it has reset the grub default to 0 and the grub delay was still 1. This would have been a problem if I didn't have xubuntu first in the list. When I loaded xubuntu I just opened and edited the grub file before updating it and now my computer works just fine. Thanks a lot to everyone who helped, I greatly appreciate being able to use xubuntu!

-Josh.

---

