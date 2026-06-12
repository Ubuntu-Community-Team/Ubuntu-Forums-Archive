---
title: "Suitable cloning software to move Ubuntu 14.04 to another partition?"
date: 2014-11-08
forum: General Help
---

### Post by Mike_Walsh on 2014-11-08
Evening, everybody.

I need some advice about cloning software, and which would be the best to use.

My rather elderly workhorse, a 10-yr old Compaq Presario desktop, is getting to the stage where the main hard drive (a Western Digital Caviar 'Black' IDE drive, of 160 GB capacity), has been making some rather odd noises for the last few months.

It doesn't happen on initial start-up, but after the system has been in use for a couple of hours, it begins to make what I can best describe as a 'whooshing' noise, every couple of seconds. It will do this for hours; any period of hard disk use will cause the sound to disappear temporarily, whereupon, after the hard drive has finished doing whatever I've asked it to do, it will resume this same pattern again.

It still performs perfectly well; it belonged to my sister until January this year, when it was 'gifted' to me......with XP installed, and approaching EOL, she had bought a new desktop with Win 7 installed. I installed Ubuntu 14.04 in May, and have been using it ever since.....the drive has only had the equivalent of about 5 years normal use in terms of hours, yet it's still 10 yrs old.

Now, replacing the hard drive is temporarily beyond my budget at the moment; I have an external Seagate USB HDD of 500 GB capacity, which is not much over 8 months old. It has a 200 GB NTFS partition at present ( a hangover from my XP days!), together with a 50 GB extended partition, containing an install of Lubuntu 14.04 with a swap partition.....and about 200 GB of unallocated space.

What I'm proposing to do is to clone my Ubuntu install to a new partiton on the Seagate (I shall enlarge the extended partition, and create two more logical partitions; one for Ubuntu, and one for my /home directory), and install GRUB to sdb itself; that way, if the 'Black' DOES pack up, I can move over to running it from the Seagate.

What cloning software is available for Linux, and what is regarded to be the best one to use.....especially for someone like myself, with not many months use of Ubuntu under his belt?

Any advice will, as always, be much appreciated. I'm not after lots of advice about replacing hard drives; I've done that enough times in the past to be 'au fait' with the pitfalls, etc. I merely wish to know what cloning software is available, and which one is the easiest to use. This is not something I've attempted to do before, and I've just got Trusty to the point where it's exactly how I want it..! 

By the way, am I right in thinking that the cloning operation will need to be carried out from a different OS.....that it can't be done from within Ubuntu while it is mounted?


Regards,

Mike. ;)

---

### Post by cariboo on 2014-11-09
I've used [Clonezilla]("http://clonezilla.org/") with great success for cloning partitions or entire hard drives for years

---

### Post by sudodus on 2014-11-09
> **Mike_Walsh said:**
> Evening, everybody.

I need some advice about cloning software, and which would be the best to use.

My rather elderly workhorse, a 10-yr old Compaq Presario desktop, is getting to the stage where the main hard drive (a Western Digital Caviar 'Black' IDE drive, of 160 GB capacity), has been making some rather odd noises for the last few months.

Are you sure it is the hard disk drive and not a fan making those odd noises?
> 
It doesn't happen on initial start-up, but after the system has been in use for a couple of hours, it begins to make what I can best describe as a 'whooshing' noise, every couple of seconds. It will do this for hours; any period of hard disk use will cause the sound to disappear temporarily, whereupon, after the hard drive has finished doing whatever I've asked it to do, it will resume this same pattern again.

It still performs perfectly well; it belonged to my sister until January this year, when it was 'gifted' to me......with XP installed, and approaching EOL, she had bought a new desktop with Win 7 installed. I installed Ubuntu 14.04 in May, and have been using it ever since.....the drive has only had the equivalent of about 5 years normal use in terms of hours, yet it's still 10 yrs old.

You can check the HDD's S.M.A.R.T. status regularly. Install ***smartmontools*** and run sudo smartctl (with options that you find in ***man smartctl***).
> 
Now, replacing the hard drive is temporarily beyond my budget at the moment; I have an external Seagate USB HDD of 500 GB capacity, which is not much over 8 months old. It has a 200 GB NTFS partition at present ( a hangover from my XP days!), together with a 50 GB extended partition, containing an install of Lubuntu 14.04 with a swap partition.....and about 200 GB of unallocated space.

What I'm proposing to do is to clone my Ubuntu install to a new partiton on the Seagate (I shall enlarge the extended partition, and create two more logical partitions; one for Ubuntu, and one for my /home directory), and install GRUB to sdb itself; that way, if the 'Black' DOES pack up, I can move over to running it from the Seagate.

What cloning software is available for Linux, and what is regarded to be the best one to use.....especially for someone like myself, with not many months use of Ubuntu under his belt?

