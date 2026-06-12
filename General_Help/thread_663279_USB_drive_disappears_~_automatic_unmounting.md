---
title: "USB drive disappears ~ automatic unmounting?"
date: 2008-01-09
forum: General Help
---

### Post by josh.on.linux on 2008-01-09
Hi!

I am fairly new to Linux, have been using Ubuntu 7.10 for about two to three months at home.  I use a DELL machine with a built-in harddrive carrying Linux and Windows and two external USB hard drives.  Just recently I noticed that after a few hours of uptime (not sure uptime is connected to the whole thing, but it seems to happen only after some uptime), my USB drives suddenly are not mounted anymore.  One click in Nautilus will mount them again, but still, it's a little strange and bothersome (I have my files spread out all over those drives, organized into categories with bookmarks in Ubuntu).

Any idea what could be the reason?  Is there any "auto-unmount" "feature" in Ubuntu?  How would I check to see what could be the issue?

Another thing: What could be the problem when I cannot manage to copy a larger amount of data (e. g. 300 MB) to an SD?  The device will be removed from the computer (unmounted?) during the copy process and the process will fail.  This error is repeatable.

Any help would be greatly appreciated.  Thanks in advance!

Josh

---

### Post by feistybird on 2008-01-10
Are you having your USB Disk attached to your PC during most of the time? (no need to remove it often?) 

Then you might want to try mount it automatically by editing /etc/fstab

About the SD card's larger file transferring problems, I sometimes have the same problem in Windows too... probably because I once accidently had it forgotten in the washing machine...

---

### Post by josh.on.linux on 2008-01-11
> **feistybird said:**
> Are you having your USB Disk attached to your PC during most of the time? (no need to remove it often?) 

Then you might want to try mount it automatically by editing /etc/fstab

About the SD card's larger file transferring problems, I sometimes have the same problem in Windows too... probably because I once accidently had it forgotten in the washing machine...

Yes, I have both USB disks attached all the time.  I have set up my system in a way that enables me to create images of a running system w/o having my documents and non-system relevant files in the image.  

How would I edit /etc/fstab to mount the disks automatically?

---

### Post by dcstar on 2008-01-12
> **josh.on.linux said:**
> Hi!

I am fairly new to Linux, have been using Ubuntu 7.10 for about two to three months at home.  I use a DELL machine with a built-in harddrive carrying Linux and Windows and two external USB hard drives.  Just recently I noticed that after a few hours of uptime (not sure uptime is connected to the whole thing, but it seems to happen only after some uptime), my USB drives suddenly are not mounted anymore.  One click in Nautilus will mount them again, but still, it's a little strange and bothersome (I have my files spread out all over those drives, organized into categories with bookmarks in Ubuntu).
.........

Sometimes power management can shut down things like USB ports after a certain period without use, you may want to check the settings.

Also, running "dmesg" in a terminal should provide you with some info as to what is happening.

---

### Post by josh.on.linux on 2008-01-12
> **dcstar said:**
> Sometimes power management can shut down things like USB ports after a certain period without use, you may want to check the settings.

Also, running "dmesg" in a terminal should provide you with some info as to what is happening.

I checked the power management under System - Preferences - Power Management, and there was hardly anything I could set up.  Nothing as to USB devices.

I ran "dmesg," but the output did not seem to be to helpful in identifying the problem (at least for me).  I then checked System - Preferences - System Log.  All I could find there was "unmounted [device name]".

It does not seem to be connected to a certain fixed period of time, it seems to happen randomly, and lately it seems to happen a lot more.  I do not remember this happening the first two months I had been using Ubuntu (same hardware setup).

Any ideas?  It's quite annoying...

---

### Post by Klainn on 2008-01-13
I believe I'm having the same trouble as the original poster. It sounds like he has an external, usb harddrive hooked up tot he box that he never disconnects, but yet after x amount of time the thing stops responding and unmounts.

Like him, the dmesg doesn't really tell you anything

