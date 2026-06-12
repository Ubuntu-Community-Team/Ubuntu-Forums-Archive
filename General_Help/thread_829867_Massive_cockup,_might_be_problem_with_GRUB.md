---
title: "Massive cockup, might be problem with GRUB"
date: 2008-06-15
forum: General Help
---

### Post by thatsnicethat on 2008-06-15
Hello All

I have been searching for a solution but can't repair my system at the moment. I'm very new to Ubuntu, using Hardy on a Dell Inspiron 6400.

First of all, how I got to this stage:
I was trying to prepare a USB device to boot to Debian, I got a very straight forward Howto from here:

[http://www.debian-administration.org/articles/446]("http://www.debian-administration.org/articles/446")

then I did something extremely stupid, I copied from the page this line
[COLOR="Red"]
zcat ~/boot.img.gz > /dev/sda[/COLOR]

when I should have substituted sda for sdb, which is the usb device. So I can only now boot to the Debian installation, and it won't show Ubuntu at all at startup. I have tried to install GRUB, but I haven't found a howto that I can fully follow without any problems. This is a bit embarrassing but there you go, as a newbie, you do cock it up sometimes...

Anyone out there with an idea would be extremely welcome.

Many Thanks

---

### Post by forestpixie on 2008-06-15
Have you been up the use livecd route or supergrub route yet?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/)

Personally I think it is useful to have a copy of the supergrub disc to boot with.

---

### Post by philinux on 2008-06-15
I'd get the super grub disk and see if that can sort you out.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by thatsnicethat on 2008-06-15
Thanks for the idea, I'm going to try Supergrub, and keep you posted.

Thnaks

---

### Post by thatsnicethat on 2008-06-15
No joy :(

First with SuperGrub, I go to:
[COLOR="Blue"]>Advanced >Restore GRUB in HardDisk[/COLOR]

then I try [COLOR="Blue"]>Automatically Install[/COLOR], but it doesn't work. I try again with manual install to [COLOR="Blue"]sda[/COLOR], then [COLOR="Blue"]hd0[/COLOR],0, but I get [COLOR="Blue"]error 18: Selected cylinder exceeds max supported by BIOS[/COLOR].

I also tried from the livecd to do [COLOR="Blue"]find /boot/grub/stage1[/COLOR] in grub>, but I get [COLOR="Blue"]error 15 File Not Found[/COLOR]. I'm fairly lost here I'm afraid.

Thanks for the replies.

---

### Post by forestpixie on 2008-06-16
Sorry I can't be of more help but a couple of things -

have you set up bios correctly

have you tried running through the how to again

What can you boot the buntu or the debian? Which is where - is buntu on the hdd - perhaps you could say what it is you're trying to end up with.

Error 15 is
> 15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)


Error 18

> Now, technology has also passed the 33.8 and 137 GB hard drive limits too, so bear these two in mind as well, when diagnosing error 18 faults.
The GRUB error 18 message could nowadays be referring to the 137 GB BIOS hard disk size limit. This occurs when a machine was made for an 80 or 120 GB hard disk, and someone fits a 137 GB+ hard disk in thier machine without checking if the BIOS supports it. 
Windows XP will work okay because it is usually installed in the first part of the hard disk, so the average user is blissfully unaware of the situation until they maybe install Linux on the second half of their hard disk, past the BIOS limit and get GRUB error 18.

> Making a separate /boot partition would probably still be the best answer even with a relatively modern computer if you think you might have the 137 GB hard drive limit.
In the following thread, Ioza had a system that wouldn't boot after and upgrade from Feisty to Gutsy. Here is the link, [http://ubuntuforums.org/showthread.php?t=582855](http://ubuntuforums.org/showthread.php?t=582855)
Apparently, an operating system that is partly inside the hard drive limit may boot for some time as long as the kernel happens to be located within the part of the disk that the BIOS can 'see'.
After an update, if a newer kernel  happens to be placed somewhere outside the limit, the operating system might suddenly become unable to boot (at least by the new kernel), and most users would find it difficult to understand the reason why not. 
Here is a great explanation of how that might happen, also already linked to in the above link, [http://www.nabble.com/Grub-tf4291271.html#a12218543](http://www.nabble.com/Grub-tf4291271.html#a12218543)
That might also explain the real reason why resizing the Linux partition to a smaller size has helped some people cure GRUB error 18.  A separate /boot partition could have fixed that and allowed them to make better use of their hard disk.
Here's how to make a separate /boot partition: How to make a separate /boot partition.
Actually, if it's a brand new installation and still empty, re-installing would probably be a lot easier, and you can create the new boot partition at the same time as you re-install.

---

### Post by thatsnicethat on 2008-06-17
Thanks for the helpful answers, maybe I wasn't that much clear about what I had done, or what I wanted to do. In the end, I haven't been able to solve it, so I've done a fresh install of Ubuntu. Fortunately I had a backup of the most important files I had, so not much has been lost.

Thank you again for the replies.

---

