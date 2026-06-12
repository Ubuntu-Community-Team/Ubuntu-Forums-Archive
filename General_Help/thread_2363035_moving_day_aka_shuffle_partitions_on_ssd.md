---
title: "moving day aka shuffle partitions on ssd"
date: 2017-06-05
forum: General Help
---

### Post by Kris_M on 2017-06-05
I tried to paste a pic of gparted of my ssd but Chromium won't display all of the manage attachments box <--- help1
(used FF to add it. :(

I have a 225GB ssd with ubuntu, swap, and 2 ntfs partitions on it. (sda5, sda6)

I will use gparted to "copy" these partitions to a spindle. Already modified fstab to account for one (comment out).

My ubuntu is sda7 so I suspect it will get renumbered when I delete sda5 and sda6 so grub probably won't find it so hopefully boot repair or rescatux will..? <-- help2

Then I will need to move my existing ubuntu partition down to the beginning of the ssd (it's all extended)

Purpose is twofold - want to leave half for 18.04.1 and at present need an extra 60GB in my 70GB ubuntu to to build for phone ROM.
Too cheap to part with $200 for 500GB ssd at the moment.

The room is there, but will I survive??? :D
Any halp/advice is appreciated!

---

### Post by oldfred on 2017-06-05
Is this a Linux only drive?

There are some advantages to gpt partitioning over the 35 year old MBR(msdos) partitioning even if still booting in BIOS mode.
I had XP on a MBR drive, but converted my small HDD with Ubuntu to gpt back in 2010.
Then with first SSD a year or two later used gpt, then when Windows converted to UEFI/gpt as standard, I included on all new/reformatted drives both the ESP - efi system partition for future use and the bios_grub required for BIOS boot. I still add both partitions as first two on all new drives even though now everything is UEFI.

My first SSD in 2011 was 60GB with two / (root) partitions. But all data on HDD.

       Oldfred's current partitions Dec 2015 (mine is an Asus Z97 in UEFI boot mode).
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

Grub2 uses UUID to boot, so changing partitions should not matter. Only in a few places are device like /dev/sda5 used.
But always best to have good backups & live installer to make repairs. I typically have Ubuntu live installer, Boot-Repair, gparted, Knoppix, parted rescue, Supergrub or Rescatux all as bootable ISO on a flash drive.

I do not like moving start of a drive as that more often can cause issues. And any interruption of move will totally corrupt data, or reason for good backups. Usually it does work. And you may need to reinstall grub.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by Kris_M on 2017-06-05
> **oldfred said:**
> Is this a Linux only drive?

There are some advantages to gpt partitioning over the 35 year old MBR(msdos) partitioning even if still booting in BIOS mode.
I had XP on a MBR drive, but converted my small HDD with Ubuntu to gpt back in 2010.
Then with first SSD a year or two later used gpt, then when Windows converted to UEFI/gpt as standard, I included on all new/reformatted drives both the ESP - efi system partition for future use and the bios_grub required for BIOS boot. I still add both partitions as first two on all new drives even though now everything is UEFI.

My first SSD in 2011 was 60GB with two / (root) partitions. But all data on HDD.

       Oldfred's current partitions Dec 2015 (mine is an Asus Z97 in UEFI boot mode).
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

Grub2 uses UUID to boot, so changing partitions should not matter. Only in a few places are device like /dev/sda5 used.
But always best to have good backups & live installer to make repairs. I typically have Ubuntu live installer, Boot-Repair, gparted, Knoppix, parted rescue, Supergrub or Rescatux all as bootable ISO on a flash drive.

I do not like moving start of a drive as that more often can cause issues. And any interruption of move will totally corrupt data, or reason for good backups. Usually it does work. And you may need to reinstall grub.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

While I very much appreciate your repeated efforts oldfred, I will not convert to GPT. I had a very very bad experience a while back with it owning my mobo and I had to completely start over to put a new mobo in there. I constantly change hardware (mobo etc) and need everything else to just ride along with that. No "ownership" idiocy. GPT will not do that. BIOS allows me to be a happy little moron swapping things in and out without a care in the world.

There is no windows left in my box but I have 2 NTFS partitions and I need to have those as NTFS as actually it is a lot easier to mindlessly share them between Linux systems (Ubuntu 16.04.2 and planned 18.04.1).

Again my profound thanks for sharing a tiny bit of your imense knowledge. Consider me just a tiny speck on the vastness of Ubuntu.

---

### Post by oldfred on 2017-06-05
I forget who I have tried to sell gpt on before, so sorry for repeated sales pitch.

If keeping NTFS, best to also have a Windows repair disk. I made a Windows 7 repair disk when I had XP, and never have had Windows 7.
But the Window 7 disk did a better job of running chkdsk than XP, but also broke XP boot and I had to fix that also.
NTFS will need chkdsk and you cannot run that from Linux.
Ubuntu used to run fsck every 40 or 60 reboots, but newer ext4 seems to self report issues so it is not automatic anymore, but also still required occasionally. Often power failure or abnormal shutdown causes file corruption no matter format. 

NTFS does not support ownership & permissions, so that is why it is easier to share.
I did use NTFS when still using XP, and when I shut XP down kept the NTFS until building a new system that then had no NTFS partitions.
And had to set ownership & permissions to get to to work. I use same settings for ownership & permissions as /home in my /mnt/data ext4 partition and have found that to work well.

One reason I like gpt, is that I never have had issues related to gpt. And in forums I see lots of users having to recover MBR(msdos) partitions and have no backups.

---

### Post by Kris_M on 2017-06-05
> **oldfred said:**
> I forget who I have tried to sell gpt on before, so sorry for repeated sales pitch.

If keeping NTFS, best to also have a Windows repair disk. I made a Windows 7 repair disk when I had XP, and never have had Windows 7.
But the Window 7 disk did a better job of running chkdsk than XP, but also broke XP boot and I had to fix that also.
NTFS will need chkdsk and you cannot run that from Linux.

Please stop telling people that - A win repair disk will destroy anything Linux on a drive..
Clonezilla is just fine.

> **oldfred said:**
> Ubuntu used to run fsck every 40 or 60 reboots, but newer ext4 seems to self report issues so it is not automatic anymore, but also still required occasionally. Often power failure or abnormal shutdown causes file corruption no matter format. 

That's precisely why I back up my ssd with Clonezilla at least once a week - whole disk to image. That wah if the ssd, or anything on it goes sideways, 10 min later I'm fine.

> **oldfred said:**
> NTFS does not support ownership & permissions, so that is why it is easier to share.
I did use NTFS when still using XP, and when I shut XP down kept the NTFS until building a new system that then had no NTFS partitions.
And had to set ownership & permissions to get to to work. I use same settings for ownership & permissions as /home in my /mnt/data ext4 partition and have found that to work well.

One reason I like gpt, is that I never have had issues related to gpt. And in forums I see lots of users having to recover MBR(msdos) partitions and have no backups.

Maybe sometime when I've got a week to spare and a different completely empty box, I'll try gpt. 

-----------------------------------------------------------

I have often heard things like gparted won't renumber partitions, and grub goes by uuid. [COLOR=#ff0000][SIZE=4]_**BOTH ARE FALSE**_[/SIZE][/COLOR].

But I knew that going into this and believed no-one.
I copied my 2 ntfs partitions up to another spindle and clonezilla'ed the ssd, 
and only then removed sda5 and 6. gpatrted of course promptly renamed sda7 and 8 to 5 and 6.

Okay so I played dumb and booted it - I knew it wouldn't boot but did this hopefully for the benefit of folks who say numbers don't change.
pic1 is gparted at present
pic2 is me looking at grub recover.  tell me - who memorized grub recover commands???  
so I fired up my laptop with win7 on it and googled for grub recover  commands. Good laugh!
The partition it was, it said was ext2. dumb!

So with tongue firmly planted in cheek (remember, I had a Clonezilla backup so nothing was lost.)
However I was now reminded that my Rescatux and BootRepair thumb drives both WILL NOT boot if my Nvidia 750 is connected as 1st display. So side trip to Bios to change peripheral first boot display and boot again while furiously replugging HDMI. 
Fine. Now into rescatux. tried the one labled "easy" and seemed to work fine.

Rebooted to Linux and it showed grub fine but enter password, screen flash, screen flash (all pretty colors!), enter password, repeat ad nauseum. 

Okay so maybe Rescatux didn't quite work so tried it again this time using a different "easy" All seemed well. but again reboot, reboot.

Finally realized this Ubuntu as it is set up won't boot with the Intel as primary display so back to Bios, back to reboot, and I'm fine.

------------------------------------------

There was another problem in there where gparted thumbdrive after using it a bunch gets an infinite bunch of io errors before loading but I will post that in a new thread.


And I still haven't repositioned Ubuntu on the SSD...  But Clonezilla again first!

I made a new thread for next steps.

---