[55256.780264] EXT2-fs: unable to read superblock
[55286.367267] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current]
[55286.367274] : Add. Sense: Logical unit not ready, initializing command required
[55286.367279] end_request: I/O error, dev sda, sector 0
[55286.367282] Buffer I/O error on device sda, logical block 0
[55286.367293] Buffer I/O error on device sda, logical block 1
[55286.367303] Buffer I/O error on device sda, logical block 2
[55286.367314] Buffer I/O error on device sda, logical block 3

jason@alucard:/backup/alucard$ grep sda /etc/fstab
/dev/sda1       /backup         ext2    defaults        0       0

mounted in fstab just like the original poster. 

This morning, and I don't know how the op gets it remounted, but I noticed it was unmounted (as there's a cron job at midnight that didn't run because the drive had offlined itself), and couldn't mount it normally..

jason@alucard:/home/jason$ sudo mount /backup/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

In my case I had to sudo fdisk /dev/sda, and then after about 5 seconds, it came back with the partition information and then sudo mount /backup mounted just fine.

Anyone know if there's a way other than possibly setting up a cron job to run hourly to keep the mount acive?

---

### Post by josh.on.linux on 2008-01-15
Does anybody have any more suggestions on this?  It is quite annoying...

EDIT 1: This is very, very annoying.  Now it began to not even allow me to mount certain drives anymore, arbitrarily.  When I boot, all is fine, but then, suddenly the drives are unmounted and one of them I will not even be able to mount anymore.  I get a message saying "Couldn't find [location]".  What on earth is that???  One minute it's working, the next it's gone.

---

