---
title: "Speeding up the Boot time"
date: 2013-09-22
forum: General Help
---

### Post by vicke4 on 2013-09-22
HI,
I have been using Ubuntu for the past 1 year.The booting time of the system is about 3mins.I am using Ubuntu 12.04 LTS.What should I do to boost up the booting time???

---

### Post by XBNCPRk on 2013-09-22
That is a pretty long boot time... what are your hardware specs? Also, do you have any programs automatically loading on startup? 

Theres also a util [http://www.bootchart.org/](http://www.bootchart.org/) available to give you a heads up as to what is taking that long to load.

---

### Post by vicke4 on 2013-09-23
Here is my boot chart.......
Can I make it fast....
I am running a intel i3 HP laptop with 2GB ram....
Boot time is about 1.16min.....
[IMG]http://www.imagebam.com/image/cb494c277687642[/IMG]

---

### Post by VMC on 2013-09-23
That boot chart is unreadable, but I was able to pull of your specs, which are quite good.
> Intel Core i5-520M Processor (2.4 GHz, 3 MB L3 cache)* Up to 2.93 GHz with Intel Turbo Boost Technology
Intel Core i5-480M Processor (2.66 GHz, 3 MB L3 cache)*
 Up to 3.18GHz Turbo Boost Technology
Intel Core i3-370M Processor (2.4 GHz, 3 MB L3 cache)*
Intel Core i3-350M Processor (2.26 GHz, 3 MB L3 cache)*
---
Integrated graphic:s (HP ProBook 4520s only)
 Intel HD Graphics
 Microsoft DirectX 10 capable
Discrete graphics: (HP ProBook 4720s only)
 ATI Mobility Radeon HD 5470 graphics controller with 512 MB dedicated video memory
 Microsoft DirectX 11 capable
 ATI Mobility Radeon HD 6370 graphics controller with 1GB dedicated video memory
 Microsoft DirectX 11 capable

Regardless of what cpu or graphics you have, maybe BIOS settings need attention. Did you load any video drivers?

---

### Post by XBNCPRk on 2013-09-23
One immediate suggestion would be to purchase (if possible) more RAM. Though the minimum requirements for ubuntu say 512mb, things such as integrated graphics are going to eat up at least as much again, leaving your system low on memory regularly. 

4gb of DDR3 RAM will run you about 35 bucks on newegg, and more than pay for itself if the system you are using gets anything more than light use.

---

### Post by oldfred on 2013-09-23
I never could read boot charts, but do look at log files. If some process in log file takes a long time, repeats and either then works or fails are then things to review.

gksu gedit /var/dmesg

My SSD shows 12.5 sec and this is a 7 year old dual core system. When booting from hard drive it is closer to 40 sec.

type of entries to review:

> [    3.715003] usbhid: USB HID core driver
[    5.612536] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[    7.924725] Adding 3076412k swap on /dev/sdc11.  Priority:-1 extents:1 across:3076412k 


I have found mounting partitions is slow, especially if they need chkdsk (NTFS) or fsck (ext4).

---

### Post by vicke4 on 2013-09-23
Yes my lap is HP probook 4520s with intel integrated graphics...
Follow this link for readable bootchart.....

[http://www.imagebam.com/image/cb494c277687642](http://www.imagebam.com/image/cb494c277687642)

---

### Post by vicke4 on 2013-09-23
> **XBNCPRk said:**
> One immediate suggestion would be to purchase (if possible) more RAM. Though the minimum requirements for ubuntu say 512mb, things such as integrated graphics are going to eat up at least as much again, leaving your system low on memory regularly. 

4gb of DDR3 RAM will run you about 35 bucks on newegg, and more than pay for itself if the system you are using gets anything more than light use.

Thanks for you response friend I will buy one as early as possible....

---

### Post by XBNCPRk on 2013-09-23
Theres a 5 second gap at the very start of your boot chart that says wait-for-root, which Im pretty sure is just the computer waiting for you to decide if you want to enter grub.

Depending on how comfortable you are with editing your grub.cfg file, you can immediately shave that 5 seconds off by changing the GRUB_TIMEOUT= parameter. You can still access grub if need be, but for single-boot systems its pretty rare for the average user to need to access it at all IMO.


On a related note, assuming this is a single boot (only one operating system) setup, did you leave part of the hard drive formatted as ntfs when you installed ubuntu? or reformat to ext3/4?

---

### Post by vicke4 on 2013-09-23
> **XBNCPRk said:**
> Theres a 5 second gap at the very start of your boot chart that says wait-for-root, which Im pretty sure is just the computer waiting for you to decide if you want to enter grub.

Depending on how comfortable you are with editing your grub.cfg file, you can immediately shave that 5 seconds off by changing the GRUB_TIMEOUT= parameter. You can still access grub if need be, but for single-boot systems its pretty rare for the average user to need to access it at all IMO.

Yes I know I have a dualboot system so I need to have that 5 second delay.......

---

### Post by XBNCPRk on 2013-09-23
Gotcha... perhaps someone better than I can see anything out of sorts, but aside from the 5 sec delay, and cups loading at the very end, it looks like its booting in 45-50 seconds, which isnt bad on a hdd system.

Definitely though if youre using Win on that system as well, you might want to looking at adding more ram... its the best bang for your buck that youre going to get for performance (and Im honestly surprised youre not plagued by windows low memory messages already).

---

### Post by Impavidus on 2013-09-23
I'm using a HP Probook 4530s (slightly higher specs than yours, 7200 RPM HDD, 3GiB RAM) and have a boot time of about 20 seconds. Seems to me something else is going on than a lack of RAM.

I'm not used to reading bootcharts, but is it correct your computer spends 8.5 seconds running fsck? I don't think that should happen every time you boot.

---

### Post by VMC on 2013-09-23
I think, as oldfred alluded to, check the var logs. Specifically, **syslog**, ***kern.log***. Look for any errors and/or failed messages.

---

### Post by vicke4 on 2013-09-24
> **VMC said:**
> I think, as oldfred alluded to, check the var logs. Specifically, **syslog**, ***kern.log***. Look for any errors and/or failed messages.

Follow the below links for my syslog and kernlog.

And the size of the kernlog is 16MB.Is this normal???

kernlog:

[https://docs.google.com/file/d/0B0k76GMavVymLXlnTWVzalBmakU/edit?usp=sharing](https://docs.google.com/file/d/0B0k76GMavVymLXlnTWVzalBmakU/edit?usp=sharing)

syslog:

[https://docs.google.com/file/d/0B0k76GMavVymZWZDQ2FfZm0zQnc/edit?usp=sharing](https://docs.google.com/file/d/0B0k76GMavVymZWZDQ2FfZm0zQnc/edit?usp=sharing)


> **oldfred said:**
> I have found mounting partitions is slow, especially if they need chkdsk (NTFS) or fsck (ext4).

Yes I think Mounting NTFS partitions is taking more time in boot........

> **oldfred said:**
> I never could read boot charts, but do look at log files. If some process in log file takes a long time, repeats and either then works or fails are then things to review.

gksu gedit /var/dmesg


gksu gedit /var/dmesg This code returns nothing means my dmesg is empty....

---

### Post by oldfred on 2013-09-24
Left out log 
Post this:
gksu gedit /var/log/dmesg

do you have anything plugged in that you do not need to?
Have you settings in BIOS for devices you do not have? One user had no floppy drive yet BIOS was reporting it, and system had a heck of time looking for something that does not exist.
Another had a DVD in DVD drive and sytem tried running fsck on it??

Any services you do not use, like bluetooth, wireless, Ethernet on IPv6 or anything else? 
I rarely use wireless on my laptop so I turn it off.

---

### Post by VMC on 2013-09-24
Your kern.log is just to big to look at for me, but ***syslog*** is filled with "Asking for cache data failed". There is a bug report on that. [Read this answer on the data failed question.]("http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning")

Also in the ***syslog*** is "Test WP failed, assume Write Enabled". More answers [here]("http://askubuntu.com/questions/194933/what-do-these-hard-disk-errors-test-wp-failed-assume-write-enabled-mean").

---

### Post by vicke4 on 2013-09-25
> **oldfred said:**
> Left out log 
Post this:
gksu gedit /var/log/dmesg

Here is the ouput
[https://docs.google.com/file/d/0B0k76GMavVymMUVEaG9tbXFNVG8/edit?usp=sharing](https://docs.google.com/file/d/0B0k76GMavVymMUVEaG9tbXFNVG8/edit?usp=sharing)

> **oldfred said:**
> 
do you have anything plugged in that you do not need to?
Have you settings in BIOS for devices you do not have? One user had no floppy drive yet BIOS was reporting it, and system had a heck of time looking for something that does not exist.
Another had a DVD in DVD drive and sytem tried running fsck on it??

Any services you do not use, like bluetooth, wireless, Ethernet on IPv6 or anything else? 
I rarely use wireless on my laptop so I turn it off.

No I have turned off all devices that I don't use.Let me check the BIOS settings.I will report you the result later......

---

### Post by oldfred on 2013-09-25
This says you are booting in 27 sec? Now with my system BIOS takes 10 sec, grub about 5, and system 25. If from hard drive BIOS & grub are same but system takes 40+ sec.

 Longer entries:
[    5.676497] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.397885] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   21.628294] Adding 4193276k swap on /dev/sda8.  Priority:-1 extents:1 across:4193276k 

   
Last entry
[   27.805872] iwlwifi 0000:43:00.0: Radio type=0x1-0x3-0x1

It looks like the mount of an external drive takes some time? It is the time between posts that is how long, but I do not know if post is after it completes previous or at beginning of task?

---

### Post by vicke4 on 2013-09-25
Okay what to do with this problem.Is there any way to fix this??Any suggestions???

---

### Post by oldfred on 2013-09-25
IF 27 sec is boot time with a hard drive, I am not sure you have any problem.

---

