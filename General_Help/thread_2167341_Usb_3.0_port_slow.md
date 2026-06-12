---
title: "Usb 3.0 port slow"
date: 2013-08-13
forum: General Help
---

### Post by ibrahimrasheed52 on 2013-08-13
Almost search every page of google search related to the issue of USB 3.0 speed in Ubuntu 13.04 or 12.10. I am using Sony USB drive 16GB and in Windows 8 I get around 70MB/sec and in Ubuntu it takes forever, thanks to the LED of my USB drive which shows that the data is being copied even after the progress bar disappears.

I tried my USB 3.0 as NTFS in LIVE CD it works really good but my installed Ubuntu there is just no hope. Is there any way to check or test what is really going on in the background to resolve this issue ):P

---

### Post by ibrahimrasheed52 on 2013-08-15
Anyone or the Ubuntu support has died totally since 12.04 ?

---

### Post by sudodus on 2013-08-15
Writing 'bump' once a day is accepted here. But don't complain about bad support, we are all volunteers :-)

How did you install Ubuntu? What file system, what version are you trying now (13.04)? And what flavour of Ubuntu?

I'm asking because it makes a big difference depending on the computer. Also please specify the computer, at least cpu, ram (size) and graphics chip/card.

What kind of USB 3 drive is it (a pendrive)?

Have a look at the paragraph about USB speed in this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by AbhimanyuAryan on 2013-08-15
i have the same problem i am using ubuntu 13.04 and i have a sony external drive   with usb 3.0 port ubuntu recognizes my drive but drive doesn't show up
after typing lsusb i got this 

cooldudeabhi@cooldudeabhi-Studio-1450:~$ lsusb
Bus 001 Device 003: ID 0c45:6407 Microdia 
Bus 002 Device 006: ID 054c:05bf Sony Corp. 
Bus 002 Device 005: ID 1bbb:0017 T & A Mobile Phones 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 004 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 004 Device 005: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
cooldudeabhi@cooldudeabhi-Studio-1450:~$



see it  recognizes but why don't my hard drive show up? this happened after last update before it was working fine
see the attached picture sidebar doesn't even show it 


ohhhh while i was writting this post i tried again........and my ext. showed after 5min. i attached it..............any sol. why it is too slow?

---

### Post by sudodus on 2013-08-15
Hi *AbhimanyuAryan*

I have no idea why it takes 5 minutes to mount your USB 3 drive. Maybe there is some hand-shaking problem between the firmware and Ubuntu's driver. I think it might help if you specify your system (hardware and software) according to post #3.

Do you run Ubuntu Studio? Are you running the low latency kernel?

What happens if you reboot? Will the computer find the USB drive faster?

---

### Post by VMC on 2013-08-15
> **AbhimanyuAryan said:**
> ...

ohhhh while i was writting this post i tried again........and my ext. showed after 5min. i attached it..............any sol. why it is too slow?

I think your experiencing the bug I reported **[here]("https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1207934")**. It use to take me 5-minutes on most USB devices, but not all. That had me confusted at first.
I compiled kernel-3.8.0 using the patch and now what took 5-min takes 1-second. Also another USB device never mount, and now it to takes 1-sec to mount.
It ends up being a 2-line patch, but takes 1 hour or more to compile?!

---

### Post by ibrahimrasheed52 on 2013-08-15
> **sudodus said:**
> Writing 'bump' once a day is accepted here. But don't complain about bad support, we are all volunteers :-)

How did you install Ubuntu? What file system, what version are you trying now (13.04)? And what flavour of Ubuntu?

I'm asking because it makes a big difference depending on the computer. Also please specify the computer, at least cpu, ram (size) and graphics chip/card.

What kind of USB 3 drive is it (a pendrive)?

Have a look at the paragraph about USB speed in this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)


I totally agree on that. As you can see it was 2 days ago I posted the issue I am facing from past few months. That was the only way to get attention of experts like you. Honestly, one comment brings a lot of HOPE to noobs like me by volunteers like you which makes me volunteer for others in future. Anyways I am sorry if I was really being mean.:KS

