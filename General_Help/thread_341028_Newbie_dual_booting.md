---
title: "Newbie dual booting"
date: 2007-01-18
forum: General Help
---

### Post by DiJEH on 2007-01-18
Okay so I've decided I need photoshop back and hence I'm dual booting in a few hours (if all goes well).

Now I'm just double checking on something here to make sure I have everything right.

I have the Ubuntu 6.10 desktop ISO ready to burn. This is the correct one I need right? I have a Dapper Live CD set next to me incase, but I figure may as well go up to Edgy now I'm here.

Obviously a Windows CD/DVD/whatever and key.

Now I've checked over partitioning tutorial but don't seem to be getting any where. So what exactly is a good partitioning set up where both Ubuntu and Windows can access the main HD Content?

And just so I have everything in order a quick "yes or no" to if this is right.

Install Windows
Shut down PC
Start Install Ubuntu 
Select partitioning
Tell it to partition and keep Windows partition/make it's own part
???
Profit (sorry, too much slashdot).

Everything in order?

---

### Post by PrinceArithon on 2007-01-18
I find it easier to do it this way

Install Windows
partition it with 2 partitions
one large enough to install windows and some programs on
and one large one that you will turn into a Fat 32 file later
leave freespace large enough to install Ubuntu and programs on
shut down pc
boot up and install Ubuntu
Tell Ubuntu to install on largest area of free space

And there you go.  After that go into Windows, and right click on that large partition go to format and format it as Fat32.  After that all you have to do is configure Ubuntu to see that Fat32 partition and you can save both your windows and Ubuntu files on there.

---

### Post by bodhi.zazen on 2007-01-18
How big is your HD ?

I would partition first, from the Ubunt desktop CD

Windows 15-20 Gb

Ubuntu root partition 15 Gb

swap ram X2, mak 1 Gb

Rest Data partition, FAT or Ext3

Install windows into a primary partition
Then install Ubuntu
go ahead and install grub into the MBR when you install Ubuntu :p

---

### Post by DiJEH on 2007-01-18
> **bodhi.zazen said:**
> How big is your HD ?

I would partition first, from the Ubunt desktop CD

Windows 15-20 Gb

Ubuntu root partition 15 Gb

swap ram X2, mak 1 Gb

Rest Data partition, FAT or Ext3

Install windows into a primary partition
Then install Ubuntu
go ahead and install grub into the MBR when you install Ubuntu :p

80 gigs

---

### Post by bodhi.zazen on 2007-01-18
Windows 15-20 Gb
Ubuntu root partition 20 Gb
Swap 0.5-1 Gb
Data partition 40 Gb

You can tweak the #'s if you wish, use mine as a guide line ....

You can do a separate /home if you wish, but you can save all your data on the data partition like this:

