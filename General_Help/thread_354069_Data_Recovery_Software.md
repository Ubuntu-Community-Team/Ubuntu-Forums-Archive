---
title: "Data Recovery Software"
date: 2007-02-05
forum: General Help
---

### Post by ghandi69_ on 2007-02-05
Hi All,

I have a crashed windows hard drive that has valuable data on it.  I have download several data recovery software titles for windows (Stellar, DART), and they all have been able to see my data, but to actually get the data, you have to pay a fee.  I was wondering if there was any type software for linux that would work.  

I have tried DD_Rescue so far, but it was unable to find anything.

Thanks,
Ghandi69

---

### Post by Ryan450 on 2007-02-05
this is what some linux livecds excell at. 

I know in ubuntu you can easily use K3B to burn a datacd to a blank cd if you have that option. 
You could also put in a flashdrive/usb pen drive to backup small amounts of data onto. 
Ubuntu also comes with what you need for network sharing if you need to push the data in question to another computer.

You can easily download the latest ubuntu livecd and use that to do any of the above without actually installing it to the HD. although for that purpose alone it is a bit of a chunky download. If your linux savy I'd say take a look at DSL's livecd, its not as pretty, its not as complete, but it will get the job done as well at 50 mb's to download, but only go that option if you are comfortable with linux.

---

### Post by Bigbluecat on 2007-02-05
In part it depends on what the crash did.

I had a windows crash and the system could not boot and it looked like the data had gone.

It turned out it was a corrupted partition table and all the data was on "D:" instead of "C:".

I downloaded the GParted liveCD and on this there is a programme called TestDisk. It runs from the command line. This was able to recover my partition table and the system booted again. 

Worth trying this.

---

### Post by ghandi69_ on 2007-02-05
Interesting that you say Live CD's are useful for this... I'm an avid linux distro "sampler", and have live CD's for Damn Small Linux, Kubuntu, Ubuntu, and Knoppix.  However, I do not see how they will be helpful.  1, the amount of data exceeds that of what would fit onto a floppy of cd/ or dvd for that matter.  Also, if linux cannot read the information installed on the harddrive when it is hooked up and running.. (my main hard drive shows up as sda.. with linux partitions... my windows shows up as sdb, but it cannot find any partition information)I'm not sure what having a live cd would allow me to do.  Ok, that gparted software looks promising.. is that a linux or a windows program?(or neitehr I guess. since your saying it is a live cd).

---

### Post by etank on 2007-02-05
I use a Knoppix disk all the time to recover data from Windows machines that have blue screened. I load it up, find the data, and then copy it to somewhere else on the network or to a usb drive. The only time that I can't get this to work is when the hard drive is physically dead.

---

### Post by aysiu on 2007-02-05
> **ghandi69_ said:**
> my windows shows up as sdb, but it cannot find any partition information) That's a bigger problem than Windows simply crashing. Your partition table info is gone. You'll need GPart, then (different from GParted). Unfortunately, I don't know exactly how to use it, but a Google search may help you.

