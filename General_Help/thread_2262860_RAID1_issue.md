---
title: "RAID1 issue"
date: 2015-01-27
forum: General Help
---

### Post by nechen on 2015-01-27
Greetings!

I'd like to thank everyone who helped me with my SAMBA problem earlier. Unfortunatley I seem to have a new issue.

I decided to go from 13.10 to 14.04 LTS. I did a FRESH install and even unplugged all my HDDs except the SSD it was going on (I do this out of paranoia because back in my early days of experimenting with Linux installs I didn't understand how hard drives were labeled and inadverntently wiped the wrong hard drives and messed a whole lot of stuff up)

Anyway now I have it running everything is going nice and smooth except my Hardware 1TB RAID1 Array seems absolutely hoses.

Back in 13.xx I had a SINGLE drive. Now for some reason I have two and they're not "keeping up with eachother." Basically any changes made to #1 doesn't take effect to number two. I have no idea what is going on what I need to do to fix this but I'm afraid of losing some very important documents and family photos, etc...

This is the dir of my /media folder where the drives are mounted. I have never seen this before in my dealing with Ubuntu. 

> 
ghost@ghostnix:/media/ghost$ dir
c31e4e15-19b6-4bc9-a533-70278973061d  c31e4e15-19b6-4bc9-a533-70278973061d1
ghost@ghostnix:/media/ghost$



I basically have two drives and I have no idea why. Even checking them in Gparted I have:
[B]/dev/sda (931.51GiB)
and
/dev/sdb (931.51GiB)

[/B]I know for a fact this means I have two drives, but I don't understand how this is possible on a Hardware RAID1?

Any insight would, as always, be greatly appreciate. Again, sorry for the n00bness. I just hope I can relay the wisdom I gain here to fellow converts in the future :p

---

### Post by SeijiSensei on 2015-01-27
Apparently the hardware RAID isn't running.  I'd start by checking the BIOS on the RAID card.  Usually there's a key you can press during bootup that will let you enter the RAID controller settings.  If you need to reset the configuration, just make sure that the drive that has all the new data is marked as the primary, so the other drive will mirror it.

Most hardware RAID devices present a single device to the operating system.  A Dell PowerEdge I manage uses a SAS card and came configured as RAID1 from the factory.  When Linux was installed, it saw the device as /dev/sda.

---

### Post by nechen on 2015-01-27
It's not a raid card, just onboard raid on an Nvidia 650i motherboard. 

It recognizes it as a Health RAID1 config. If I do anyting to it won't it wipe the data?

And why would this happen when they were disconnected during a fresh OS installed? I'm trying to figure out if this is a software/OS issue or a hardware issue...

I hate to sound like an end user by saying "It was working fine before" but I'm just totally confused.

---

### Post by SeijiSensei on 2015-01-27
That's a so-called "[fake RAID]("https://help.ubuntu.com/community/FakeRaidHowto")" device, one that requires a driver in the operating system to support it. Apparently you had this driver before, but probably now you do not.  That FakeRaidHowto is really out-of-date with no information on releases since 10.04.  From reading [this document from Arch](https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID), it looks like you need to use the "dmraid" tools during installation.  I don't see any comparable recent documentation on how to do this in Ubuntu.  Do you remember doing anything special when you installed 13.10?

If you can back up the array to another device, I suggest you replace the fakeRAID scheme and just use Linux software RAID instead.  Back up the currently active drive, probably /dev/sda.  Now use mdadm to combine the two drives into a single RAID1 array.

---

### Post by nechen on 2015-01-28
> **SeijiSensei said:**
> That's a so-called "[fake RAID]("https://help.ubuntu.com/community/FakeRaidHowto")" device, one that requires a driver in the operating system to support it. Apparently you had this driver before, but probably now you do not.  That FakeRaidHowto is really out-of-date with no information on releases since 10.04.  From reading [this document from Arch]("https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID"), it looks like you need to use the "dmraid" tools during installation.  I don't see any comparable recent documentation on how to do this in Ubuntu.  Do you remember doing anything special when you installed 13.10?

If you can back up the array to another device, I suggest you replace the fakeRAID scheme and just use Linux software RAID instead.  Back up the currently active drive, probably /dev/sda.  Now use mdadm to combine the two drives into a single RAID1 array.



Sadly I did nothing but use UNetBootIn to burn the Ubuntu 13.xx ISO and install it. That was it. 

Literally in order:

1.) Set SATA/Integrated Peripherals from IDE to RAID in the BIOS and save+exit
2.) Hit the F2 key to go into the "NVIDIA" RAID config
3.) Stripe both 1TBs of identical model#'s
4.) Boot to USB
5.) Install Xubuntu 13.xx

And  wham-O it was fine. Is it possible I didn't select something I SHOULD  have during the 14.04 install? If so I'd like to figure out what it was.

At  any rate I have a spare 1TB floating around I can back up the docs to.  However, I'd feel more comfortable having a nice stable PCI RAID card  installed. 

Can you recommend any good, solid, simple RAID cards  that aren't prone to failure/firmware problems? I'm just needing it for  RAID1 w/ (2) SATA Ports.

Thanks again for all your help!

---

### Post by nechen on 2015-01-28
Actually this just occurred to me..

If I had the TWO HDD's that were part of the "Fake RAID1" during the install wouldn't that have resulted in two separate drives since they weren't "merged" during installation as a single drive?

---

### Post by mastablasta on 2015-01-28
from the fakeraid wiki article posted above: > Linux, which has built-in softRAID functionality that pre-dates these devices, the hardware is normally seen for what it is -- multiple hard drives and a multi-channel IDE/SATA controller.  Hence, ***fakeRAID***

just use software raid. also RAID is not a backup. it's a disk redundancy. e.g. if you get corrupted data on one disk, it will be corrupted on both. if you accidentaly overwrite on one disk you will overwrite it on the other as well.

---

### Post by nechen on 2015-01-28
> **mastablasta said:**
> from the fakeraid wiki article posted above: 

just use software raid. also RAID is not a backup. it's a disk redundancy. e.g. if you get corrupted data on one disk, it will be corrupted on both. if you accidentaly overwrite on one disk you will overwrite it on the other as well.


Yeah I just did some reading up on it. Also, if someone wants to correct me, it seems HARDWARE RAID cards are quite a bit of $$

Anyway I had to do a fresh install because I had my 1TBs disconnected DURING install so once it completed it literally saw them as two hard drives. I've never felt dumber than I do now. 

At any rate I have Xubuntu 14.04 working like a charm and a SINGLE 1TB Volume mounted. I was already aware of how striping was just disk redundancy and not backup. I dunno I guess it gives me a warm fuzzy feeling to have a spare tire.

SO the lesson for today is remember to have your actual hard drives that are part of your RAID array PLUGGED IN during install kiddies!

_nechen

---

