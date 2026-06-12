---
title: "Where Are Temporary Files Stored?"
date: 2021-08-14
forum: General Help
---

### Post by wyattwhiteeagle on 2021-08-14
I'm not able to install Ubuntu to the internal hard drive until it's fixed or replaced.

Where does the "Try Ubuntu" store temporary files and where are they purged to?

---

### Post by Frogs Hair on 2021-08-14
AFIK a live session stores nothing on the computer or boot medium. It possible to create usb with persistence so you can save your work/files.

---

### Post by QIII on 2021-08-14
"Try Ubuntu" makes no changes to your storage devices unless you deliberately mount storage media on the machine and write things there.  Generally, it runs entirely from files on the install media and in memory.  There are no temporary files saved when the memory is purged when you shut the machine down.

If you create media "with persistence", then files may be saved on the medium containing the image, but, as above, not on the machine unless you deliberately do it.

---

### Post by wyattwhiteeagle on 2021-08-14
Would there be a need to use something like BleachBit while in the live session to keep from "eating up" the free space of the 128 GB LiveUSB Session? 

(it shows at first there is 125 GB usable freespace on the live session 128 GB USB stick.)

---

### Post by QIII on 2021-08-14
If you did not create the media with persistence (I'm guessing you didn't), then Bleachbit is not necessary.  Any applications you install on a live session are installed only to the in-memory OS.  Those installed applications do not survive the end of the session and would have to be re-installed the next time you booted to the media.

In fact, any changes you may make to the OS in-memory are utterly lost as the volatile memory is cleared when shutting down.

Without persistence, that 128GB USB device will always be unusable, wasted space.  You will only be using read-only files used to start the OS in-memory or read and held in memory when the OS is running.  A 128GB device doesn't provide more resources in a live session than a 16GB one.

---

### Post by wyattwhiteeagle on 2021-08-14
> **QIII said:**
> If you did not create the media with persistence (I'm guessing you didn't), then Bleachbit is not necessary. Any applications you install on a live session are installed only to the in-memory OS. Those installed applications do not survive the end of the session and would have to be re-installed the next time you booted to the media.

In fact, any changes you may make to the OS in-memory are utterly lost as the volatile memory is cleared when shutting down.

Without persistence, that 128GB USB device will always be unusable, wasted space. You will only be using read-only files used to start the OS in-memory or read and held in memory when the OS is running. A 128GB device doesn't provide more resources in a live session than a 16GB one.

That's the very reason I hardly ever shut it down.

Because of not shutting down, any changes made to the volatile OS in-memory seems to be filling up and leaving me with a "not responding" and "freezing up" system.

Installing things also help use up all the "volatile in-memory" and leaves no room for the user to actually do anything.

I'm financially broke until I get paid and have to pay it all to bills. Until I can repair or replace the internal hard drive, I'm stuck using the Live-USB "Try Ubuntu" session.

I don't have the luxury of having the money to just go get a bigger usb stick or a working internal hard drive.

I can't install anything on the internal hard drive at all. Not Windows or Ubuntu or anything else.

I'm "stuck" using the Ubuntu "try it" live session.

I don't enjoy spending all day re-installing and updating and upgrading just to have to do it all over again the next day.

May I please have the locations where things are being stored?

---

### Post by QIII on 2021-08-15
Again: *they are not being stored*.  That is the nature of a live session in memory.  They exist only in memory during a live "Try Ubuntu" session.  If you are installing and running more stuff in memory than you have physical memory to hold it, it is not surprising that it is locking up.

You can actually install Ubuntu on the USB device as your "hard drive".  Would you prefer to do that?

---

### Post by wyattwhiteeagle on 2021-08-15
> **QIII said:**
> Again: *they are not being stored*.  That is the nature of a live session in memory.  They exist only in memory during a live "Try Ubuntu" session.  If you are installing and running more stuff in memory than you have physical memory to hold it, it is not surprising that it is locking up.

You can actually install Ubuntu on the USB device as your "hard drive".  Would you prefer to do that?

ok, something you are saying is what is throwing me from understanding what you are meaning.

