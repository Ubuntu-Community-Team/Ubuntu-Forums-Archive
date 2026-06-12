---
title: "DDRescue on internal HD with I/O Errors."
date: 2015-10-21
forum: General Help
---

### Post by da_wogz_back on 2015-10-21
Hi,

I have a Seagate 320GB hdd which i was running in my previous laptop which became corrupt after the laptop developing a power issue.

When i connect the drive in windows explorer, i see two icons display. One shows "Local Disk [G]" without a file size under it which is where my operating system was stored and another which says "System Recovery [E] which shows 79MB used of 100MB which i can access but there are no files in the folder.

When i try to open the Local Disk G drive in windows explorer when connected via either SATA or USB as it simply hangs when I try to access then simply returns 'G: could not be accessed due to a I/O device error". I have ran multiple different data recovery windows based programs which either take too long to complete and return no files complete, or simply wont read the device at all.

I created a parted magic CD recently and used in an old desktop and connected the failing drive to see what would happen. When i access the device in 'DISK HEALTH' it shows the device, but lists a completely wrong file size of 600 petabytes. However when i run  Fdisk -l, it shows the correct size of both the G and E drives.

PhotoRec and Test disk have both been unsuccessful in recovering anything, so my final option is DDRescue as i have heard that it is quite a powerful tool. Professional data recover is out of the question - i mean, the files are important, and i would really like to get some of them back, but i will not pay exorbitant amounts of money to do so, I either fix it myself or i destroy it, simple.

Anyway, after attempting to copy the contents of the faulty drive to a fresh 500gb spare drive, i was unsuccessful as DDrescue only ran for a flash of a second and listed : 0 bytes rescued...

I have ran HDDguru a while back which returned about 600 bad sectors on the drive (contents move to the spare area) so i know im dealing with bad sectors and a corrput MBR, but what i want is a chance at recovering some of my old files which state that that they have been moved to ' a spare area ' but DDrescue wont even give me a chance. 

Am i missing something while running DDrescue? I cant mount the file either as it states "A mandatory SMART command failed: exiting. To continue, add one or   more '-T permissive' options"

Forgot to add, device was never dropped, nor does it make any clicking sounds. ( spare system recovery partition can be access in windows explorer without any issues, so im sure there must be hope here)

ANY help will be appreciated, ill be watching this thread like a Hawk...

---

### Post by sudodus on 2015-10-22
***ddrescue*** must be able to identify the damaged drive as a mass storage device (/dev/sda in the example below), in order to extract data from it.

I suggest that you try according to ```
info ddrescue
```

```
Example 1: Rescue a whole disc with some partitions in /dev/sda to
/dev/sdb.
Note: you do not need to partition /dev/sdb beforehand, but if the
partition table on /dev/sda is damaged, you'll need to recreate it
somehow on /dev/sdb.

     sudo ddrescue -f -n /dev/sda /dev/sdb logfile
     sudo ddrescue -d -f -r3 /dev/sda /dev/sdb logfile
     sudo lsblk /dev/sdb

```

After that you try to repair the partition table and file systems on the target drive (/dev/sdb in the example) with various tools depending on each file system. If the partition table and file systems are beyond repair, you can try again with ***photorec***, this time on the target drive.

---

### Post by da_wogz_back on 2015-10-22
It does recognise it as a Mass storage device. 

The command I used which rescued nothing was:

```
ddrescue -f -n -u -R /dev/sda /dev/sdb logfile
```

Sda being the problem drive and SDB being the fresh drive.

is there an error with my commands?

---

### Post by sudodus on 2015-10-22
I don't know the option -u

It is not available in the info page of ddrescue version 1.14, that I have. Maybe you used or intended to use another option, for example -v (--verbose)?

---

### Post by da_wogz_back on 2015-10-22
I removed the -u option and ran the command again but the same results occurred:

