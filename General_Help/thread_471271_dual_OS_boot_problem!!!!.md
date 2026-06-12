---
title: "dual OS boot problem!!!!"
date: 2007-06-11
forum: General Help
---

### Post by supred on 2007-06-11
I have just got my ThinkPad X60 today. And the first thing I did was to install Ubuntu on it. the installation went fine. It's just when it comes to the boot menu after I rebooted it, the windows won't start!!! Not only that, the "ThinkVantage" button (it's kinda a short cut to the "hidden hard drive" where the recovery files are at) also stopped working. After I chose to boot from windows, it will start and the hard drive light will flash a little bit, then that's it! It won't go any further.
Someone PLEASE help me!!




Bruce

---

### Post by veerakumar on 2007-06-11
fdisk -l /dev/harddrive
You might have formatted the whole hdd

---

### Post by carcioni on 2007-06-11
I think I would agree. Check the /boot/grub/menu.lst file and see if the install actually made a Windows boot option. If it didn't you may have taken the default during the install which would have been to use the whole drive for Ubuntu. (Been there, done that, got the bruises on my head from hitting it on the wall) ;)

Cheers
C

---

### Post by supred on 2007-06-11
Thank you all for such fast response. 

But I am pretty sure I didn't wipe out the entire hard drive, the menu.lst is as follows: 

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

hope this can provide some clue to my problem. 

Really appreciate your help!!!!!

---

### Post by ^Pho[T]on on 2007-06-11
what error message are you getting when u try to start windows?

---

### Post by supred on 2007-06-11
Just to provide some more detailed info. 
I splited  the hard drive in 5G-30G-20G, the 5G  is the so-called "predesk" area, supposingly, can't be modified by any OS. Then the 30G for Vista, originally, it's one partition of 50G, I resized it to 30. Then the 20G(extended partition) , divided into two ways 10G in NTFS, and the other 10G=4G+3G+4G in ext3.  Ubuntu was installed in the last 10G. 

You may find this way of partitioning wired, the truth is I don't know much about all this, my previous experiences were mainly "mouse clicking". Hopefully my knowledge will grow! ^^


THANKS AGAIN FOR STOPPING BY AND REALLY APPRECIATE!!

---

### Post by ^Pho[T]on on 2007-06-11
when u try to boot an OS and ther is no screen output, it culd be because of the incorrect resolution/refresh rate of the screen. if the screen is  completely blank, u can start by searching that on google. 

another remote problem is that i see you are using a sata harddrive. with windows xp that gave me a problem, but i doubt vista wuld stiill have that problem. if it is the problem however, u  wuld need to get the drivers/sata controllers for the motherboard u are using from the oem (original equipment manufacturer) of the motherboard.

---

### Post by supred on 2007-06-11
the thing is, the Windows won't start and it doesn't provide me any error message either, it just sit there, doing nothing!!!!

---

### Post by merlinus on 2007-06-11
You may have trashed your mbr (windows master boot record).

Try booting from your windows cd, and select Restore.

-merlin

---

### Post by supred on 2007-06-11
If I have one, I would definitely try that.  But the fact is, my X60 doesn't even have a cd-drive. That's why I am trying to get to the "predesk" area, it has all i need. But sadly, it won't start!!  -_-!

---

### Post by ^Pho[T]on on 2007-06-11
a similar thing happened to me once where the screen would go completely blank with no error message (not even blinking cursor). it turns out ubuntu was trying to boot in a resolution not supported by my moniter. i solved it by putting vga=ask in my menu.lst like this

title           BlakHat_ Kernel 2.6.20.3
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20.3-ubuntu1 root=UUID=15b2a017-c2a8-48bc-af55-e93d8442d1f3 vga=ask ro

i believe vga=[resolution code] is for linux

as for windows, this looks like sumthing new. perhaps sumthing went wrong installing grub?
to reinstall u can check this link out  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by supred on 2007-06-11
Hi Photon, 
Let me clarify myself a little more. I have no problem starting up Ubuntu, Vista is the problem here(it will have a black screen and a mouse that i can move OR the progress bar(the one shown when windows starts) going on forever with nothing else going on, in both cases, no hard drive activity at all).  

At the last step before the installation of Ubuntu started, it asked me if i want to install "loader?" to "hd(0)?" (not really sure what that is, but i did click "yes" without thinking much),  could that be the problem???!!!

---