[B]Laptop Model :- Lenovo G580 (20157)
Ubuntu Installation Manner :- Did a clean installation on the first day of official release of Ubuntu 13.04 after 12.10 or by removing 12.10 entirely.
Filesystem :- Please find the attachment of the screenshot. (First three partitions are of Windows and then remaining are EXT of linux.)
Ubuntu Flavor :- Unity 
Cpu :- Intel® Core&#8482; i5-3210M CPU @ 2.50GHz × 4 
Memory :- 8GB
Graphics :- Intel® Ivybridge Mobile 
Flash Drive :- Sony 8GB Flash (Gives 40MB/sec on Windows 7 while copying from and 60MB/sec while copying to)[/B]
[IMG]http://s15.postimg.org/4tttnzfvf/Filesystem.jpg[/IMG]

---

### Post by ibrahimrasheed52 on 2013-08-15
I have no issue of detecting the flash drive and this is not just one flash drive any USB with 3.0 or even 2.0. After data is copied (assumed copied as per progress bar) it still keeps copying the data in background whereas windows once it is finished at progress bar. I can safely remove the drive without any issues.

---

### Post by Gilad_Pellaeon on 2013-08-15
Good to know all this as i'm considering purchasing a Western Digital external hard drive but I'd be using USB 2.0 on this drive just to keep backup's of files.

---

### Post by ibrahimrasheed52 on 2013-08-15
I don't know, Ubuntu is just so FLAWLESS then how come USB 3.0 on NTFS behaves so strange.

---

### Post by sudodus on 2013-08-15
> **ibrahimrasheed52 said:**
> I have no issue of detecting the flash drive and this is not just one flash drive any USB with 3.0 or even 2.0. After data is copied (assumed copied as per progress bar) it still keeps copying the data in background whereas windows once it is finished at progress bar. I can safely remove the drive without any issues.
The system copies to a buffer, and writes to the drive afterwards. You can see it if there is a LED on the pendrive. And you can always force writing to the drive with the terminal window command 

```
sync
```

When it returns to prompt, it has finished.

Safe removal of USB drives in Windows corresponds to unmounting the partition(s) on the drive in linux. You unmount clicking the eject symbol on the left pane of the file browser or use

```
sudo umount /dev/sdxy
```

where x is the drive letter and y is the partition number.

It happens in Windows too, that the system continues writing from a buffer to the pendrive. And if you unplug it without safe removal alias unmounting the file system might be corrupted.

The speed is much higher with ***ext4*** than with ***ntfs*** in linux. And the speed is very different between different USB pendrives. I have good experience with Sandisk Extreme 32 GB (USB 3 pendrive).

---

### Post by sudodus on 2013-08-15
> **ibrahimrasheed52 said:**
> I don't know, Ubuntu is just so FLAWLESS then how come USB 3.0 on NTFS behaves so strange.

NTFS is a proprietary file system (owned by Microsoft). The specifications are not available, so it is not easy to make efficient drivers for linux.

*Edit*: And there is the bug, described by *VMC*.

---

### Post by Gilad_Pellaeon on 2013-08-15
> **sudodus said:**
> 
It happens in Windows too, that the system continues writing from a buffer to the pendrive. And if you unplug it without safe removal alias unmounting the file system might be corrupted.

The speed is much higher with ***ext4*** than with ***ntfs*** in linux. And the speed is very different between different USB pendrives. I have good experience with Sandisk Extreme 32 GB (USB 3 pendrive).

So would I be better off formatting my USB flash drives that I have to ext4 and same if I decide to purchase an external hard drive in the future?

---

### Post by ibrahimrasheed52 on 2013-08-15
but again EXT4 isn't supported on Windows except FAT32 or NTFS. Seriously I just noticed by formatting my flash drive to EXT4 (version 1.0) and tried copying 2GB of data , started well with 30MB/sec and came down till 10 MB/sec and when I cancelled the copying of data. There you go its been two minutes it is still blinking.

---

### Post by sudodus on 2013-08-16
> **Gilad_Pellaeon said:**
> So would I be better off formatting my USB flash drives that I have to ext4 and same if I decide to purchase an external hard drive in the future?

Yes, ext4 for linux.

FAT32 is fast in linux (and works in 'all' operating systems).

---

