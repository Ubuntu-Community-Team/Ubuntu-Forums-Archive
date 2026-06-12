---
title: "Hard Drive Problems"
date: 2007-06-14
forum: General Help
---

### Post by nimrod_cs on 2007-06-14
I recently triend playing around with Ubunt 6.06 "Dapper Drake" LiveCD and it worked well a couple of times, but on the third time I tried to create a partition on my second hard drive, but after getting through a couple of stages I aborted.  Then when I proceeded to shut down the computer it didn't shut down properly and so didn't issue the "killall" command and eject the CD.  So i just turned it off.  From then my desktop wouldn't restart properly back into Vista, it would just hang.  I ended up removing both hard drives and the RAM and testing one by one.

As it turns out, it is only the hard drive I tried to partition that is affected.  So the low down is I can't use it to boot up with, even though it was set as a slave because shomething is causing the system to hang.  Also when I try and use the hard drive in an external USB bay it also hangs.

Does anyone have any suggestions as to how to fix the problem or what is causing it?

So far the only thing I can think of is to take out the primary insert the secondary hard drive and try and boot off the linux disk, and installing linux properly so at least the hard drive might work.  From then on I can either try and wipe it or keep it as a dual boot.

Cheers

---

### Post by smoker on 2007-06-14
hi, just some ideas,

if these are IDE drives, try putting the jumpers to CS (cable select) on each hard drive, assuming each drive is on the same IDE channel, and see if it boots ok off the master then (the master being the one at the other end of the IDE cable from the motherboard. if it does, then you can chkdsk, format, through disk management in vista.

if it doesn't download the gparted live-cd and boot from that, then you can format the drive through that.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

can i ask how you checked the drive? perhaps if the drive is failing, 'drive fitness test' may tell you:
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

best of luck

---

### Post by nimrod_cs on 2007-06-14
Thanks I'll give that a try and let you know how I get on.  But do you have any idea why the hard drive doesn't want to seem to boot?  Its  a fairly new 200 Gigabyte Western Digital @ 7,200 rpm, it was originally used as an external/backup device, but I ended up putting it in my main machine.  So I don't think it can have just died, as this is the only unusual thing that has happened to it.

As for how I diagnosed the problem, I read somewhere that Ubuntu loads into the RAM off the LiveCD, so I thought that when I restarted the computer a few times I didn't leave it long enough for a cool down or to wipe the RAM.  So I physically swapped the RAM over into opposite sockets and tried then and it didn't work any better.  I then tried to remove the hard drive I tried to partition and it booted up relatively normally.  Therefore I can only assume it was that hard drive affecting the system.  Also when I put in the USB caddy Windows Explorer/My Computer window would just lock up.

I don't know whether that will help anyone at all?

Chris

---

### Post by smoker on 2007-06-14
> I tried to create a partition on my second hard drive, but after getting through a couple of stages I aborted. Then when I proceeded to shut down the computer it didn't shut down properly and so didn't issue the "killall" command and eject the CD. So i just turned it off.

> But do you have any idea why the hard drive doesn't want to seem to boot?

i'm only surmising here, but i would guess that because the format was never completed, the drive is maybe not being read correctly, ie, the master file table is corrupt. the gparted app will let you know the state of the drive as far as the file system is concerned, but if you were changing the file system from, eg, ntfs, or fat32, to ext3, and the action was interrupted, then probably the only way to fix this is with a complete new format, and gparted will also do this -  this though is assuming there is nothing mechanical wrong with the drive, which is where the drive fitness test is useful.

best of luck

---

### Post by tgalati4 on 2007-06-14
You might have to low-level format the drive using the Manufacter's Setup program.  You can probably find it on the web or use the Ultimate Boot CD.  This is a disk that contains a collection of manufacter's drive routines and other testing programs.  Handy to have in this situation.

Linux expects perfect hardware, perfect power, and predictable user actions.  Missing one and you will have problems.

What caused you to abort the partitioning in the first place?

---

### Post by nimrod_cs on 2007-06-14
I began the process to see what would happen and what it wanted me to do etc., but I thought that I didn't want to partition my hard drive with linux until I had unplugged to primary hard drive as they are both identical in size and make and have similar names and so I didn't want to risk deleting or losing any data.  

So I set it to abort and followed the procedures and then logged off and that's when my computer started to have problems as Ubuntu would issue the killall command when logging off, I left it for over an hour and then got fed up and turned the power off.  Expecting to be able to reboot into Windows as normal, but obviously something between trying to partition the drive and not issuing the killall command something has caused the drive to be unreadable in Windows.

As for perfect equipment etc., it was fully functioning when I started, and there wasn't much else I could do asit was stuck in perpetual limbo, so I just powered it down.

Chris

---

### Post by tgalati4 on 2007-06-14
Ouch, sounds like you took precautions and you still got bit.  I've seen several cases where folks try to install dual-boot on machine, have a problem, then end up reinstalling windows which happily reformats their entire drive, losing any data from either the Windows or Linux partition.

The Live CD is enticing, but one needs some partition experience to get through installation successfully.

It's possible that the hard poweroff caused a problem with the drive.  As these are newish drives, sometimes the quality level is suspect.  Also 7,200 rpm drives are less forgiving of power problems.

Also, you need to install Ubuntu with all of your drives installed, otherwise you will find yourself in configuration file hell because the names of the disk drives will change and the install procedure expects that the drives will remain the same after reboot.

Normally the Ubuntu install is smooth, without worrying about data on your other disks.  If you change disks or move things around, you will certainly cause a problem, but it is correctable.  A forum search on "install grub" will give you pointers.

So, that said, you have a busted install and a wonky drive.  You might have to run fixmbr on your Windows Install disk to fix the master boot partition to get your Windows drive to boot properly.  Don't reinstall windows otherwise it will wipe everything.  Windows is good at this.

Good luck.

---

