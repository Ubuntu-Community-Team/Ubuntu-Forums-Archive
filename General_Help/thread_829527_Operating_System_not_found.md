---
title: "Operating System not found"
date: 2008-06-14
forum: General Help
---

### Post by onetb on 2008-06-14
This is not directly related to Ubuntu, but it is the only operating system I use, and most of the search results that came up in Google pertained to Windows, so...

About a month and a half ago, I came home to my old desktop, only recently dusted off and imaged with Ubuntu, to find it had shut itself off.  I switched it on the find "Operating system not found".  Tried restarting it a few times but this kept coming up.  Quite sad.  So about two weeks later, I borrowed an old HD from inventory at work (I work in server operations at a state university) and installed 7.10 fresh on the HD, only to find on it's first boot is read "Operating system not found".  I switched the hd's back out and left it alone until yesterday.  I was going to check the bios for something but was surprised to find it was now booting properly.  I have been messing around with it just a little since.  Just now, when trying to turn it on, I got the same error again.  Ctrl+Alt+Del fixed it immediately, but I am quite confused.

Most people are saying that this error is caused by a few things.  (1) an error in the MBR, but this seems unlikely as a restart immediately fixed it.  Plus, it gets through the GRUB loader without any other errors when it does actually load.  (2) There is a physical issue with the HD, but both HD's had the error.  It is quite possible the borrowed HD was bad, but why would this only happen sometimes with the HD I'm currently using. (3) The BIOS is not seeing the HD, again, this may or may not be the issue, but I could not say.

Is there anything people might suggest to help me narrow this down.  Or is any one out there so awesome as to just tell me what the deal is?

---

### Post by heatpumpcontrol on 2008-06-14
try the cabling....

---

### Post by onetb on 2008-06-21
Would you mind elaborating.  Not to second guess, I just like to have a good understanding of someone's suggestions before I embark.

---

### Post by cariboo on 2008-06-22
I guess what the previuos poster was saying is to check the power and data cables to the hard drive. The only thing I can thinK of that could cause intermittent problems like this is check the jumpers to see if you've got it jumpered for Cable Select or as a Master. I've never had any luck with cable select.

Jim

---

### Post by lisati on 2008-06-22
The only time I've had "Operating System not found" is when I've cleaned out a HD and forgotten to install an OS. 

I'm wondering if booting from a Live CD and doing ```
sudo fdisk -l
``` or something similar would shed any light on the matter.

---

### Post by onetb on 2008-06-22
cariboo907: I know the HD is set as master, but that doesn't mean the serial cable isn't corrupted.  I got this computer about 6-7 years ago, and it has seen some travel and storage.  I don't know how i might check this other than buying new cords, and this issue is not that inconvenient.  

lisati:  I don't believe this would be the issue.  I have only 1 HD in this comp, and I destroyed all the old data on it with qtparted before my very recent install of H.Heron (about 1 week ago).

Thanks

---

### Post by josir on 2008-06-22
Hi onetb, some old bios do not recognize the only one HD as /dev/hda. It starts with hdb or sda, or some weird letters. So the suggestion to try 

fdisk -l 

is worthy. Tell us what was the result. I also agree that the problem should be on grub.

Good Luck,
Josir.

---

### Post by WeeWoh on 2008-06-22
Check your GRUB boot menu. Is it pointed to the Ubuntu hard disk and partition or is it pointing somewhere else? (To read to menu type in terminal```
gksudo gedit /boot/grub/menu.lst
```)

Sorry if you already know that but some people dont.

You could also try reinstalling Ubuntu.

---

### Post by pietjanjaap on 2008-06-22
Try a new battery in your bios bios?
Maybe your battery is sometimes not giving enough juice.

---

### Post by onetb on 2008-06-22
Wow, lots of great responses.  Currently running live cd, so I will list the results of fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b637f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974        1155     1461915   82  Linux swap / Solaris
/dev/sda3            1156        9729    68870655   83  Linux

```

I have already reinstalled Ubuntu and the problem remained.  It also presented with several HDs, so I don't think it is anything to do with that.  It seems the HD name may have been it, as my bootable partition is "sda1".

As far as the battery goes, do you think that would explain why almost every time I boot it, I get the "Operating System Not Found" error, and then a restart brings to OS up?

Will post GRUB boot menu shortly.

---

### Post by onetb on 2008-06-22
Alright, here are the uncommented portions of the GRUB boot menu:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=105ce3a9-a8ea-41b1-9a34-38fe9f242ca4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=105ce3a9-a8ea-41b1-9a34-38fe9f242ca4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=105ce3a9-a8ea-41b1-9a34-38fe9f242ca4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=105ce3a9-a8ea-41b1-9a34-38fe9f242ca4 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=105ce3a9-a8ea-41b1-9a34-38fe9f242ca4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=105ce3a9-a8ea-41b1-9a34-38fe9f242ca4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

From this, correct me if I am wrong, But I see two things.  (1) I need to uninstall the older kernel versions on my computer and (2) they all seem to be pointing at "hd0" instead of "sd0".

Suggestions/Answers?

---

### Post by josir on 2008-06-22
Hi onetb, 

hd0 is the internal name convention used by grub. 

You should list the /boot/grub/device.map

This file contains the relation between devices and grub codes.

Josir.

---

### Post by onetb on 2008-06-23
/boot/grub/device.map reads...
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Is this something to be fixed in the BIOS, or in the GRUB menu?  I want to be thorough about this, because the last time I jumped the gun about a fix, I trashed my xorg.conf file so that I could only boot into shell and had to rebuild a large part of the file before I could boot again.  ](*,)

---

### Post by josir on 2008-06-25
Hi onetb, your grub files seems to be fine. My last try:

When you got the grub menu hit edit (E) instead of hit enter.
Then, change the (hd0) with (hd1) and hit boot to see what happens.

If this tip does not work, I can't find a way to help you anymore - my knowledge on this matter ends here... I will leave you with more experient users.

Good Luck,
Josir.

---

### Post by onetb on 2008-07-01
Sorry I haven't gotten back, but without implementing Josir's last suggestion, I have not experience the problem again.  Don't know why, but it has just stopped happening.  Will revise the post later if the issue returns.

---

