---
title: "Help with windows and ubuntu [TOTAL NOOB]"
date: 2019-03-14
forum: General Help
---

### Post by ogdale on 2019-03-14
I recently installed ubuntu but during installation some issues where present which resulted in me accidentally removing my windows OS and only having ubuntu. 

At the start I had only the demo version of ubuntu and was unable to download or install anything. Now I have the full version installed and its working fine. 

I'm having issues however trying to make a bootable version of windows 10 on either USB or DVD. 

From WoeUSB I consistently get to around 89% of creating the bootable USB but then it force stops with this message: 

```
Installation failed!
Exit code: 256
Log:
/usr/bin/woeusb: line 433: local: warning: only_for_gui_ref: circular name reference
/usr/bin/woeusb: line 433: warning: only_for_gui_ref: circular name reference
/usr/bin/woeusb: line 508: warning: only_for_gui_ref: circular name reference
WoeUSB v@@WOEUSB_VERSION@@
==============================
Wiping all existing partition table and filesystem signatures in /dev/sdc...
/dev/sdc: 2 bytes were erased at offset 0x000001fe (dos): 55 aa
/dev/sdc: calling ioctl to re-read partition table: Success
Ensure that /dev/sdc is really wiped...
Creating new partition table on /dev/sdc...
Creating target partition...
Making system realize that partition table has changed...
Wait 3 seconds for block device nodes to populate...
mkfs.fat: warning - lowercase labels might not work properly with DOS or Windows
mkfs.fat 4.1 (2017-01-24)
Mounting source filesystem...
Mounting target filesystem...
Applying workaround to prevent 64-bit systems with big primary memory from being unresponsive during copying files.
Copying files from source media...
The command "dd if="${source_file}" bs="${DD_BLOCK_SIZE}" skip="${i}" seek="${i}" of="${dest_file}" count=1 2> /dev/null" failed with exit status "1", program is prematurely aborted
Resetting workaround to prevent 64-bit systems with big primary memory from being unresponsive during copying files.
/usr/bin/woeusb: line 1608: local: only_for_gui: readonly variable
Unmounting and removing '/media/woeusb_source_1552606432_11133'...
Unmounting and removing '/media/woeusb_target_1552606432_11133'...
You may now safely detach the target device
```

Through some means, through different methods, I am able to write the ISO to the USB for booting. However upon restarting the machine, My UEFI or BIOS has completely changed over to GRUB from what I believe and I have no idea how to get this back. 

When trying to use Brasero or ubuntu's own file writing program for disc, it doesn't recognise my discs as 8.5GB but instead as 3.5GB. It still allows the burning process, but this also unexpectly ends at around 30% and the dvd ejects itself. 

I've been working on this for around 3 days now and wasted 3 discs. 

All I really want is to get windows 10 installed on my machine again. 

I have no care for the files which are lost as I recently got this machine and there isn't anything of value on it. 

For people who may ask, I've done this before on older machines with no problems. I dont know much about linux but always wanted it to be dual booted so I could boot up and start learning how to use linux. Now I feel I'm stuck in this mess with only having one OS being linux and I've lost windows to my own mistakes. 

Does anyone have any noob advice as I've followed online guides ( a number of them ) and I'm still not able to create a bootable anything to try install windows 10 again back on the machine. 

Any help is greatly and truely appreciated!

---

### Post by dragonfly41 on 2019-03-15
> 
When trying to use Brasero or ubuntu's own file writing program for disc, it doesn't recognise my discs as 8.5GB but instead as 3.5GB. It still allows the burning process, but this also unexpectly ends at around 30% and the dvd ejects itself. 

I've been working on this for around 3 days now and wasted 3 discs. 


I will chip in since you are getting frustrated.  Understand that if you have formatted a USB with Fat32 then there is a 4 GB limit.  Formatting in NTFS removes restrictions.

[https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706](https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706)

Although I have dual boot Windows10 + Ubuntu 16.04 on dell my memory about the co-habitation rules is fuzzy.  I defer to others.
I know that Windows 10 is a bit like a cuckoo in the nest and strives to chuck out neighbours such as Ubuntu. Windows demands to be the first in pecking order.  Some form of bot to automate dual boot should be created for new users.

---

### Post by nicholasarussell on 2019-03-15
I installed Brasero (dvd burning software) from software centre

I can burn windows iso's to DVD and now I am happy with ubuntu and photon lol

its seems to be the only fool proof way I found for burning them.

GL and HF :)

---

### Post by jdeca57 on 2019-03-15
> **nicholasarussell said:**
> I installed Brasero (dvd burning software) from software centre

I can burn windows iso's to DVD and now I am happy with ubuntu and photon lol


Slightly off-topic the burning of a DVD isn't everything because Windows has an activation key and that is what you need if you were ever contemplating to use the license you paid for.

---

### Post by ogdale on 2019-03-15
> **dragonfly41 said:**
> I will chip in since you are getting frustrated.  Understand that if you have formatted a USB with Fat32 then there is a 4 GB limit.  Formatting in NTFS removes restrictions.

[https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706](https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706)

Although I have dual boot Windows10 + Ubuntu 16.04 on dell my memory about the co-habitation rules is fuzzy.  I defer to others.
I know that Windows 10 is a bit like a cuckoo in the nest and strives to chuck out neighbours such as Ubuntu. Windows demands to be the first in pecking order.  Some form of bot to automate dual boot should be created for new users.

Yes I am aware of the fat32 restrictions and I've tried formatting my 32GB usb to NTFS. I've also unmounted this but near the end of WoeUSB creating the bootable USB, it gives a 256 error and this happens each time. 

Brasero also spits the dvd out of my drive when it reaches around 25-30%. 

No real idea what I should be doing now to solve this.

---

### Post by yancek on 2019-03-15
I've never used Woeusb but have seen a lot of posts with people having problems with it.  You can put the windows install iso on a usb or on an ntfs partition on your hard drive and boot it from the Grub on your currently installed system.  The steps (and there are a number of them) required are explained in detail at the link below.  You can ignore the part about installing Grub to a usb and you can either use a usb or a partition on your hard drive.  If you do this, you would need to put an entry in the /boot/grub/grub.cfg file on your Ubuntu system as explained rather than on the usb.  Do NOT update grub after doing this.  If you can read and follow detailed instructions, it works as this is what I used.  I would suggest you read through the page before beginning.  One thing I had a problem with was using Disk Image Mounter on Ubuntu as the file was too large.  If that is the case, you can loop mount the iso before copying it.


[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