Any advice will, as always, be much appreciated. I'm not after lots of advice about replacing hard drives; I've done that enough times in the past to be 'au fait' with the pitfalls, etc. I merely wish to know what cloning software is available, and which one is the easiest to use. This is not something I've attempted to do before, and I've just got Trusty to the point where it's exactly how I want it..! 

By the way, am I right in thinking that the cloning operation will need to be carried out from a different OS.....that it can't be done from within Ubuntu while it is mounted?

Yes, you can boot from

- a Clonezilla live CD/DVD/USB  drive, or

- an Ubuntu desktop install CD/DVD/USB  drive - 'Try Ubuntu' alias run a live session.

> 
Regards,

Mike. ;)

> **cariboo907 said:**
> I've used [Clonezilla]("http://clonezilla.org/") with great success for cloning partitions or entire hard drives for years

+1 I also use Clonezilla. But I'm not sure it is the best tool in this case.

-o-

1. ***If you want a complete backup, use Clonezilla and make a compressed image*** of the whole internal 'black' HDD. But that is only a storage of your installed system. It cannot run. In order to run it, you must restore it to a HDD of at least the same size as the original drive.

[s]2. Clonezilla can also clone the internal drive to the external drive. But that would overwrite it (everything stored there would be overwritten). I don't think you want that.[/s]

3. ***You can install a copy or clone of the installed system to the external drive***. In this case I would not recommend Clonezilla.

3a. ***rsync***

You can boot from an Ubuntu desktop install CD/DVD/USB  drive - 'Try Ubuntu' alias run a live session - and run ```
gparted
``` to edit the partitions to what you want. Then you can use ***rsync*** to copy the whole system (your root partition and other partitions if you have them).

```
sudo rsync -Havn source target
```

Read carefully the manual ```
man rsync
``` so that you understand what you do. Check carefully (with a small test directory) that the rsync command line is doing what you want, then run the whole thing as a dry run (with the n option), then remove the n option.

You should edit the file **/etc/fstab** in the target partition to use the new UUID of the root partition and swap partition (and home partition if you have one)

After that you need to install the grub bootloader with ```
sudo grub-install ...
``` See ```
man grub-install
``` and this link

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

It is not easy, but not very difficult either. I think you can make it :-)

3b. ***OBI***

Another option (that is reasonable at least if the installed system is not huge with a lot of private files (multimedia files etc)) is to use the ***One Button Installer*** and create a tarball of the installed system (it works only with systems contained in the root partition, not with separate home partitions). Then the One Button Installer can install the system anywhere, in your case into a partition in the external drive.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by Mike_Walsh on 2014-11-09
Thanks for the replies, guys.

@Cariboo; I looked at Clonezilla a few weeks ago; it looked AWFULLY complicated...kinda put me off (but thanks for the suggestion anyway)!

@sudodus; Hm. That's a fair old bunch to take in, and process! (Tricky when you're only firing on a coupla grey cells at the best of times...)

The noise is definitely not the fan; the entire cooling assembly has been out, cleaned up & overhauled recently, and the fan's running as sweet as a nut. The curious thing is, I've now realised, is this usually seems to happen when I'm on the 'net.....and more specifically, when I'm listening to streaming music stations; odd, that.

And before you ask, it behaves the same in Chromium, Chrome & Firefox...so it doesn't seem to be specific to one browser.

**********************************************************************************

I like the sound of this One Button installer. It would only be needed for installing the root partition, sda1, in any case. I made a backup of the entire /home partition a couple of days ago, as I've been considering this for a little while now; but I wanted to get some options from those more knowledgeable with these kind of procedures than I am!

Here's a shot of sda, and you can tell me if this OBI is feasible, please:-

[ATTACH=CONFIG]257842[/ATTACH]

What do you think? Is the current size of the system too large for OBI to work effectively? Would I need to shrink the partition down a bit.....or would it compress OK as it is?

Regards,

Mike.

---

### Post by sudodus on 2014-11-09
Did you check also the fan for the CPU? It could run faster, because the CPU is working harder (than idling) when you process multimedia. (Is it only music or music video clips?) It could also be noise because the HDD stores (buffers) streaming data.

10-11 GiB should be OK for the OBI to create a tarball. It may compress down to around 6-7 GB, so that you can have it together with the OBI system in an 8 GB pendrive, and definitely it would work well in a 16 GB pendrive. If you have no suitable pendrive, see this link with tips

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

In your case, prepare the external drive with two or three partitions:

1 - the root partition
2 - the home partition (that you transfer manually, for example with rsync). Preserve the ownership and permissions!
3 - maybe a swap partition, but it is probably a good idea to re-use (or share) the swap partition on the internal drive.

---