You're saying, "in memory." A lot of people these days have no idea what RAM stands for. RAM stands for Random Access Memory while people these days differentiate "RAM" and "Memory stick" and believe that RAM has nothing to do with memory.

To me, a "USB thumb stick" (a.k.a. flash drive or USB hard drive) isn't a "RAM stick".

It sounds like you are saying "live session in memory" as if to mean "in the memory of the flash drive only".

I expect the memory of the live session to be emptied at every shut down.

Someone here on the forums had posted that a USB can't install to another USB port. Is that no longer true?

Considering that a "Ubuntu bootable" usually means on a USB, how can Ubuntu be fully installed and maintained on a USB flash drive?

Is the 128GB flash drive more than enough to receive a full install and be able to sufficiently be updated, upgraded, and properly cleaned and backed up?

I honestly didn't know I had that option, and I apologize.

---

### Post by ActionParsnip on 2021-08-15
The live desktop runs in RAM. If you have persistence then you will have a large persistence file where your changes are written to.
If you are using live desktop a lot then I suggest you install the OS to the USB stick (will require 2 USB sticks. One to install with and one to install from). You can then use the entire USB stick just as you would an internal disk. The physical connection media is utterly irrelevant

---

### Post by wyattwhiteeagle on 2021-08-15
> **ActionParsnip said:**
> The live desktop runs in RAM. If you have persistence then you will have a large persistence file where your changes are written to.
If you are using live desktop a lot then I suggest you install the OS to the USB stick (will require 2 USB sticks. One to install with and one to install from). You can then use the entire USB stick just as you would an internal disk. The physical connection media is utterly irrelevant

OOO, no offense meant to anyone but now I feel like a kid on Christmas morning!

Are there steps I should take before trying to just install to the flash drive?

---

### Post by wyattwhiteeagle on 2021-08-15
After switching which usb flash drive i used as the live session (8 GB) and which one to install ubuntu onto (128 GB)

I am currently on the 8 GB live session.

I found some tutorials on the internet.

Following the below tutorial...
(but choosing Normal install and no updates and no third-party)

[https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/](https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/)

After booting with the full Ubuntu (128 GB), it opened LivePatch then it went away then it started acting like it was running from 2 seperate OS graphics.

When I simply moved the mouse not clicking anything, the display started blinking, showing the normal UI and showing what looked to be another window showing what the normal was showing.

Did I do something wrong?

---

### Post by wyattwhiteeagle on 2021-08-16
Here are the screenshots showing info abt the usb Install.

One of the images show that I'm not able to do a SMART Scan and Self-Test on the drive.

---

### Post by QIII on 2021-08-16
@wyattwhiteeagle

No, I am not saying the USB device is memory.  It is *storage*. 
> ... believe that RAM has nothing to do with memory.

This is the misapprehension that is confusing you.  RAM *is* memory and the USB device is *storage*.  These are two basic and separate concepts.  There is nothing to be confused about here.


When you run a live session, it is all in memory -- all the files you create, all the apps you install, *everything*.  These things are not saved on USB storage if you do not create it with persistence.  What is needed to run the OS in memory is contained in read-only files on the USB (or other media) and those have to be read into memory by the running OS just as if you were running from any other storage device.  However, nothing you do is saved back to the storage device.  It exists only in RAM.

Thus, temporary files are not "stored" anywhere and everything disappears entirely, without a trace, when the memory is cleared at shut down.

---

### Post by wyattwhiteeagle on 2021-08-16
reading an answer on askubuntu.com...I think i found what I did wrong...

[https://askubuntu.com/questions/1119700/how-to-fully-install-ubuntu-on-usb-flashdrive](https://askubuntu.com/questions/1119700/how-to-fully-install-ubuntu-on-usb-flashdrive)
I noticed in the chosen answer it is advised the the internal HDD be disconnected as well as both new partitions marked as primary.

In my mistakes, I didn't disconnect the internal and I chose the 2nd new partition as logical and not primary.

I shall try again and return with a report.

Cheers :)

---