### Post by sudodus on 2013-08-16
> **ibrahimrasheed52 said:**
> but again EXT4 isn't supported on Windows except FAT32 or NTFS. Seriously I just noticed by formatting my flash drive to EXT4 (version 1.0) and tried copying 2GB of data , started well with 30MB/sec and came down till 10 MB/sec and when I cancelled the copying of data. There you go its been two minutes it is still blinking.

That's bad, I have higher speed with my best USB 3 pendrives in USB 2 ports! If your Ubuntu system is still much slower than Windows with the USB 3 equipment I think there are two alternatives:

1. There is a bug in your present version of Ubuntu. Did you try the bugfix, described by *VMC* in post #6? There is also the alternative to try Ubuntu 12.04.2 LTS, which is more debugged and polished because it has long time support.

2. Some hardware or firmware along the data route to the USB 3 drive does not cooperate well with Ubuntu's drivers. Something may be non-standard but fixed to work with Windows, maybe inside the computer, maybe in the USB 3 drive.

---

### Post by ibrahimrasheed52 on 2013-08-16
I made few test by doing deep format with three different ways 

1. NTFS
2. EXT4
3. FAT32

and to my surprise all three have behaved quite similar except in the progress bar results.

1. NTFS :- The copy of one single ISO file started at 34MB/sec and then started going down till 8.4 MB/sec and as usually even after the progress bar disappeared the USB was still active and was copying the data.

2. EXT4 :- Started as usual at 48 MB/sec and finally came down to 17 MB/sec and then it was worst than NTFS after the progess bar disappeared, it stayed for 10 minutes blinking and finally finished copying the data.

3. FAT32 :- This made me happy in the beginning by copying at 70MB/sec and it went fine until it started coming down till 30MB/sec (which was good for me) now its been 15 minutes there is no progress bar but my flash drive is still blinking 

Update :- FAT32 finally stopped copying successfully, hurray I am going crazy.

---

### Post by ibrahimrasheed52 on 2013-08-16
I am sorry I just gone through the link posted in #6 but I am currently having 3.8.0-27-generic and doesn't have much idea about compiling the patch into my current kernel ?

---

### Post by VMC on 2013-08-16
See if you can install Quantel kernel:
```
sudo apt-get install linux-generic-lts-quantal
```
If you can, then on re-boot choose its kernel.

---

### Post by sudodus on 2013-08-16
Well, if you have no experience of compiling (or programming) maybe you must choose some other route.

I wonder if Windows has really finished copying (flushing the buffer to the pendrive) when you think it has. What happens when you click on 'safe removal of the drive'? Will it be ready at once, or will it let you wait?

If it will be ready at once, the write process is really faster in Windows.

Anyway, it might be worthwhile to test Ubuntu 12.04 LTS. If you have another USB drive or a CD drive, you can test it ***live*** (without installing anything).

---

### Post by ibrahimrasheed52 on 2013-08-16
> **VMC said:**
> See if you can install Quantel kernel:
```
sudo apt-get install linux-generic-lts-quantal
```
If you can, then on re-boot choose its kernel.

Thanks VMC but no it is not compatible it says while installing.

---

### Post by ibrahimrasheed52 on 2013-08-16
> **sudodus said:**
> Well, if you have no experience of compiling (or programming) maybe you must choose some other route.

I wonder if Windows has really finished copying (flushing the buffer to the pendrive) when you think it has. What happens when you click on 'safe removal of the drive'? Will it be ready at once, or will it let you wait?

If it will be ready at once, the write process is really faster in Windows.

Anyway, it might be worthwhile to test Ubuntu 12.04 LTS. If you have another USB drive or a CD drive, you can test it ***live*** (without installing anything).

Honestly, its been two years now since I am using Ubuntu and never got disappointed but these days I am really facing situations where I have to be quick on copying stuff from my laptop and I don't mind if it does remain an UNSOLVED mystery but then again I just wanted to give it a TRY solving it instead of living with it.

---

### Post by ibrahimrasheed52 on 2013-08-16
I have Windows 8 as dual boot and yes I tried that it works on not less than 35MB/sec and once it is done and I can instantly do the SAFELY REMOVE and without any issues it ejects the drive.

---

