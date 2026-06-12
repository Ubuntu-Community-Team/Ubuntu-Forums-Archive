---
title: "Cant format new drive"
date: 2007-06-03
forum: General Help
---

### Post by steam_engenius on 2007-06-03
So I've been scouring threads trying to find some consolation for myself here but not having much luck, figured I'd start one myself. 

I have just received a brand new 160gb SATA hard drive and I obviously want to use it, just for extra storage space. I plugged it in, the computer recognized it, Ubuntu recognized it, I created one big partition for the whole thing and its all at "/dev/hde1".

Now I need to format it and its getting pretty annoying. The first few times I tried running mkfs it was giving me errors. Now it starts doing it (I'm formatting to ext3) but is *extremely* slow. I installed gparted and the drive and partition come up but under file system it says "unkown" and has an exclamation point icon next to it. I tried formatting it through gparted but it failed, I'm trying that again right now. This is the error I receive:

"The following operation could not be applied to disk:

Format /dev/hde1 as ext3

See the details for more information"

And the details just say it couldn't change the partition type.

I'm aching to get access to this space so I would really appreciate it if someone could lend me a hand here. Thanks a bunch.

---

### Post by phidia on 2007-06-03
Have you tried using the live or install cd? You can select that drive and give it any mount point ( I wouldn't use / though) and just cancel the installer after it formats the hde1 partition.

BTW what release are you using? A sata drive would usually be seen as /dev/sd? not _h_.
Although apparently the latest update to feisty changed that.

---

### Post by merlinus on 2007-06-03
Best bet is the gparted live cd from

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by steam_engenius on 2007-06-03
I'm on feisty, and I thought it was supposed to be "s" as well but thats what it gave me so I just kind of went with it. I just burned the gparted live cd so I'm going to try that now. Thanks for the quick reply btw.

---

### Post by pseudonym on 2007-06-03
> **steam_engenius said:**
> I'm on feisty, and I thought it was supposed to be "s" as well but thats what it gave me so I just kind of went with it. I just burned the gparted live cd so I'm going to try that now. Thanks for the quick reply btw. Is the disk connected to a RAID controller, either on the motherboard or an add-on PCI card? Your problem sounds similar to what I encountered when setting up a dual-boot WinXP/Xubuntu on an old IBM P3. The motherboard disk controller is slow so I installed a PCI controller card, which happens to be a RAID card. It uses a special BIOS for the RAID functions and to install WinXP you need to go into this BIOS and set up a RAID array (even if it's just one disk), otherwise the WinXP driver won't see the disk (this is not uncommon with these type of cards).

I didn't think Linux cared about this so after installing WinXP I tried to install Xubuntu without telling it about the RAID array. Things started out fine but problems arose when it came to partitioning and formatting - I got a whole heap of I/O errors and eventually the disk stopped responding.

I've sinced learned that the way out of this situation is to install *buntu using the package 'dmraid', which is designed to work with the RAID BIOS similar to what Windows does. There is a (rather involved) howto [here]("https://help.ubuntu.com/community/FakeRaidHowto?highlight=%28fakeraid%29") if this is the same problem you're having.

If this still doesn't work I'm going to wipe the disk, destroy the RAID array, and then install Xubuntu by itself on the whole disk, without creating a new array. I'm pretty sure that's the path of least resistance.

---

### Post by steam_engenius on 2007-06-03
I booted from the gparted live cd and it started by asking me how I want to configure it so I choose the first option (auto config) and a whole bunch of stuff whizzed by and ended with some errors.

I'm looking into that RAID thing now. I installed dmraid and got this:

michael@michael-desktop:~$ sudo dmraid -ay
Password:
No RAID disks

I dont really understand the whole RAID thing in terms of how it fits in to me formatting the drive, could someone explain? I mean Im not installing Ubuntu on the disk I just want to use it for extra space.

---

### Post by pseudonym on 2007-06-03
If dmraid didn't detect any rAID arrays then my suggestion is probably irrelevant in your case. One thing you could try is verify in your system BIOS that your SATA controller is set to standard operation, and not as RAID.

As far as RAID goes, when you set up your disks this way the operating system uses a different device name to  work with them instead of the usual /dev/sd? or /dev/hd? . If you try to perform an operation (eg. formatting your disk) using the standard device name, it will fail because now the OS 'knows' the disk by its RAID name, and not by its usual one (even though it can still 'see' them with the standard names).

But if RAID isn't set up on your disk controller(s) then this isn't the source of your problem.

---

### Post by rbmorse on 2007-06-03
If you have the Gparted LiveCD I'd just boot the machine form that, use Gparted to completely delete any existing partitions on the drive and then let it create a new partition and format it for you.  

If Gparted won't let you do that at all, then is is likely that there is a problem in setup. 

If Gparted lets you start that operation, but it subsequently fails, consider that the drive may be defective.

---

### Post by steam_engenius on 2007-06-04
I tried running mkfs again and its says its writing the inode tables but its moving terribly slow, at this rate it could take days. It is moving though so I kind of want to just let it finish and see if it works. If not I'll try the GParted LiveCD again.

The drive should not be defective seeing as its a replacement for a defective drive I sent back to WD. Will trying to format the drive so many times mess it up? If so I'm screwed.

---

### Post by steam_engenius on 2007-06-07
It took like 2 days to write the inode tables in mkfs then it sat at "Creating Journals" for a few hours so I decided to just kill it because it obviously shouldn't be going that slow. I tried booting from the gparted liveCD but I cant even get into the GUI because it crashes during some configuration thing at the beginning. I deleted the partition that I had created in fdisk with the gparted I installed on the system, then tried to create a new partition with ext3 formatting, but it failed. 

Its really starting to annoy the $**t out of me so I just unplugged the damn thing and am going to try and forget about it for a little then maybe get back to it. My friend has my Ubuntu install cd so maybe I'll get that back from him and try using gparted in that. I didn't pay for the drive or anything so its not really a huge loss, I was just really looking forward to another 160 gigs of space.

I still don't really get the RAID thing. How would I know or figure out if thats part of the problem? In the dmraid howto it says "If you get errors or "No RAID disks", you need to repair these before you continue." But I mean that presuming that you're aware that your hardware is using RAID, and I have no idea whether it is or not. So I don't know whether to take "No RAID Disks" as me not using RAID or as me using RAID but somethings messed up.

I was thinking that maybe I should try formatting the drive in windows, just to be sure that it even works. That wouldn't hurt but I don't have access to a windows machine with SATA so I'm kind of stuck right now.

Thanks a lot for your help though guys, its good to know that I can actually count on getting responses from people on here. If anyone can think of anything else or lend any information that might help me I would greatly appreciate it.

---