### Post by Tobias104 on 2008-01-21
I have been having this problem too. Mostly I just unplug and plug them back in, and they get re-mounted, but it is annoying. This happens for my thumb drive, my external hard drive, and my iPod, all at the same time (I assume, I've never had just one not there when I looked).

---

### Post by killermist on 2008-01-21
I have some thoughts, but I don't know how helpful they will be.

Concerning fstab for mounting USB drives during boot, because the USB subsystem is one of the last to come online, when the system tries to mount everything in fstab, most USB drives will fail because they aren't yet available to the system, and the device files for them are not yet available.  On one machine this caused (until I figured it out) the system to stop booting and sit waiting asking for input about what to do because the device was missing.  After removing it from fstab, the system functioned normally again during boot.

The only recommendation I can really make for resolving the problem might be to hit the console, and mount the drives manually, instead of using the automagic-mounting systems of the GUI.  Usually, mounting drives as root from the console tends to carry a considerable more weight than mounting via GUI tools and file managers.

It's also possible that the problem lies in an area unrelated to any of what I've said, so my thoughts may not be helpful in your specific circumstances.

---

### Post by deeptingler on 2008-01-23
Same problem here too.   Its annoying as I have to switch external drive off then on again for it to re-mount.... prob is... I switched from a large desktop to a neat laptop with external drive but need the external drive to be connected and available 24/7 for streaming data to a media centre.... now because it keeps unmounting itself I find that it affects the media centre availability so is now pushing me back towards a big power hungry desktop again!!!!   just when I was enjoying the silence too.

---

### Post by josh.on.linux on 2008-01-26
> **killermist said:**
> I have some thoughts, but I don't know how helpful they will be.

Concerning fstab for mounting USB drives during boot, because the USB subsystem is one of the last to come online, when the system tries to mount everything in fstab, most USB drives will fail because they aren't yet available to the system, and the device files for them are not yet available.  On one machine this caused (until I figured it out) the system to stop booting and sit waiting asking for input about what to do because the device was missing.  After removing it from fstab, the system functioned normally again during boot.

The only recommendation I can really make for resolving the problem might be to hit the console, and mount the drives manually, instead of using the automagic-mounting systems of the GUI.  Usually, mounting drives as root from the console tends to carry a considerable more weight than mounting via GUI tools and file managers.

It's also possible that the problem lies in an area unrelated to any of what I've said, so my thoughts may not be helpful in your specific circumstances.

Thank you for your thoughts - this at least gives us something to look at.  How would I mount the drives on the console?  Would I have to turn off automatic mounting somehow?

---

### Post by lawhorne on 2008-02-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i have the same or similar probblem.  it seems to be a known bug that is getting worked on.  see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235")

The following workaround worked for me, but it disables usb2.0.

 Workaround for random device disconnections

Random disconnection is a kernel bug that is not fixed yet. Some users report randomly disconnecting USB devices, especially external hard drives. One solution is to start the system with the option "irqpoll" in grub, but this doesn't work for everybody, and is believed to make the whole system slower. The other solution is to disable USB 2.0. This will result in way slower read/write, but the connection remains stable.

To disable USB 2.0, type this in the terminal:

sudo modprobe -r ehci_hcd

Test if the copy/write process is stable, and if you want to disable USB 2.0 upon boot, type:

sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo update-initramfs -u -k `uname -r`

[edit]
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections")

---

### Post by sweetcancer on 2008-02-11
I have this problem too... annoys me like hell. I disabled automagic-mounting by removind the gnome-volume-manager, and now i only mount my drives manually through the command line. My external drives are still unmounting themselves after a little time... I dont want to disable usb 2.0 :(

What if i updated my kernel? is this bug fixed in the 2.6.24 kernel?

---

### Post by lawhorne on 2008-02-11
does anyone know if this is this a generic linux problem or just an Ubuntu problem?  I don't know if the kernel is 100% identical in different distros or not.

Thanks

---

### Post by sweetcancer on 2008-02-13
Now im using Linux Mint 4.0 (based on gutsy) with kernel 2.6.24-7 and the problem still appears...

---

### Post by whoop on 2008-03-02
Came across this thread while trying to find a solution for this problem... I have this problem on two different machines (7.10 32 and 7.10 64). 
After a while usb storage devices get unmounted.
Any updates ?

---

### Post by proalan on 2008-03-03
i had this problem last week.

There has been mention of bugs in the current gutsy kernel, so I tried out the [zen kernel]("http://ubuntuforums.org/showthread.php?t=623874"). No random un-mounts so far. And I dare say it does seem to deliver a more stable / faster experience like it is advertised. 

Just an option anyways, no guarantee that it will solve the problem.

---

### Post by UeB on 2008-03-17
I have the same problem:

I recently (last week) upgraded from feisty to gusty and after that my 2 external usb drives (200 & 400 GB) seem to unmount them self after a while.

it is easy to get them back i just have to press the button on the right hand side next to the home folder button in nautilus. But this does not help the programs that depend on the data from this drives.

I normally happens when there has been no transfer for a while (so it seems to be something diffrent as this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235) )
 I did not have any disconnect while a data transfer was running


Normally the drives appear on the desktop after they are automounted (when i plug them in or switch them on) but after a while the dissapear form the desktop and no program can access them any more. But there are not physically switched off because there power diods are still on.

It is very anoying because I have programs running that need the data from the usb drives but only after random time.
If I knew this would happen I would have never upgraded to gusty :(


Is there anything new about this problem?

---

### Post by proalan on 2008-03-21
The problem returned for me.

The problem mostly occurs when I close a window of the mounted device or finish copying or moving files to and from a usb device.

I notice that this issue only occurs with the laptop, my desktop machine does not get affected by this. Since my laptop is quirky with ubuntu installs anyways I'm going to try the hardy distro upgrade on it.

---

### Post by lawhorne on 2008-03-23
I upgraded to Hardy, hoping that would fix the problem.  It seemed to make it unmount less frequently, but it definitely did not fix the problem.  Any suggestions other than turning off usb2.0?  Thanks.

---

### Post by lawhorne on 2008-03-27
since upgrading to hardy did not fix the problem, I decided to try a fresh install of hardy.  this seems to have corrected the problem for me.

---

### Post by UpSignal on 2008-03-29
i'm having the same problem also. And yes, in hardy this is fixed. However, they should fix this in gutsy..as it still remains 26 days to hardy release. I had it on my laptop and desktop. But it's a little buggy for me, so i decided to get back to gutsy, and now i'm facing this infernal problem again. so annoying...

---

### Post by rabalder on 2008-04-02
Do you know for a fact that this is fixed in Hardy?

---

### Post by lawhorne on 2008-04-02
I don't know.  in my case, the upgrade helped a lot, but did not 100% fix the problem.  I did a complete reinstall and the problem was fixed then.  However, I also disconnected an internal usb card reader at the same time.  So I don't which one was the fix.

---

### Post by WebDesignHero on 2008-06-29
I think I am having the same problem, I am using 8.04 and it was not an upgrade. The drive will turn on, then randomly spin down and disconnect, then usually reconnect (sometimes it dosn't, and even if I unplug/replug it does not recognize the drive). It will also sometimes remount it to a different location. for example /media/New Volume then it reconnects as /media/New Volume_ which makes it useless for my media player sine the library obviously dosn't know its the same files just mounted wrong.

In the 3 minutes I've been sitting here typing, it has spun down, unmounted, then remounted, each time popping up the nautilus window.

Is this the same behavior as everyone else? also, is this because it is an ntfs file system?

---

### Post by lawhorne on 2008-06-29
I had a similar issue, see [http://ubuntuforums.org/showthread.php?t=762095]("http://ubuntuforums.org/showthread.php?t=762095")

I think my drive unmounting for no reason was caused by an internal usb card reader.  after disconnecting it, all my hard drive mounting problems went away.  It was a rosewill card reader.  the other problem with the underscore added after new mount (media player in my case), was not fixed by removing the card reader.  it took a new install.  i didn't do anything differently, just a fresh install.  hope that helps some.

---

### Post by UeB on 2008-06-30
> **rabalder said:**
> Do you know for a fact that this is fixed in Hardy?

In my case the problem is still there after an upgrade to hardy also it "feels" as I they are less often than with gusty. But as I said the problem did not exist before the upgrade to gusty.
A fresh install is no option for me because of the use of some self compiled software which would use to long reconfiguring and recompiling efforts.

I do have an pcmcia flash card reader which is always attached to my laptop and was already in there before I first installed Ubuntu 2 years ago.

I will try if removing it will help.

---

### Post by UeB on 2008-07-05
> **UeB said:**
> 
I do have an pcmcia flash card reader which is always attached to my laptop and was already in there before I first installed Ubuntu 2 years ago.

I will try if removing it will help.

Removing it did not help. Problem is still there.

---

### Post by absheva on 2008-07-12
I upgraded to Hardy in April.  I also bought a 500G WD My Book for rtorrent space.  I never had any problems until I used up all the available space on the disk.  I bought a WD My Book 1T to alleviate the space issue but then the 500 started to randomly unmount.  The CPU usage goes to almost 100%.  I can't kill the rtorrent process.  I can't remount the drive.  Sometimes I can't even reboot the system.  I guess that is what off switches are for.  
I removed the 1T from the system, I have reduced the number of open files in rtorrent.  I have created more available space on the 500.  Still there are the random unmounts.  This afternoon I was not using the disk at all.  I had just rebooted after doing a WD quick test diagnostic which said the drive was fine.  I was burning a disk, the source was an internal drive.  The 500 external decided to unmount.   It killed the burn process.  I really needed one more silver coaster for my collection.  
I am currently running the WD Data Lifeguard extended test on the drive.  The quick test found no problems.  I don't know if it is the drive, my machine, rtorrent, or Ubuntu.  It could be summer too.  The room I am in is about 80 degrees.  The drive feels warm but not hot.  Until the drive started unmounting I was totally satisfied with everything.  But now I leave rtorrent running and it may or may not be when I check on it.

---