### Post by VMC on 2013-08-16
I think sudodus has the right solution. Try livecd using Precise 12.04, and test the results.

---

### Post by 1clue on 2013-08-16
Some of what you're experiencing with speed is probably related to the usb thumb drive.  None of them work at full USB3 speeds.  The better ones have a speed written right on the package, read and write.  The cheap ones don't bother, because you're not going to be impressed.

Not all USB flash drives are created equal.  There seems to be no standards, or if there are then nobody complies.  At one point I wanted a USB3 drive but wound up getting a USB2 drive because it's actual data transfer rates were higher than the usb3 ones in the store at that time.

Buying a USB drive for performance is like driving through Egypt.  You have to pay attention and be careful.

---

### Post by sudodus on 2013-08-16
> **1clue said:**
> Some of what you're experiencing with speed is probably related to the usb thumb drive.  None of them work at full USB3 speeds.  The better ones have a speed written right on the package, read and write.  The cheap ones don't bother, because you're not going to be impressed.

Not all USB flash drives are created equal.  There seems to be no standards, or if there are then nobody complies.  At one point I wanted a USB3 drive but wound up getting a USB2 drive because it's actual data transfer rates were higher than the usb3 ones in the store at that time.

Buying a USB drive for performance is like driving through Egypt.  You have to pay attention and be careful.

+1

See this [Link to USB 3.0 Flash Drive Speed Tests]("http://www.whoratesit.com/Best-Flash-Drive/Comparison/1")

---

### Post by ibrahimrasheed52 on 2013-08-16
> **1clue said:**
> Some of what you're experiencing with speed is probably related to the usb thumb drive.  None of them work at full USB3 speeds.  The better ones have a speed written right on the package, read and write.  The cheap ones don't bother, because you're not going to be impressed.

Not all USB flash drives are created equal.  There seems to be no standards, or if there are then nobody complies.  At one point I wanted a USB3 drive but wound up getting a USB2 drive because it's actual data transfer rates were higher than the usb3 ones in the store at that time.

Buying a USB drive for performance is like driving through Egypt.  You have to pay attention and be careful.

Its a branded Sony USB 3.0 and it does really working 40MB/sec in Windows and other machines with USB 3.0 ports and thats why I started this posts to seek help. Anyways I have also tried upgrading to my kernel to the latest (mainline) and it is still 10 MB/sec max what its giving right now on all three formats. 

I am going to give it a try by creating a live CD tomorrow for 12.10 LTS and then post the screenshot over here and would also do the same with 13.10 build.

---

### Post by sudodus on 2013-08-16
> **ibrahimrasheed52 said:**
> Its a branded Sony USB 3.0 and it does really working 40MB/sec in Windows and other machines with USB 3.0 ports and thats why I started this posts to seek help. Anyways I have also tried upgrading to my kernel to the latest (mainline) and it is still 10 MB/sec max what its giving right now on all three formats. 

I am going to give it a try by creating a live CD tomorrow for 12.10 LTS and then post the screenshot over here and would also do the same with 13.10 build.

 Try a live CD or USB drive using Precise ***12.04 LTS***, and test the results. I expect that one to be better debugged and more stable.

*Edit*: 12.10 is *not* LTS.

---

### Post by ibrahimrasheed52 on 2013-09-05
Yeah I will. Currently facing a strange issue and I am going post for it.

---

### Post by raj22 on 2013-10-12
I seems the speed has something to do with power management.   When I plug a usb 3 stick and start transfering a large
file, it start with fast speeds around 50 MB/s but then drops to 2 MB/s.   I noticed in /var/log/kern.log:

CPU0: Package power limit notification (total events = 1428)
 CPU1: Package power limit notification (total events = 1428)
CPU2: Package power limit notification (total events = 1428)
CPU3: Package power limit notification (total events = 1428)

then

CPU0: Package power limit normal
CPU1: Package power limit normal
CPU2: Package power limit normal
CPU3: Package power limit normal

If I then use powertop to set Tunables from good to bad the speed improves:

   Bad      Runtime PM for PCI Device Intel Corporation Panther Point USB xHCI Host Controller
   Bad      Autosuspend for USB device UDisk            (General )

---