This may be a good place to start:
[http://geekblog.oneandoneis2.org/index.php/2006/02/05/triumph_aamp_tragedy](http://geekblog.oneandoneis2.org/index.php/2006/02/05/triumph_aamp_tragedy)

---

### Post by ghandi69_ on 2007-02-05
Yeah, my bad for not being more specific...windows didn't just crash.... the partition information is indeed lost.  Thanks for the help and the advice on using live cd's, I'm sure that information will come in handy at some point.  I'll check into Gpart and cross my fingers!

Thanks for the help,
Ghandi69

---

### Post by Bigbluecat on 2007-02-05
If your partition table is gone it sounds like you have the same problem I did. 

TestDisk works on both windows and linux drives. 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.pcstats.com/articleview.cfm?articleid=1139&page=8](http://www.pcstats.com/articleview.cfm?articleid=1139&page=8)

Disk analysis tools can do more when running from the LiveCD because the hard drive is not mounted. Remember - you are not copying any data off - your are reconstructing the partition table.

You may find (although I am not sure) that TestDisk is on the Knoppix LiveCD. Pop it in, open a terminal and type testdisk.

Read the links above and google a bit more. It saved my windows drive.

---

### Post by ghandi69_ on 2007-02-06
Coming back another day.

I have run Test Disk, but it went through and was unable to find any logical drives.  However, as mentioned, any windows program I download a demo of from Downloads.com has been able to detect the information on my dead drive, but they charge like 70 bucks to get if off of their.  As a linux advocate, this makes me even more determined to try to get the data off of my hard drive using linux.  Any other ideas or programs out there besides TestDisc and Gpart?

Thanks,
Ghandi

---

### Post by Sef on 2007-02-06
Download [Knoppix]("http://knoppix.com") and see if you can pull off the information.  Just copy to a flash drive.  I did that on a hard drive that would not boot up, and GParted would not work on it.

---

### Post by Bigbluecat on 2007-02-06
That's a shame about testdisk. It worked for me. I used the commandline to find that my files still existed and was able to reconstruct the drives.

Good luck getting your data back.

---

### Post by ghandi69_ on 2007-02-07
Back again...

My efforts have now moved onto a bootable .iso in the form of "Trinity Rescue Kit".... I have just stumbled upon it from a different thread in this forum, and was wondering if anyone out there has had any luck with it.  I'm downloading it now and will try it after work.

Ghandi69

---

### Post by UniRecovery on 2007-02-12
If the damage is physical damage on the drive then BEAWARE: any software would cause further damage on the drive. If the drive has developed "bad sectors"  or damage head, then it is imminent that further serious damage will be inflicted on the HDD, which could easily result in permenant damage/loss of data. AVOID using any of these commercial softwares if the damage is on the hardware, these software often are appropriate on logical damage rather than physical ones.

---

### Post by Tanker Bob on 2007-02-12
You can also try SystemRescueCd at [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page).  It boots as a livecd and has a number of disk recovery programs.

---

### Post by az on 2007-02-12
Foremost is a tool to recover files.  It works very well, even if the partition is gone.  Just run it on the raw drive.

You will need to mount a drive somewhere where the recovered files can be saved.

You can run the Edgy live cd and install and run it.  Just enable universe and install foremost

then, mount your hard drive to save the files to (for example /saved) and run

sudo foremost -o /saved -i /dev/sdb

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

---

### Post by ghandi69_ on 2007-02-12
UniRecovery:: I am pretty certain the damage is software related and not physical.. mainly due to the easy most windows apps have been able to recover the data.  I would like to have the data back, but there really isn't a timetable... so it has now turned into a project for me at least to try to get the data back using open-source free software with linux.....

TankerBob:: I looked at the System Rescue website... and the disc contains mostly tools I have tried before.  However, since this disc kinda sets it up using a graphical interface, maybe It will correct any errors I made using those tools...  Either way, this discs looks to be a pretty useful tool to have around, so I'll be downloading and keeping it around anyway.. thanks for the heads up.

AZ::  This is something I have not heard of before and has not been recommended to me.  I have the defective hard drive mounted to a currently running and working edgy install on a different harddrive, so it should be easy for me to test this software out.  Thanks for the recommendation.

:: For those that use windows... and unlike me have some EXTREMELY important data they have lost... I have found that Stellar makes a product called Phoenix that was able to find my information.. although it was like 60 bucks to use.. and a product called D.A.R.T. also was able to recover my data, but again, another 60 bucks are so to purchase.::

---

### Post by euler_fan on 2007-02-12
I'm not sure what kind of damage there is on my drive, but there is this odd grinding noise sometimes when I start up an old laptop of mine. I wouldn't care except there are a few files on it (.doc files mostly, and a few other things) that I care to get back.

Right now when I try to boot, GRUB loads and says there are not bootable partitions. I tried loading an ubuntu live cd and looking at the drive to see what is up, and it says there are no partitions on the drive.

I am downloading KNOPPIX now and have downloaded Foremost, so I hope to get my data off. After that if the drive is junk I am more than happy to spend a few dollars getting it replaced so I have a back up machine.

Any further advice would be much appreciated. Thanks in advance.

EDIT: I can get foremost on the machine that is working fine . . . anyone know how to get it on a CD/flash-drive so I can run it on the damaged machine?

---

### Post by ghandi69_ on 2007-02-13
If you have no working system to boot to, using the live cd options or boot discs like Trinity Rescue Disc or System Rescue are really your only options.

Is there anyway one would be able to treat his damaged drive on a labtop like an external hard drive?  Sorry I'm not more help..but besides some windows apps that could find it.. I havent been able to get my info off my drives either... best of luck.

---

### Post by az on 2007-02-13
> **euler_fan said:**
> I'm not sure what kind of damage there is on my drive, but there is this odd grinding noise sometimes when I start up an old laptop of mine. I wouldn't care except there are a few files on it (.doc files mostly, and a few other things) that I care to get back.

Right now when I try to boot, GRUB loads and says there are not bootable partitions. I tried loading an ubuntu live cd and looking at the drive to see what is up, and it says there are no partitions on the drive.

...

EDIT: I can get foremost on the machine that is working fine . . . anyone know how to get it on a CD/flash-drive so I can run it on the damaged machine?

Just use the Ubuntu live cd, enable universe and install foremost

sudo apt-get install foremost
(You can install stuff while running the live cd - they get installed to the ramdisk)

If you have no net access, it's more complicated.

> **ghandi69_ said:**
> Is there anyway one would be able to treat his damaged drive on a labtop like an external hard drive?  


Well, what would be best in the case of hardware failure is to image the drive - you never know if the time you can actually read the disk will be the last time...

Use dd to image the entire drive to a file (on another, bigger, disk)  Then use whatever tool (foremost) on the image file.

---

### Post by euler_fan on 2007-02-13
Thanks all. I was going to buy an external at some point here soon . . . sounds like that is the next step prior to going too crazy. I just hope in the restarts that happened prior to this point I haven't completely fried things.:-(

EDIT: Sorry for my ignorance (or if I'm missing the obvious), but what is this "dd" tool spoken of?

---

### Post by az on 2007-02-14
dd is a command line tool.  It is short for data dump.

sudo dd if=/dev/sda of=file

That dumps the data from sda to the file named "file"

---

### Post by euler_fan on 2007-02-14
thanks.

---