[http://ubuntuforums.org/showthread.php?&t=300246](http://ubuntuforums.org/showthread.php?&t=300246)
	[indent]Posts # 10 and 13[/indent]

Install Windows
Install Ubuntu
[indent]give the data partition a mount point at Ubuntu install. /mnt/data ; /media/data ; what have you[/indent]

If you go with ext3 for your data partition you will need this:

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by DiJEH on 2007-01-18
> **bodhi.zazen said:**
> Windows 15-20 Gb
Ubuntu root partition 20 Gb
Swap 0.5-1 Gb
Data partition 40 Gb

You can tweak the #'s if you wish, use mine as a guide line ....

You can do a separate /home if you wish, but you can save all your data on the data partition like this:

[http://ubuntuforums.org/showthread.php?&t=300246](http://ubuntuforums.org/showthread.php?&t=300246)
	[indent]Posts # 10 and 13[/indent]

Install Windows
Install Ubuntu
[indent]give the data partition a mount point at Ubuntu install. /mnt/data ; /media/data ; what have you[/indent]

If you go with ext3 for your data partition you will need this:

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

Not quite sure which 10 and 13 are. Maybe I'm just tired but could you link me directly to them?

---

### Post by bodhi.zazen on 2007-01-18
LOL, sorry about that.

I was referring to my posts # 10 and 13 in the thread.

Here they are:

[http://ubuntuforums.org/showpost.php?&p=1762199&postcount=10](http://ubuntuforums.org/showpost.php?&p=1762199&postcount=10)

[http://ubuntuforums.org/showpost.php?&p=1763453&postcount=13](http://ubuntuforums.org/showpost.php?&p=1763453&postcount=13)

---

### Post by DiJEH on 2007-01-18
> **bodhi.zazen said:**
> LOL, sorry about that.

I was referring to my posts # 10 and 13 in the thread.

Here they are:

[http://ubuntuforums.org/showpost.php?&p=1762199&postcount=10](http://ubuntuforums.org/showpost.php?&p=1762199&postcount=10)

[http://ubuntuforums.org/showpost.php?&p=1763453&postcount=13](http://ubuntuforums.org/showpost.php?&p=1763453&postcount=13)

Well THAT went well.

Step 1 : Insta... no wait power cut. Long *** nap instead.

Step 2 : Install windows
Step 3 : reboot
Step 4 : Recieve this.

[IMG]http://i49.photobucket.com/albums/f300/Astrayoutframe/Windowsproblem.jpg[/IMG]

Step 5 : ???

Currently I'm running Edgy (full installed). I'm guessing I can resize the ubuntu partition and then install Windows in the empty part (it was an option in the Windows installing process). What do you think?

I tried to wipe and reinstall windows but  just ended up in a rebooting cycle over and over. It would start to boot, reboot and repeat in an infinite loop of XP loading screens

---

### Post by khedron on 2007-01-18
On Googling, this paragraph is wrong. GRUB corrects the described problem. ((* If you do, make sure that you resize from the front, as Windows needs to be partition #1, although I'm not sure whether that refers to being the first partition or the oldest partition. It's possible that this is what is going wrong for you. *))

Personally, if I were going for a clean install of both OSs, I would manually create partitions during the Ubuntu installation and leave enough unpartitioned space for Windows at the front, then install Windows, then boot the Ubuntu Live CD and reinstall Grub. I didn't find partitioning that hard to do, and if you can't work out which partitions should be where during that stage, you can just click cancel. The installer won't write to the disk unless it has explicitly asked you.

---

### Post by DiJEH on 2007-01-18
It's not about resizing, it's that Windows nose dives and I have no idea why :/

---

### Post by bodhi.zazen on 2007-01-18
See [here](http://farm.tucows.com/images/2006/06/data_bsod.gif) for [color=blue]blue screen of death[/color].

What is your partition table exactly ?

And what was > Step 1 : Insta... no wait power cut. Long *** nap instead.Power outage ? During the windows install ?

Is your windows install CD working ?

---

### Post by DiJEH on 2007-01-18
Yea, it just booting down after formatting the HD. The weather here is terrible and the entire village went out :(

My partition table is currently nothing. I just did a full clean Edgy install.

---

### Post by strabes on 2007-01-18
Partition your disk with the windows CD with two partitions: 1 as ntfs which you will install windows on. It should be 15-20 gigs NTFS, that's it. The other partition don't format as anything. Once windows is done installing on the ntfs partition, boot into the ubuntu live CD, and create three partitions. A 15-20 gig ext3 one to install ubuntu on, a 2 gig one for swap, and the rest of your harddrive as the last one, a fat32 one, for data storage that can be read/written by windows and linux. Once this is done, you should select the appropriate mount points for the ubuntu install partition (preferably sda2/hda2), the swap (preferably sda3/hda3), and the data partition (preferably /media/data). It's easier to mount it during the install than to mount it manually once ubuntu is installed.

So to review, your 80gig hard disk should look like this in the live cd gparted partitioner:

15 gigs - NTFS windows /dev/sda1, not mounted in linux
15 gigs - ext3 ubuntu /dev/sda2, mounted as /
2 gigs - swap /dev/sda3, mounted as swap
48 gigs - fat32 /dev/sda4, mounted on /media/data

Don't bother mounting the ntfs partition in ubuntu.

---

### Post by bodhi.zazen on 2007-01-18
swap = 1 Gb

2 Gb is almost certainly overkill

---

### Post by DiJEH on 2007-01-18
It probably is but hey it's only a gig at the end of the day.

I'm on my other box and trying to dual boot my main box now. Installing windows.

I made 4 partitions. 2 15000mb, 1 2000 mb and the final one is everything left. Now just to wait and hope.

---

### Post by DiJEH on 2007-01-18
Okay, I tried again and the same problem. It bluescreens. I did notice the last thing it loads before it dies is Mup.sys

any ideas?

---

### Post by bodhi.zazen on 2007-01-18
Add this to the Windows is easier then Linux thread :p

I do not know what the problem is with windows, well I do but it does not help us right now :D

What I would do is change tactics ...

Install windows, give it the whole HD

Boot windows, make sure it is happy, defragment ....

Now boot Ubuntu, downsize and re-partition you HD as above (swap 1 Gb, geeze I can recall when a 4 Gb HD was considered HUGE, only 1 Gb indeed :p Anem, anyways, ..)

Install Ubuntu

Install Grub to MBR

---

### Post by DiJEH on 2007-01-18
> **bodhi.zazen said:**
> Add this to the Windows is easier then Linux thread :p

I do not know what the problem is with windows, well I do but it does not help us right now :D

What I would do is change tactics ...

Install windows, give it the whole HD

Boot windows, make sure it is happy, defragment ....

Now boot Ubuntu, downsize and re-partition you HD as above (swap 1 Gb, geeze I can recall when a 4 Gb HD was considered HUGE, only 1 Gb indeed :p Anem, anyways, ..)

Install Ubuntu

Install Grub to MBR

That would work if not for that fact that a straight Windows install beings up said error too.

---

### Post by bodhi.zazen on 2007-01-18
> **DiJEH said:**
> That would work if not for that fact that a straight Windows install beings up said error too.

Thus proving once and for all how easy Windows really is :p

Did you give the entire disk to windows (delete ALL OTHER partitions for now).

If so, looks like you may have a bad windows install disk :(

Ouch ...

---

### Post by DiJEH on 2007-01-18
> **bodhi.zazen said:**
> Thus proving once and for all how easy Windows really is :p

Did you give the entire disk to windows (delete ALL OTHER partitions for now).

If so, looks like you may have a bad windows install disk :(

Ouch ...

To Sealand!! erm wait.. damn it they arn't there yet :)

I thought that maybe it.

As for the windows is easier.. I switched to Linux because Windows wouldn't run the hardware I was using (netgear network cards), but Ubuntu did out the box :)

---