[http://i.imgur.com/Xtm07p0.jpg](http://i.imgur.com/Xtm07p0.jpg)

it runs, then finishes instantly and displays the above results.

when I view the drive in disk health I see the following (incorrect) information:

[http://i.imgur.com/cj2ccI9.jpg](http://i.imgur.com/cj2ccI9.jpg)

when I try to view in file manager, i see the correct file size, but the following error prevents further access:

[http://i.imgur.com/fHLbuGW.jpg](http://i.imgur.com/fHLbuGW.jpg)

i just know I've got to be doing something wrong. My Linux knowledge just isn't great enough to undertake such task.. Which is why I'm here asking for help :)

---

### Post by sudodus on 2015-10-22
I think that something is very wrong with that drive. I'm not sure that I would succeed with it. There seems to be no S.M.A.R.T. information.

Just double-checking: Are you sure that you have the correct drive letters, /dev/sda and /dev/sdb ? Both of them should be HDDs, while you boot from another drive, I guess from a CD/DVD/USB drive.

---

### Post by da_wogz_back on 2015-10-22
Yes, I'm booting from cd, SDB is the failing drive and SDA is my empty Hdd which I want to recover off once I copy the failing drive to it...

i have run run a smart scan on a Windows based program 'HDD guru' it mainly returns bad sector errors. 660 of them.

---

### Post by sudodus on 2015-10-22
I'm sorry, but I have no good idea how to continue except

- to try again with photorec,

- to disconnect the bad drive and try to connect it again, maybe with another cable and maybe in another computer.

Let us hope more people will read this. Someone may be able to help you with better ideas :-)

---

### Post by da_wogz_back on 2015-10-22
- Tried photo rec many times runs full scan then finds absolutely nothing.

- no luck, tried this multiple times also

its all up to ddrescue... that's my last hope.. In combination with some help on here :)

---

### Post by da_wogz_back on 2015-10-23
Bump?

The fact that I can see the system reserved partition which shows up as healthy partition as soon as I connect the HDD and I am able to access it freely in windows explorer tells me that my hdd can't be a total loss.. 

I know now there is someone out there who can help me here..
please!

---

### Post by stalkingwolf on 2015-10-23
try using the hd regen program on the hirens tool disk.   i have had excelent luck with it .  only once was the drive so bad it wasnt usable after regen.  but it still repaired it enough that i could  save all the files.

---

### Post by da_wogz_back on 2015-10-24
> **stalkingwolf said:**
> try using the hd regen program on the hirens tool disk.   i have had excelent luck with it .  only once was the drive so bad it wasnt usable after regen.  but it still repaired it enough that i could  save all the files.

Okay I will give it a go, but I read that in cases where data recovery is the goal on a HDD with I/O errors, never to try and repair the file systems... could this possibly harm my chances at data recovery by using this tool?

I would also like to add that after hooking up the failing HDD to a more powerful desktop PC via sata, I no longer get "I/O error device' when I try to access the drive in windows, rather I get "CRC Cyclic reduncancy check" instead. When I view the device in disk management, it shows up HEALTHY PARTITION RAW. I managed to run REMO Recover on the drive and it took 10 hours to complete the scan but upon completion, it returned 0 files at 0kb.

Does this mean that somehow ALL my data on the drive has been wiped for good?

I have no idea how this drive got in such a bad state after a simple power supply error...

---

### Post by sudodus on 2015-10-25
> **da_wogz_back said:**
> Okay I will give it a go, but I read that in cases where data recovery is the goal on a HDD with I/O errors, never to try and repair the file systems... could this possibly harm my chances at data recovery by using this tool?

If ddrescue can clone the drive, it is much better to try to repair the partitions and files systems and try to recover files with photorec from from cloned copy than to try to repair the drive itself. But if ddrescue does not work, you must try something else ...
> 
I would also like to add that after hooking up the failing HDD to a more powerful desktop PC via sata, I no longer get "I/O error device' when I try to access the drive in windows, rather I get "CRC Cyclic reduncancy check" instead. When I view the device in disk management, it shows up HEALTHY PARTITION RAW. I managed to run REMO Recover on the drive and it took 10 hours to complete the scan but upon completion, it returned 0 files at 0kb.

Does this mean that somehow ALL my data on the drive has been wiped for good?

In the opening post you wrote "Professional data recover is out of the question - i mean, the files are important, and i would really like to get some of them back, but i will not pay exorbitant amounts of money to do so, I either fix it myself or i destroy it, simple."

It might be worthwhile to ask a professional company what they would charge. Maybe you overestimate the cost.
> 
I have no idea how this drive got in such a bad state after a simple power supply error...

---