### Post by wyattwhiteeagle on 2021-08-16
> **QIII said:**
> @wyattwhiteeagle

No, I am not saying the USB device is memory. It is storage.


This is the misapprehension that is confusing you. RAM is memory and the USB device is storage. These are two basic and separate concepts. There is nothing to be confused about here.

The confusing part wasn't the two pieces of hardware, but was how I read what you were saying.

I was learning about computers long before usb flashdrive's was in the retail markets. While learning, I didn't even know what a flashdrive was let alone heard of one. I learned what RAM is.

When I finally heard of a usb flashdrive, I asked for an explanation and learned that it was like an external hard drive that plugs into a small port on the computer without opening the case and without using a cord.

About four years ago, I walked into a Walmart with a memory stick in my pocket. I asked the kid working in the electronics department if they had any memory sticks. He showed me all kinds of usb flashdrive's. I showed him my memory stick and explained to him that I was needing to help my laptop run faster. He then proceeded to "inform" me that a memory stick isn't going to help me, that I need more RAM, and put emphasis on RAM. I then thanked him for that "uneducated" information and left the store.

The confusing part was how I thought the live session worked. I was unaware that the live session actually uses the RAM. I believed that it doesn't use the RAM at all but "stored" things on the flashdrive in temporary folders which disappear at the termination of the live session.

---

### Post by wyattwhiteeagle on 2021-08-16
> **wyattwhiteeagle said:**
> reading an answer on askubuntu.com...I think i found what I did wrong...

```
https://askubuntu.com/questions/1119700/how-to-fully-install-ubuntu-on-usb-flashdrive
```

I noticed in the chosen answer it is advised the the internal HDD be disconnected as well as both new partitions marked as primary.

In my mistakes, I didn't disconnect the internal and I chose the 2nd new partition as logical and not primary.

I shall try again and return with a report.

Cheers :)

It turns out that I was making more mistakes than just those two.

1. My laptop is a Windows 7 laptop and probably more mismatched hardware "rigged up" to work. I believe it's time to just get a new one when I have the money.

2. I only have 4 GB RAM. More RAM would help.

3. My lappy didn't boot Ubuntu normally while I had the internal disconnected and the installed usb plugged in.

4. With the internal connected, Ubuntu booted and loaded the LivePatch notice then seemed to do nothing else except show me that I can move the mouse. Just seemed very very slow.

Looks like my next option is to recreate the live session on the 128 GB with persistence.

---

### Post by wyattwhiteeagle on 2021-08-16
Uh oh...

When I tried to create the 128 GB LiveUSB with persistency, It gave me an error saying that the specified file couldn't be located.

I have 2 Ubuntu 20.04 LTS Live USB's. One 8GB and one 128GB.

Is there a way to create a persistent partition on the 128GB somehow?

---

### Post by dragonfly41 on 2021-08-16
This guide might help you, using mkusb.

