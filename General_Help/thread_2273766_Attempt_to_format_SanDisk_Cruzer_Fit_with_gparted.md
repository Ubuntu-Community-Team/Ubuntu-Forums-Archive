---
title: "Attempt to format SanDisk Cruzer Fit with gparted"
date: 2015-04-15
forum: General Help
---

### Post by offir on 2015-04-15
i have SanDisk Cruzer Fit sdcz33-016g 
[http://www.sandisk.com/products/usb/drives/cruzer-fit/]("http://www.sandisk.com/products/usb/drives/cruzer-fit/")

When I connect the disk to the computer
I have 3 partitions appears
300 MB
262 MB
262 MB

All partitions are empty


1) I activated gparted 
2) I chose the disk I want to format (the SanDisk Cruzer Fit)
3) I did unmount
4) I deleted the partitions
5) I created a new one partition
6) I clicked on [COLOR="#0000FF"]Apply[/COLOR]

The software performed the actions

And shows me one big partition

I close the program
Then the disk unmount and muont again
and It returns to the 3 partitions
As if I did not do anything

I tried several times
You can not delete these partitions


The software shows it delete the partitions
And created one large partition
Listed on the disk[COLOR="#0000FF"][COLOR="#FF0000"] 16GB BL130224570V SDCZ33[/COLOR][/COLOR]

[COLOR="#0000CD"]
[SIZE=4]How can one delete these partitions
And create one large partition ?[/SIZE]
[/COLOR]

---

### Post by Bucky Ball on 2015-04-15
Just a thought: delete the partitions so you have unallocated space then eject the drive. Plug it back in. What do you see? If it's blank space, create the partition. Now eject that and plug it back in. One partition?

Throwing this in because I'd probably give it a go if I was in your situation. I can't think of anything obvious.

---

### Post by offir on 2015-04-15
Now I get an error
Write protected disk
Did not do anything different
Only after deleting partitions
I pressed Apply

---

### Post by buzzingrobot on 2015-04-15
I've had similar problems some times. Very annoying.

Try removing the stick after properly ejecting it, then reboot.  Insert the stick, run gparted, and take a look.  This has sometimes worked for me. (Guessing it has to do with the kernel needing to refresh its notions of the status of drives and partitions.)

I've also resorted to using parted or fdisk.

---

### Post by Bucky Ball on 2015-04-16
Write protected USB? There is a little sliding switch on the side of the dongle. Perhaps you need to slide that the other way ... :-k

---

### Post by offir on 2015-04-16
> Try removing the stick after properly ejecting it, then reboot. Insert the stick, run gparted, and take a look

It does not work

---

### Post by Kenneth_Benson on 2015-04-16
I have one like that, only 4gb. It's hardwired internally to not allow you to do that. Believe me, I've tried. Better to just get a new stick (NOT sandisk) and use that.

---

### Post by Mike_Walsh on 2015-04-16
Hallo, offir. 

If it's what I think it is, you'll not be able to format that USB stick in any way, shape or form. I'll explain why...

Take a look here:-

[http://forums.sandisk.com/t5/All-SanDisk-USB-Flash-Drives/SanDisk-Cruzer-Blade-16GB-write-protected-error/td-p/253484/page/12](http://forums.sandisk.com/t5/All-SanDisk-USB-Flash-Drives/SanDisk-Cruzer-Blade-16GB-write-protected-error/td-p/253484/page/12)

It is, apparently, an on-going problem; and has been for some time. From the look of things, it's a defect in the manufacturing process, and SanDisk are saying 'There IS no fix; send it back to us, and we'll replace it, free of charge'. They're admitting it's their fault, it's not 'fixable', and are offering to replace it for you. It's not just limited to the Cruzer 'Blades', either; the 'Edge's, 'Fit's, and 'Micro's are also affected. It would seem to be a defect in the actual controller hardware/firmware, in a batch that must have escaped the quality control process.

This particular thread was running for over 3 1/2 YEARS; from Feb 2011 to Sept 2014. Although the thread had nearly 50,000 visits in that time, as one of the moderators points out,  the people complaining on the forum represent perhaps a microscopic fraction of 1% of the total number who actually bought them. Rather like the vociferous minority on here who regularly complain about Unity.....loudly, to anyone who'll listen..!


Regards,

Mike. :)

---

### Post by offir on 2015-04-17
Thanks for the details

At first I thought that maybe it's not a USB flash disk
But some kind of key

I read about the problem
I saw that many have this malfunction

The only thing I can do is
Open a service ticket

---

### Post by Mike_Walsh on 2015-04-17
I myself have 4 of the Cruzer 'Blades'. One 8 GB, two 16 GB, and one 32 GB. I haven't had a minute's trouble with them, since the day they were purchased, nearly two years ago. You must have been unlucky enough to get one of the faulty ones.

Regards,

Mike.

---

