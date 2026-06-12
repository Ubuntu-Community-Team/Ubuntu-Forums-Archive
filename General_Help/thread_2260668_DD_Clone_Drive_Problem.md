---
title: "DD Clone Drive Problem"
date: 2015-01-13
forum: General Help
---

### Post by box02-0 on 2015-01-13
Hi.

I have 2 Samsung 850 pro 512 gb ssd drives. (32gb of ram)

I've built the first drive (SDA) with Windows 8 and Ubuntu 14.04 and 2 data partitions.


I booted with a USB which is a remastersys iso of my ubuntu desktop.


I want to clone Drive 1 to Drive 2. I made sure no drives were mounted and nothing else running. 

In Terminal, 
```
sudo dd if=/dev/sda of=/dev/sdb bs=32M

15 minutes later
15262+1 records in
15262+1 records out
```

Copy ended with no errors.

I booted Drive 1, and it worked fine as before.
I booted Drive 2, selected Windows, and I got:
    ```
a required file is missing or contains errors
    File:\windows\system32\winload.exe
    error code 0x000000e
    
```
I used nemo and both drives looked identical. All 4 parttions are there, and all look as expected.
I looked at \windows\system32\winload.exe on both drives, and they look identical.

Why can't I load Windows on Drive 2 ?

M....

---

### Post by vinnywright on 2015-01-13
how did you boot drive 2 ,,,,,,,,,it may be that windows is expecting the DD'ed drive to be  connected to the primary connection (swap the connections on the drives on the MB ) 

but IF this is the case the current primary drive wont boot windows connected as the secondary dive ether .

VINNY

---

### Post by oldfred on 2015-01-14
You cannot clone a drive and have both drives installed at same time.
System works on UUIDs and you cannot have duplicates.

Also with two drives better to have Windows on one drive and Ubuntu on the other drive. Then backup most critical data from Windows into a backkup partition on Ubuntu drive and Ubuntu /home into backup partition on Windows drive.

---

### Post by box02-0 on 2015-01-15
Hi.

Yes I realize that cloning a drive presents a duplicate uuid problem. I didn't think WIndows cared about that, but maybe that was part of my problem.

Recap of what happened:

I did a "dd" of drive 1 to drive 2 (cloned the 2 drives).
With both drives bios enabled, I booted WIN8 sucessfully on drive 1.
 
Using the bios, I forced the 2nd drive to attempt a boot - WIN8 would not boot. The first time, there was a twrling  little wheel, and after 20 seconds WIN8 said there was a problem with my pc. When I tried the next time, WIN8 came back instantly and said there was a problem with my pc. Did the first attempt cause WIN8 to write someting in the registry? 

Here is what I did next:

I repeated the "dd" clone of drive 1 to drive 2.
I disabled D2 and booted D1 - as before, worked AOK.
This time I disabled D1 and enabled D2, and told the bios to boot D2. Worked perfectly!:D

I don't know if it was a uuid problem, or maybe whan I tried to boot WIN8 on D2 (with D1 enabled), Windows saw another copy of WIN8 and didn't like it?? 

Whatever the reason, it works fine now. And it makes sense to have only one drive enabled at a time (except for backup). Was my bad.

So while I have your attention, I have another question. I booted with my remastersys iso usb, with only D1 enabled. I performed a similar "dd" clone from D1, only this time to a parttioned 1 terabyte usb. The copy completed with no errors. I disabled D1, and used the bios to force boot the 1tb usb. No go.

How come it worked fine for D2, but not for the usb?

Thanks for your help,

M..

---

### Post by sudodus on 2015-01-15
> **box02-0 said:**
> Hi.

Yes I realize that cloning a drive presents a duplicate uuid problem. I didn't think WIndows cared about that, but maybe that was part of my problem.

...

I repeated the "dd" clone of drive 1 to drive 2.
I disabled D2 and booted D1 - as before, worked AOK.
This time I disabled D1 and enabled D2, and told the bios to boot D2. Worked perfectly!:D

Yes, this is it :-)
> 
...
Whatever the reason, it works fine now. And it makes sense to have only one drive enabled at a time (except for backup). Was my bad.

So while I have your attention, I have another question. I booted with my remastersys iso usb, with only D1 enabled. I performed a similar "dd" clone from D1, only this time to a parttioned 1 terabyte usb. The copy completed with no errors. I disabled D1, and used the bios to force boot the 1tb usb. No go.

How come it worked fine for D2, but not for the usb?

Thanks for your help,

M..

Windows is made to *not* boot from USB.

If you copy an Ubuntu system (from drive to drive, not to a partition) it will work also in USB drives, even USB pendrives. I have done this many times.

---

