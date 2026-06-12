---
title: "Help, I destroyed my external drive."
date: 2008-01-18
forum: General Help
---

### Post by Charkel on 2008-01-18
Well here we go. Don't laugh :P
I was installing Ubuntu onto a USB pen drive but I did not notice I was doing my external hdd untill it was already to late. So now my 300GB moves and shows are gone.

No I need a guide to restore my disk into a single 320GB NTFS drive which can be used in windows.
I tried to do it by doing:
fdisk /dev/sda
Made a new partition but didn't really know what to choose e.t.c. so now it shows up as a disk with 0kb used and 0kb left...

If someone could please guide me similar to this [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/) I would be VERY great full.

---

### Post by nikolas68 on 2008-01-18
sorry i'm not quite understanding: movies are all gone, right? so why can't you format the HD? is that what you want?

---

### Post by Sam on 2008-01-18
Don't do any activity on the failed disk. This would make the recovery less successful.

Use [this](http://www.cgsecurity.org/wiki/TestDisk) tool. I've successfuly recovered a deleted partition with it.

---

### Post by njparton on 2008-01-18
Just format it under computer management in windows (control panel > administration > computer management > disk management if I remember correctly).

---

### Post by Charkel on 2008-01-18
I don't wanna restore any of the lost media, I already understand that it's forever gone, I just wanna be able to use the disk again.

And njparton, I wasn't able to format it using disk management.

I probably have to make a new partition using Linux I just wanna know how I creat a 320GB NTFS partition in ubuntu. Or maybe a FAT partition to format with NTFS in Windows later on.

---

### Post by nikolas68 on 2008-01-18
Use gparted

---

### Post by njparton on 2008-01-18
Download the gparted live CD off sourceforge and boot from that if gparted in ubuntu can't do it.

---

### Post by nikolas68 on 2008-01-18
> **njparton said:**
> Download the gparted live CD off sourceforge and boot from that if gparted in ubuntu can't do it.

He's talking of an external HD: how can he boot from it?

---

### Post by Charkel on 2008-01-18
There must be a way using fdisk :/
I rmemember I managed to fix a usb flash memory but I don't remember how I did.

---

### Post by nikolas68 on 2008-01-18
> **Charkel said:**
> There must be a way using fdisk :/
I rmemember I managed to fix a usb flash memory but I don't remember how I did.

Just get GParted and in a couple of clicks you'll have your HD formatted how you want it...

---

### Post by Charkel on 2008-01-18
> **nikolas68 said:**
> Just get GParted and in a couple of clicks you'll have your HD formatted how you want it...
I think I got it to work. Got a error the 2 first times but it looks like I made it the 3rd time.
I'm going back into windows now to see if it works. If I don't comment anything more it worked.
Thank you everyone. <3

EDIT: I found it in windows and everything works. But for some reason it's only on 298GB, I've lost 20GB space :/

---

### Post by njparton on 2008-01-18
I thought you said it was a 320GB drive?  298GB formatted sounds about right.  File tables etc takeup space you know

---

### Post by Charkel on 2008-01-18
> **njparton said:**
> I thought you said it was a 320GB drive?  298GB formatted sounds about right.  File tables etc takeup space you know
Yeah, I know but I can swear it was more before all this happened :p Well it ain't nothing to bitch about. I'm glad I can use it again.

---