[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by wyattwhiteeagle on 2021-08-17
> **dragonfly41 said:**
> This guide might help you, using mkusb.

[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

I got good news and bad news...

Bad news...I'm having to still use the basic live usb (safe graphics)

Good news...I now have a 128 GB persistent live usb. Thank you for that link, It helped.

I think I made a small but very important mistake.

When I tried the persistent live session...it booted and loaded fine until I clicked on settings to disable the screen fading black.  I clicked on settings and a little later the screen went black then went to the Live Session User for me to log in.

I'm not sure if it restarted or not.

After I clicked to log in, it was taking a very long time to fully load.

What is going on with this thing?

Would creating a swap partition or doing something like "virtual memory" help?

---

### Post by TheFu on 2021-08-17
> **wyattwhiteeagle said:**
>  
Would creating a swap partition or doing something like "virtual memory" help?

Very unlikely. I wouldn't bother.

---

### Post by wyattwhiteeagle on 2021-08-19
> **mastablasta said:**
> in linux unlike in windows, the drivers are part of the kernel. newer kernel usually means newer drivers.


only a few proprietary drivers are added to kernel after install (some are optional). whatever works with linux usually has drivers already available.

> **mastablasta said:**
> you can install the whole OS on USB or use a live session with persistency for that

A lot of people are saying that live session with persistency works very well on a 16GB usb.

I believe other options include installing to usb or an older release of Ubuntu for the more compatible drivers.
(my system shipped with Windows 7 Home Premium (SP1).

With more frequent cleaning, purging, removing, uninstalling, backups, etc due to only 128GB

Are these other options?

---

### Post by TheFu on 2021-08-19
Anything that works is an option.

I only use flash media for emergency needs with an OS.  Running an OS off it drastically reduces the lifespan due to the write count limits that all flash storage has.  Logs are constantly written.  

Be certain you backup the storage when there is something important on it.  For example, if this flash contains a full semester of school work.  I know people who have lost everything on the flash drive because it died about 2 months after they set it up.  I know other people who happily use them for over a year.  Somehow, storage _knows_ when it holds critical stuff and that's when it dies.  But if we have multiple, versioned, backups, then either it won't die or when it does we don't care (so it isn't a big deal).

Only 128G?  If you use a lite Linux, 16G is more than enough. Then the rest of that storage can be used for junk data.  I've run a few laptops with just 16G SSDs for a few years.  My main desktop (20.04) has .... let's check .... 
$ df -Th
```
Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/vda1                  vfat  511M  7.1M  504M   2% /boot/efi
/dev/mapper/vgubuntu--root ext4   19G   15G  3.2G  83% /
/dev/mapper/vgubuntu--home ext4   12G  6.3G  4.9G  57% /home
```
So, more than enough storage.  There's a 4.1G swap LV too, which isn't included above. In total, it has 42G on that SSD.

If you control the OS/applications bloat, and avoid snaps, a $10 USB3 64G flash drive should be more than enough for everything for a few months.  Keep the junk on different storage, say an SD card for media that doesn't need high performance and is mostly read-only.

But whatever works, is fine.  It won't be the fastest, but the USB3 it won't be the slowest either.  A cheap SSD in a $9 SSD-to-USB3 enclosure would be even better.  Those enclosures come fairly small - like 2 zippo lighters only and about that thick for an m.2 2280 SATA SSD.  I have an enclosure for an m.2 2242 SATA SSD and it was great until the SSD died. It ran out of writes. When it died, even reading data wasn't possible.

---

### Post by wyattwhiteeagle on 2021-08-19
My df -Th output (128GB USB Safe Graphics live session no persistency)

```
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     382M  1.7M  380M   1% /run
/dev/sdb1      vfat      120G  2.8G  117G   3% /cdrom
/dev/loop0     squashfs  2.0G  2.0G     0 100% /rofs
/cow           overlay   1.9G  195M  1.7G  11% /
tmpfs          tmpfs     1.9G     0  1.9G   0% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     1.9G  500K  1.9G   1% /tmp
/dev/loop2     squashfs  219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop1     squashfs   56M   56M     0 100% /snap/core18/1988
/dev/loop3     squashfs   65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop4     squashfs   52M   52M     0 100% /snap/snap-store/518
/dev/loop5     squashfs   32M   32M     0 100% /snap/snapd/11036
tmpfs          tmpfs     382M   68K  382M   1% /run/user/999
```

That's awesome to know, however I have a few questions.

1. Would a "minimal install" of an older LTS version be considered a "lite linux"?

2. Backups: Data recovery. This gets me a bit confused. Is it backup data as in personal pictures, budget/family records, fav music, etc...or is it data that the system uses to recover/repair/restore the filesystem, or like a Windows OS "Last known good configuration", or is it both?

3. Snaps: Is it a camera image or a screenshot; what is refered to as a snap?

4. Flashdrive Write Counts: This is the first I've heard of it. Is this an I/O threshold specific to the flashdrive hardware?

---

### Post by TheFu on 2021-08-19
> **wyattwhiteeagle said:**
> df -Th output (128GB USB Safe Graphics live session no persistency)

```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      vfat      120G  2.8G  117G   3% /cdrom
/cow           overlay   1.9G  195M  1.7G  11% /

```

Every other line isn't real storage.  120G FAT32 isn't good.  Is it read-only?   FAT32 is limited to 64G by the standards. And only 2.8G is being used.  So, for what this system is using today, only 8GB would be sufficient now. Over time, the overlay will grow.

> **wyattwhiteeagle said:**
> That's awesome to know, however I have a few questions.

1. Would a "minimal install" of an older LTS version be considered a "lite linux"?

Nope. Always use a supported release. Always patch it at least weekly.  The internet is a dangerous place. College networks are probably more dangerous than most from what I've seen.

> **wyattwhiteeagle said:**
> 2. Backups: Data recovery. This gets me a bit confused. Is it backup data as in personal pictures, budget/family records, fav music, etc...or is it data that the system uses to recover/repair/restore the filesystem, revitalize the hardware, etc like a Windows OS "Last known good configuration", or is it both?

It is anything you don't want to lose.

> **wyattwhiteeagle said:**
> 3. Snaps: Is it a camera image or a screenshot; what is refered to as a snap?

Snaps are a package type that Canonical has been pushing since 20.04.  If you use their GUI to install software, you very likely have a number of snap packages.  The alternative would be APT packages or Deb packages or AppImages or Flatpaks.  Your df output says 5 packages on your system are snap packages.  Snaps use more storage than deb/apt packages.

> **wyattwhiteeagle said:**
> 4. Flashdrive Write Counts: This is the first I've heard of it. Is this an I/O threshold specific to the flashdrive hardware?
Google to learn more about it. SDHC, microSD, USB-sticks, and SSDs are all flash storage. They all have a designed number of writes. In general, cheaper flash storage is designed for fewer writes before it fails. Enterprise SSDs are both over-provisioned and have higher write counts in the design of the flash.  When it comes to USB flash storage, I wish there was a way to know how many writes each stick has and how to track the count and how to predict before it fails. None of that seems possible to my knowledge.  I wish it was a simple as buying X brand or Y model of USB storage.  I've been disappointed with cheap and expensive USB storage about equally.

> **wyattwhiteeagle said:**
> 5. Swap Area Partition: Is it the "Windows Virtual Memory" but as a separate partition? Will the flashdrive need a swap partition or will a swap area partition conflict with RAM operations?
Virtual memory (swap) needs are dependent on the workload and total RAM inside a system.  For most desktops, if you have less than 12GB of RAM, then you need virtual memory of 4.1G to prevent out of memory issues and system crashes.  There are other uses for virtual memory too.  Google a little. There's a wikipedia article on this too.

---

### Post by wyattwhiteeagle on 2021-08-19
I'm not sure if it's read-only. I will check and post what i find.

I used the defaults in Rufus 3.6 on Windows 7 to create the Live USB.

Is there a way to properly adjust the 120G/2.8G value's to recommended levels even if it means using a different tool to create the bootable usb?

How can I see what those snap packages are and the locations so that I can find the smaller alternatives?

Is there a way to see if a package is a snap before downloading/installing?

---

### Post by TheFu on 2021-08-19
> **wyattwhiteeagle said:**
> I'm not sure if it's read-only. I will check and post what i find.

I used the defaults in Rufus 3.6 on Windows 7 to create the Live USB.

Is there a way to properly adjust the 120G/2.8G value's to recommended levels even if it means using a different tool to create the bootable usb?

How can I see what those snap packages are and the locations so that I can find the smaller alternatives?

Is there a way to see if a package is a snap before downloading/installing?

I don't use rufus, sorry.  There are lots of alternatives.  Lots of people here seem to like **mkusb**. [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)  I played with it about a year ago and found it slightly confusing, but after 3 attempts, I understood what the outcome was for the different options. The terminology used confused me, but perhaps it would make sense to a Windows person?  IDK.

When I'm creating a Try-Ubuntu disk, I use **cp** or **dd** and I don't setup persistent data on it. If I want persistent data, I'll mount other storage in the system and write stuff there.  That probably isn't your use-case.

To see a list of snap packages ... 
```
$ snap list
```

I only use **apt install** from a shell, so no snap packages are ever installed unless Canonical is forcing only the snap to be used. They do this with Chromium-browser and lxd.  To my knowledge, no other packages will install snaps from the shell.  If you use a GUI, I cannot say. I haven't used a GUI for package stuff in years.

Hopefully someone else has better answers to those questions.

---

### Post by wyattwhiteeagle on 2021-08-19
Everything I'm finding is saying that to disable the write protection of any usb device is to dismount the device using "$ sudo su -" in a terminal of an installed or dual-boot session.

but nothing about checking to determine its write protection status.

I may be able to disable the write protection in a Windows session.

---

### Post by TheFu on 2021-08-20
> **wyattwhiteeagle said:**
> Everything I'm finding is saying that to disable the write protection of any usb device is to dismount the device using "$ sudo su -" in a terminal of an installed or dual-boot session.

but nothing about checking to determine its write protection status.

I may be able to disable the write protection in a Windows session.

That isn't the correct instruction.

Run 'mount' without any options to see all the mounts.  There will be 1 per line.  Something like this:
```
/dev/mapper/vgubuntu--home on /home type ext4 ([COLOR="#FF0000"]rw[/COLOR],noatime,errors=remount-ro)
```
That's a read-write mount.  I can create files on that file system.  If it was [COLOR="#FF0000"]ro[/COLOR], then that would be read-only.

ISO files are read-only. No way around that. It is part of the standard.  
Linux doesn't run from FAT32 systems, so it isn't that partition.  An ISO file can be held on a FAT32 file system and mounted from it, but I haven't looked at that recently, so I don't think that's actually what happens when an Ubuntu ISO is "installed" on to a flash drive.  I'm using the 'installed' term to mean bit-for-bit copied, not actually using the Ubuntu Installer from 1 flash drive to install the OS onto another flash drive.  BTW, that works too.

---

### Post by wyattwhiteeagle on 2021-08-20
Ok

It was the official ISO file downloaded from [www.ubuntu.com]("http://www.ubuntu.com")

---

### Post by wyattwhiteeagle on 2021-08-20
> **TheFu said:**
> Run 'mount' without any options to see all the mounts.  There will be 1 per line.  Something like this:
```
/dev/mapper/vgubuntu--home on /home type ext4 ([COLOR=#FF0000]rw[/COLOR],noatime,errors=remount-ro)
```

My live usb...

```
/dev/sdb1 on /media/wubuntu/UBUNTU 20_0 type vfat (rw,nosuid,...(edited out by me)...,errors=remount-ro,(...edited out by me...)
```

It says the live usb is a rw

---

### Post by wyattwhiteeagle on 2021-08-20
I am now on a minimal install on a usb...woohoo

My usb is acting as the internal hard drive, though it has quite a few packages missing from the panel and yes it is running a little slow.

Gparted has disappeared. Not a prob...I already have the sudo codes to get it back.
Disk Usage Analyzer is gone. I need to find the sudo codes for it.

The Software Center redirects to open the Snap Store

---

### Post by wyattwhiteeagle on 2021-08-20
$ df -Th
```
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     382M  1.7M  381M   1% /run
/dev/sdb1      ext4      112G  4.9G  101G   5% /
tmpfs          tmpfs     1.9G     0  1.9G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     382M   52K  382M   1% /run/user/1000
/dev/loop0     squashfs   32M   32M     0 100% /snap/snapd/11036
/dev/loop1     squashfs   56M   56M     0 100% /snap/core18/1988
/dev/loop2     squashfs  219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop3     squashfs   65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop4     squashfs   52M   52M     0 100% /snap/snap-store/518
```

$ snap list
```
Name               Version             Rev    Tracking         Publisher   Notes
core18             20210128            1988   latest/stable    canonical&#10003;  base
gnome-3-34-1804    0+git.3556cb3       66     latest/stable/…  canonical&#10003;  -
gtk-common-themes  0.1-50-gf7627e4     1514   latest/stable/…  canonical&#10003;  -
snap-store         3.38.0-59-g494f078  518    latest/stable/…  canonical&#10003;  -
snapd              2.48.2.1            11036  latest/stable    canonical&#10003;  snapd
```

How do I uninstall and clean out all traces of the removable snaps and replace them with the better ones that aren't snaps?

---

### Post by TheFu on 2021-08-20
> **wyattwhiteeagle said:**
> My live usb...

```
/dev/sdb1 on /media/wubuntu/UBUNTU 20_0 type vfat (rw,nosuid,...(edited out by me)...,errors=remount-ro,(...edited out by me...)
```

It says the live usb is a rw

Don't confuse an entire storage device with a partition.  USB is the entire storage device and it isn't rw or ro.  The partition is.
vfat = FAT12/FAT32/FAT16.  None of those can be used to run Linux off.  It just doesn't work.  

Here is what a standard Ubuntu ISO placed onto usb or sdhc storage using dd/cp/unetbootin/Etcher/Yumi does:
 Disk --> Partition --> ISO --> pseudo-disk --> read-only Partitions

An ISO is a read-only storage format and nothing inside it can be directly modified.  To modify an ISO, it has to be re-mastered ... which is done by copying all the files out to different storage and modifying those files, then writing a new ISO file (or to optical media). No other way.

I think we are going in circles. Sorry I'm not any more help.

---

### Post by wyattwhiteeagle on 2021-08-20
> **TheFu said:**
> Don't confuse an entire storage device with a partition.  USB is the entire storage device and it isn't rw or ro.  The partition is.
vfat = FAT12/FAT32/FAT16.  None of those can be used to run Linux off.  It just doesn't work.  

Here is what a standard Ubuntu ISO placed onto usb or sdhc storage using dd/cp/unetbootin/Etcher/Yumi does:
 Disk --> Partition --> ISO --> pseudo-disk --> read-only Partitions

An ISO is a read-only storage format and nothing inside it can be directly modified.  To modify an ISO, it has to be re-mastered ... which is done by copying all the files out to different storage and modifying those files, then writing a new ISO file (or to optical media). No other way.

I think we are going in circles. Sorry I'm not any more help.

No, we aren't going in circle's. It's just your knowledge, as is many members here on the forums, is far more advanced than my own knowledge.

I remember when I first started using Ubuntu. I started with ver 14.04 LTS. There are way more things for me to learn than there is of me just having a"limited knowledge".

It seems as though Ubuntu is somewhat different now than in 2014 and in 2018.

Things like many guides on the internet saying "apt" and "apt-get" are now "one and the same" where as before, they were a little different.

For someone who sometimes feels the need to go back and forth between Windows and Ubuntu without setting up dual-boot, It sends them into that "gray area" where they feel they need to throw out everything they thought they knew about using Ubuntu and gain "new knowledge".

I understand that the whole storage space is (especially when it holds and runs a OS) it usually has at least 2 partitions, sometimes more depending on how the system is setup and used.

The partitions on my usb hard drive may need some adjustments, I'm certain of that. I'm just not sure which adjustments I need to make and what steps to take.

For ver 20.04.*, which is more appropriate...sudo apt autoremove or sudo apt-get autoremove? The same question for autoclean, update, and full-upgrade.
(notice the "apt" and "apt-get" in that question)

Sometimes, just making a simple suggestion, and how to do what is suggested, is more of a help than anything.

Trust me,...you, as well as many other members here at the forums, are more of a help than you all know.

Another person I reach out to for help when I'm "stumped" is OldFred here on the forums, very knowledgable and very helpful. There are others but I can't think of their user names right off the top.

So, now that I have Ubuntu 20.04.x minimal install running on a usb hard drive...(I'm using it even now)...

"backup...trim the 'fat' (bloatware and other unwanted software, updates and upgrades)...backup again"

I actually prefer google chrome...Does Ubuntu require firefox or does Ubuntu go by what the user sets as the default web browser?

---

### Post by wyattwhiteeagle on 2021-08-25
[COLOR=#000000]Yay

I'm not on the LiveUSB. I actually used an 8gb LiveUSB to install to a 128GB usb drive. 6.1gb of that is a swap area.[/COLOR]
I didn't even use MKUSB, only 8gb live and the 128gb and the "Something Else" option in the installation process.

[COLOR=#000000]It isn't like being installed to an internal, but like an external.[/COLOR]
[COLOR=#000000]I'm having to use it as my main drive because my internal is dead.[/COLOR]
[COLOR=#000000]it's working fine so far.

[/COLOR]

---

### Post by wyattwhiteeagle on 2021-08-25
[COLOR=#000000]What directories are constantly being filled up with files, logs, etc that doesn't empty out with just a restart?[/COLOR]

---

### Post by TheFu on 2021-08-25
Logs can be anywhere, but system logs should go under /var/log/.  The size of log files is managed by automatic processes and systemd settings.  System settings are stored under /etc/ .... somewhere.

End user applications can put logs anywhere. There are suggested standards, but some programs don't follow those, so it is best to never assume.  The same applies to server daemons.  They are supposed to use system logging tools, but some do not. Just yesterday I was installing an email filter daemon and it asked if I wanted to use syslog or not.  I could believe it. I went with the default (whatever that was).

When you did the "install", some things were assumed - like either a HDD or SSD was being used for storage, so you'd be fine with logs.  This is NOT called a "persistent" install ... By using that term, I initially assumed you were booting from the ISO and had done something special.  You seem to be running a normal install, just sent to USB flash storage, not an SSD.  Ouch.

If you were to run using a Live-Boot environment with persistence, then the /var/log/ directory would probably be a RAM disk - in-memory-only.  I don't know and haven't run one in some time to recall.  mkusb allows making this sort of system.

---

### Post by wyattwhiteeagle on 2022-02-12
I'm no longer fully installed to the usb flashdrive.

Flashdrive disk-write limits was a constant worry.

I've had to resort to installing onto an 80gb internal HDD.

I'm not sure if Internal HDD has disk-write limits.
If so, they are far more above the usb limits as an Internal seems to be made to last a lot longer than a flashdrive.

---

### Post by TheFu on 2022-02-12
If you want the best performance and an external install there are USB3.2 SSD drives available.  

Or you can get almost any SSD (m.2 SATA or m.2 NVMe or 2.5inch SATA) and put those into a USB3 external enclosure.  These cost between $9 and $30 with the NVMe costing the most.  SATA SSDs can reach about 450MBps writes, so they are very fast, but still less than the theoretical USB3.1 bandwidth.  With NVMe, we probably want a USB3.2 interface and a matching port on the computer.  Those can reach 3300+ MBmps ... which is so far beyond what any USB can currently support, the USB port (whatever it is) will be the bottleneck.

If you have tons of money and want fast external storage, Samsung and others will happily charge 40% more than the parts bought separately cost. The assembly is sliding an m.2 storage device into a slot and screwing in 3 screws. It is about the easiest thing to do. Plus, you get to pick the USB type and chips this way.  I've got an m.2 SATA 2242 external USBc enclosure.  Put a very, very, very, cheap SSD into it that came with a Chromebook. Eventually the SSD failed.  I don't trust USB storage, so there was nothing on it when it stopped working.  Seeing how SSDs fail was very enlightening.  I've since only bought reputable brands. Most of those have 3 yrs or 24/7/365 work on them - still working great and fast. 

This will let you have the performance and write counts of an SSD (not all are equal, so get a reputable model/brand like Samsung). A full featured Linux desktop is quite happy with 32-64G of storage. If you want to be smaller, that is possible too, with a little care.  I ran my desktop in 20G of storage for over a decade.  Today, my "desktop" has about 40G if we include the 4.1G for swap I think the smallest SSD still sold is 240GB, so that will have plenty of room.

If the computer doesn't have USB3, don't bother with an SSD for the USB.

---

### Post by HermanAB on 2022-02-14
Note that USB sticks and SD cards come in various speed ratings - the higher the number the better.  A number 6 SD card or higher ( or USB widget) will give you a blazingly fast system.

---

