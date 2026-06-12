---
title: "Grub loading errors"
date: 2008-07-06
forum: General Help
---

### Post by sunburstgl on 2008-07-06
Im running ubuntu Hardy Heron. When I try to boot my computer, I get to "Grub Loading stage 1.5" and then I get an error. This error seems to change from time to time. so far I have gotten errors 2, 8, 12, 15 and 24.

I have also gotten a "grub loading..." but it never loads and it just sits there and blinks.

I have also gotten a GRUB bash prompt when trying to boot too.

Is there any way I can fix this or should I just install ubuntu again.

Here is a list of what the GRUB errors are for stage 1.5
2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 

8 : Kernel must be loaded before booting
    This error is returned if GRUB is told to execute the boot sequence without having a kernel to start. 

12 : Invalid device requested
    This error is returned if a device string is recognizable but does not fall under the other device errors. 

15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

24 : Attempt to access block outside partition
    This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool). 

Thank you in advance for those of you who answer.

---

### Post by VMC on 2008-07-06
Why not just reinstall Grub. By the way you didn't mention if you also have Windows installed. From a Livecd type the following:

```
sudo grub
find /boot/grub/stage1
```
Note the output. In my case it was (hd0,2).
```
root (
```
press <tab> it will complete the first part hd0,
type: 2) (Or whatever is applicable for you)
```
setup (hd0)
```
press <tab>
Finally type: quit

---

### Post by sunburstgl on 2008-07-07
Thanks, and no I do not have windows installed on another partition. THank you very much. I'll give it a try

---

### Post by sunburstgl on 2008-07-08
It didn't work. I still get errors.

---

### Post by sunburstgl on 2008-07-08
and now even when I try to do it over again, when I type find /boot/grub/stage1 I get "Error 15: File not found"

---

### Post by 164747 on 2008-07-09
I having the same problems as you: a totally random and incorrect behavior from Grub.
Though I can sometimes succesfully boot if I try it over and over again. 

If I boot from a live-cd and re-install grub, the NEXT boot is succesfull, but the 
one after that may be corrupted. When I did a re-install it worked fine untill the
first software update. Hence the problem can be connected with some upgrade after 
the Hardy realease.  

If I would make some suspicious points:
* HARD-DRIVE -- SATA/IDE
* BIOS       -- What should be the precise SATA settings.
* LVM        -- I have / on a own partition the rest on a logical vol group.
* ENCRYPTION -- I have a fully encrypted system.
* UPDATE     -- see above

do you have the same feeling?

I have also googled around and tried and added the following two kernel arguments in menu.lst:
all_generic_ide
iommi=soft

But I did not have any luck. This is very frustrating. Have a feeling that this 
problem is Hardy-specific. Maybee changing back to Feisty is the best thing to do?

---

### Post by kd5ful on 2008-07-09
At the moment, I am considering re- partitioning back to 7.10 (or whatever) from Hardy simply due to this error.
I am highly upset.
My only question would be at this point, IF I were to do so, would I be able to mount the original hardy drive under an older version in order to recover the data thereon?

---

### Post by 164747 on 2008-07-11
I can give one comment. Found a place (cannot find the link again) that said that (as I understood):

 these random **** could occur when the hard drive cabling was wrong (wrong order/not tightened ...). It worked if some Bus was reset and otherwise no (hence the randomness). Older kernels did not care about this error, but the new kernel chooses to stop working without a proper error-message.

Therefore I opened my box, check the order against my motherboard manufacturers guide (yes I found the energy), it was OK. But I tightened the SATA-cables. I have only booted once.It went perfect. Before when I could boot I had to wait ~ 10s for the Grub menu to show, now it showed up immediately. I am ~50% sure that this was the error in my case. So maybe it is a good idea to open your box. 

I will get back if this really was the problem in few days.

Good luck!

---

### Post by 164747 on 2008-07-11
The easiest way to backup the data before a re-install is to boot your computer with a live-cd. Then connect an external usb-harddrive och copy the content on the drive to another computer with scp.

If this is not possible for you, then you have to install your new system without touching the partion(s) currently holding your data. Hence you have to choose "manual" in the partion-guide during re-install.

---

### Post by 164747 on 2008-07-17
I did get the random errors (mentioned above) even after I tightened the SATA cables to
my harddrive. However I did one desperate move. I changed the cable connections
according to

OLD
SATA 1, Harddrive1  (boot)
SATA 2, Harddrive2
SATA 3, empty
SATA 4, dvd-rom
SATA 5,6 empty

NEW
SATA 1, Harddrive1  (boot)
SATA 2, Harddrive2
SATA 3, dvd-rom
SATA 4,5,6 empty

After this I have had no errors. If they remain they are at least much less common.
The only instruction on how to connect the hard-drives that I found in my mother-
board manual, was that the boot drive was supposed to be connected to SATA1. This
is fulfilled by both OLD and NEW configuration.

---

