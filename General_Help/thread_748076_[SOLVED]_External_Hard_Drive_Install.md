---
title: "[SOLVED] External Hard Drive Install"
date: 2008-04-07
forum: General Help
---

### Post by Vince4Amy on 2008-04-07
What I'm aiming to do here is install Ubuntu onto my 120GB Maxtor External hard disk drive. This should be simple to install to the drive since my BIOS allows me to do this. 

What I want to do is the following:

[LIST]
[*]Install Ubuntu to the External Hard Disk
[*]Do NOT let grub modify the boot sector, I do not want it overwriting the Vista one. The reason for this is that the External drive will not be connected at all times, so this will confuse GRUB if the drive isn't connected. I will boot the external drive from the BIOS boot menu.[/LIST]How would I overcome the second bullet point, I really do not want the Vista boot sector to be overwritten with GRUB due to the circumstances, as I said I can boot the drive from the BIOS, so I do not need the GRUB menu, if the External drive is not connected the BIOS will not attempt to boot it first so that Vista will boot as normal anyway.

---

### Post by gsmanners on 2008-04-07
I think you can control how grub is handled if you use the "alternate" CD.

---

### Post by cdenley on 2008-04-07
To be safe, I would disconnect or disable the internal drive when you install ubuntu. You can always configure the external drive for dual-boot manually, if necessary. I think setting the external drive to the highest boot priority would work, but I'm not sure.

---

### Post by fsmithred on 2008-04-07
Take a look at this. I think you'll need to get usb modules into your initrd to get it to boot from the external drive. 

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

There might be newer posts, too. I think this question came up very recently.

---

### Post by cdenley on 2008-04-07
I didn't have a problem installing gutsy on usb drives.

---

### Post by rugbylg6 on 2008-04-07
[http://ubuntuforums.org/showthread.php?p=4673273#post4673273](http://ubuntuforums.org/showthread.php?p=4673273#post4673273) 
also a really helpful post. Maybe a little different than what your looking for but it might help.

---

### Post by Vince4Amy on 2008-04-08
I unplugged the SATA cables on the Internal drives in the end, and then set the boot priorities after Ubuntu was installed and everything was fine. Thanks for the help anyway.

---

### Post by oligray on 2008-04-08
[http://ww.ubuntuforums.org/showthread.php?t=747263](http://ww.ubuntuforums.org/showthread.php?t=747263) this is my guide

and i know your solved now but i wouldnt have thought unplugging the internal would work 100% because all the stuff i input into the terminal in my guide is about making ubuntu boot off external..

also its easier than unplugging the drive.. but unplugging the drive is safer because if you do something wrong in the install you end up with GRUB errors and theyre jsut annoying.. lol

---

### Post by Vince4Amy on 2008-04-08
Yes this is exactly why I unplugged the drives, I can't be bothered with GRUB errors.

---

