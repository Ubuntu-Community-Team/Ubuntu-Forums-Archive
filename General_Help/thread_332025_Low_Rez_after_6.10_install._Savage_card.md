---
title: "Low Rez after 6.10 install. Savage card"
date: 2007-01-05
forum: General Help
---

### Post by bdmp on 2007-01-05
I reinstalled to 6.10 edgy and I got 800x600 resolution. It is too low. (under dapper it worked fine)

This is the card: "01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133"

I tried to fix it by running the auto detector again which fixed the resolutin (at least for the log-in screen)but I got in an endless log-in screen loop. Same thing happend when I edited xorg.conf to use 1024x768. 

I reinstalled again after that problem arose to start fresh. So now I am where I started with low resolution.

Any help would be appreated.  Thanks

---

### Post by bdmp on 2007-01-10
Bumping for help. If anyone could point me in the right direction I would really appreciate it.

---

### Post by Mick_user on 2007-01-24
Hey BD , this may help.
I have a t22 with a savage/IX-MV chipset and this worked for me.
Your mileage may vary,but may help.
Go and get ready to edit the xorg.conf.
Under the "Device" heading for thr video card , you can add these lines after the bus ID line.
Option "BusType" "PCI"
Option "DmaMode" "None"
VideoRam       8192     

Or whatever your video ram total, mine is 8 megabytes
Make sure the default color depth is 16 not 24.
If you have a 14" TFT display try under "Monitor" section
HorizSync      30-70
VertRefresh   50-90

That's it,worked great for me.
I understand that the newer Xorg needs the Savage video to be recognized as a PCI device,even though it is an AGP 2x , it can't use the DMA and needs to know exactly how much ram you have for the DRI portion to work.
Mine would lockup so bad that I had to boot as single user in order to even have a useable screen to fix.
The default driver is most likely "vesa" so before you edit the files, do a "sudo modprobe savage" first (no quotes).
There is also no quotes used for the videoram number as I typed it.
This fix also worked on Xubuntu,Kubuntu,Mepis 6 and Debian etch (net install)for me.
Good luck and best wishes on your quest.
Mick

---