### Post by howefield on 2014-11-09
> **Mike_Walsh said:**
> @Cariboo; I looked at Clonezilla a few weeks ago; it looked AWFULLY complicated...kinda put me off (but thanks for the suggestion anyway)!

Hi Mike_Walsh, just another vote for Clonezilla, it does look complicated but really it is not, as long as you read each screen the defaults will most likely be all you need. Try browsing a couple of youtube videos which will give you the idea :)

You could also have a look at Redo Backup and Recovery as an alternative.

---

### Post by oldfred on 2014-11-09
I usually recommend new install, not sure if Clonezilla copies UUID or not, but if it does it will be an issue if restored partition is on same system.

New install will auto houseclean all the old log files, kernels and other 'stuff' that accumulates. You should do though housecleaning before copying if you do decide clone system.

You have to change UUID in new partition as system cannot have duplicate UUID. Then you have to edit fstab with new UUID and reinstall grub so it updates to use new UUID. Grub also has internal info on which drive to reinstall into by model/serial so that has to be updated and swap has internal data on UUID for hibernation.

You can just copy /home with rsync. An example is here on moving /home. If you do a new install, you do not have to edit fstab after copy, just use Something Else and include mount, but NOT format when installing.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Mike_Walsh on 2014-11-09
Thanks for the replies, everybody, Been playing about with Puppy Linux this afternoon, and to my great delight it works perfectly in my old Dell Inspiron 1100 lappie, from a nano flashdrive...I'm really chuffed about that!

@sudodus; The fan I referred to WAS the CPU cooler. It definitely needed an overhaul. I doubt it had been out since it was put together by HP, nearly ten years ago.....it still had the factory applied thermal patch between the CPU and the cooler unit. My poor old sister, due to constant house moving, and a husband who loves nothing better than DIY, has been living in an almost permanent building site for the last 15 yrs or so, and the cooler was clogged solid with brick dust, wood shavings, assorted crap, you name it, when I first got it 10 months ago. I'd been meaning to overhaul the cooler for ages, but only got around to it the other week.....life keeps getting in the way; you know how it is!

The fan never runs above a whisper on the Compaq, anyway.....I've always found AMD's run pretty cool, to be honest; this one certainly does....rarely gets above 40C. I hadn't thought about the buffering; it could be that, but I'm fairly used to the noises it makes by now....the old IDE PATA drives, mounted in a full-size tower, are NOT the quietest of beasts at the best of times!

@howefield; I'll bear that in mind, young sir! I may have another look at it, actually....when I first clapped eyes on it, page after page of text kinda put me off a bit, since I'd not long since started with Ubuntu; bit of a shock after 20 some-odd years of GUIs with MS! I'm getting more used to the text-based side of Ubuntu now....I'm a lot more confident in the terminal than I used to be.


Regards,

Mike.

---

### Post by mountainman70 on 2014-11-09
I dual boot W7 and ubuntu 14.04 and use Clonzilla to clone to spare HDDs. It is really simple once you do it.

Here is a tutorial on using Clonzilla:

[http://www.wikihow.com/Use-Clonezilla](http://www.wikihow.com/Use-Clonezilla)

---

### Post by Mike_Walsh on 2014-11-09
Well, well, well; there ARE a lot of votes in favour of Clonezilla.....it must have something going for it, then; that's all I'm going to say! 

I'd best dig out the CD I burned of it a couple of months ago; and have a look at mountainman's link to wikihow, and see what it's all about. I'll mark this as 'Solved' for now; thanks to everybody who's replied.....it's given me plenty to consider in the short-term. I'll report back, as & when I get the job done.

Cheers!


Regards,

Mike. ;)

---

### Post by sudodus on 2014-11-10
> **oldfred said:**
> I usually recommend new install, not sure if Clonezilla copies UUID or not, but if it does it will be an issue if restored partition is on same system.

New install will auto houseclean all the old log files, kernels and other 'stuff' that accumulates. You should do though housecleaning before copying if you do decide clone system.

You have to change UUID in new partition as system cannot have duplicate UUID. Then you have to edit fstab with new UUID and reinstall grub so it updates to use new UUID. Grub also has internal info on which drive to reinstall into by model/serial so that has to be updated and swap has internal data on UUID for hibernation.

You can just copy /home with rsync. An example is here on moving /home. If you do a new install, you do not have to edit fstab after copy, just use Something Else and include mount, but NOT format when installing.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Clonezilla is easy and straight-forward, when used for the whole drive, cloning or making a compressed image.

But Clonezilla is more difficult (but possible) to use, when operating on partitions, if you plan to move them, or in your case *Mike_Walsh*, you plan to make it run in another drive at another position in that drive. Then I think it is easier to understand what happens, when you use ***rsync***. (If you want to fix the UUID stuff automatically, use the ***OBI***).

---

