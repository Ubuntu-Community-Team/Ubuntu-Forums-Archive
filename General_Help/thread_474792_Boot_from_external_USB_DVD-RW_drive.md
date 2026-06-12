---
title: "Boot from external USB DVD-RW drive?"
date: 2007-06-15
forum: General Help
---

### Post by nightfire117 on 2007-06-15
Hello.... This isn't necessarily Ubuntu-related but I suppose that some Linux solutions (i.e. using GRUB or LiLO, perhaps?) might work for my problem.

I have a Gateway 450SX4 notebook, Pentium 4-M, 512 RAM, internal CD-ROM (**not** DVD-ROM) and no USB boot support for the BIOS. I want to boot from an external USB DVD drive (a Sony DRX-510UL) so I can install something that way. But I haven't been able to, after hours, find a solution.  I'm willing to install whatever in order to get it working. And in the end I'm going to use the DVD to reformat the hard drive anyways. So preferably a boot-CD method would be good. Thanks in advance, you guys have always answered my questions. XD

~Nightfire

---

### Post by cookies on 2007-06-15
Your BIOS should have the option to select External/Internal CD/DVD Drive.

When the computer first boots, look for an F button to press, like F12 or F7 or something that says Setup or, for newer BIOSs, MultiBoot Menu.

Then you can set to boot from the External Device.

---

### Post by nightfire117 on 2007-06-15
Thanks for the reply. The only such option is "Boot from Removable Device," nothing about USB. I have other computers that boot from USB and their options say things like "USB-FDD," "USB-HDD," "USB-ZIP," etc.

Sorry I didn't specify it earlier. Thank you for your reply. ^^

~Nightfire

---

### Post by logos34 on 2007-06-15
Does it have a floppy or do you have a usb floppy?  if so you could use smart boot manager

---

### Post by nightfire117 on 2007-06-15
> **logos34 said:**
> Does it have a floppy or do you have a usb floppy?  if so you could use smart boot manager

I have a USB floppy drive, no internal floppy. (But the BIOS doesn't have a boot from USB-FDD option.) Smart Boot Manager? I haven't used it before, but it looks interesting. Thanks for that. XD I'll give it a shot, then. Hopefully my results are good, heh. (And I'm open to more suggestions.)

~Nightfire

**[EDIT]:** Noting that I cannot install it to my NTFS partition and I am not assuming it'll boot from the USB FDD. Lucky for me I found a boot CD that has it - that might work. I'll give it a shot now.

~Nightfire

**[EDIT]:** Tried that tool and many other boot tools, and none of them recognize that there is a USB CDRW/DVDRW drive attached to the PC. I even installed a boot loader on there, but that didn't work either. Umm, the primary drive is in a 12 GB NTFS partition and 6 GB FAT32 partition, not that that has any relevance. There's an internal CDRW that's recognized, but the external CDRW/DVDRW is not recognized. o.o This has stumped me.

~Nightfire

---

### Post by nightfire117 on 2007-06-15
Hate to bump this, but, anyone?

~Nightfire

---

### Post by bluknight on 2007-06-15
Yep I posted an install to ext USB HD somewhere in this forum. Works for Edgy (CE2.2) but Feisty(CE3.2) require some wrangling of kernel/initramfs to boot:
[http://ubuntuforums.org/showthread.php?t=450246&page=2](http://ubuntuforums.org/showthread.php?t=450246&page=2)

---

### Post by nightfire117 on 2007-06-16
Thanks for the response, but as far as I can tell that has nothing to do with my problem, which is wanting to boot from a USB CD-ROM drive, but my BIOS doesn't support it. >.<

~Nightfire

---

### Post by nightfire117 on 2007-06-17
I take it there's no real answer to this, at least, no "one" answer. I guess one can't have everything/anything.

~Nightfire

---

### Post by adblock on 2007-06-17
I had today almost the same problem , like you. Ubuntu install CD does not have USB DVD support for my  Thinkpad X32. So what I did:
1. Install VMware on my windows XP. 2. In windows XP I has created ISO image of Ubuntu install disk.
3. Create in VMware virtual machine with simulation of CD using  that ISO image and physical HD as HD inside VM, 
Here I has made some trick. Outside VM , I temporarely disabled all active partitions on HD by partition manager. 
4. Start Virtual Mashine with boot from the ISO image drive. 
5. Following standard procedure ,install Ubuntu inside virtual mashine to HD drive
6. After install was finished , I have restored active partition.
That is all!

---

### Post by nightfire117 on 2007-06-17
Thanks for the info, I will look up how to activate/deactivate a partition. I'll try that soon, thanks. XD

Haha, when I saw "adblock has just replied to a thread you have subscribed to..." in my inbox I thought I was going to be punished for spamming or something. Hehe. Again thanks for the post.

~Nightfire

---

### Post by adblock on 2007-06-18
"Deactivate" means make partition not bootable. You can do it  by Fdisk or other disk partitioning program. You need deactivate partition, because by default VMware looks through all connected drives and try boot not from virtual CD but from virtual HD. IF HD will have active partitions , VMware will boot from the HD.

---

### Post by adblock on 2007-06-18
!!!!!Be carefull!!!!! , after you deactivate partition. Do not switch off your PC, or you will not be able to boot without active partition. After VMware boots up correctly, just immidiately restore active partition flag back.

---

### Post by nightfire117 on 2007-06-18
Thanks for the info! I'll see if I can do it in Acronis Disk Director, which is what I use.

~Nightfire

---

### Post by longlegs on 2007-06-18
Hi ,
The boot process starts in bios, so if bios does not support USB, you cannot boot from USB. It is a catch 22 situation in that your system cannot 'see' the USB until the system boots, and it cannot boot from USB until it can see the USB.
I have searched for companies/people/ etc that might have a bios flash or replacement bios so I could boot from USB but no luck so far.
Have a good day!
longlegs

---

### Post by nightfire117 on 2007-06-18
Oh.... That's quite unfortunate, hehe. But, thanks for the information, you have saved me much time and trouble.

~Nightfire

---

### Post by adblock on 2007-06-19
To Nightfire. I just found how to control boot process in VM ware. If press ESC during the initial boot of virtual mashine, You will  enter bios settings of virtual mashine(that bios has nothing to do with real bios of your PC) and can set option  to boot from virtual CD.
After this no need to play with boot partitions on your real HD.   That is much better for you, I think.

---

### Post by nightfire117 on 2007-06-19
Thanks for the info. I had suspected the ESC would work, it did for me but I forgot to mention I did that. XD Umm, as for the boot it cannot be done natively and thus I would avoid VMware. But thanks for the tips, because if I need them in the future (and probably will) they'll prove quite useful. 

~Nightfire

---

