---
title: "Ubuntu HD on Secondary IDE channel"
date: 2006-11-10
forum: General Help
---

### Post by mark2741 on 2006-11-10
I just realized while booting up the other day that my PC is all wacky. I have felt that my Ubuntu seemed to run kind of slow for some time, but I just figured that was because my hardware is getting up there in age:

P4 1.7ghz
512mb RAM

I have a 7200rpm, 200gb hard drive, an 80gb 7200rpm drive, and a DVD burner.

Of the 2 IDE channels in my PC, here is how they are configured:

IDE 0: Master: None   Secondary: DVD Burner
IDE 1: Master: WinXP HD  Secondary: Ubuntu HD

It's been like this for a long time, probably since I installed the DVD burner. I have a *very* small case with little room, which is probably how it got this way int he first place. I know that normally you want the primary boot disk on the IDE0: Master channel, but back then I wasn't sure if I'd be sticking with Ubuntu or not. Well, that was back in summer of '05 and I'm at a point now where I rarely boot up Windows.

So, will changing to configuration like this:

IDE 0: Master: Ubuntu HD
IDE 1: Master: Windows HD, Secondary: DVD Burner

Make my system faster? More importantly - will changing the IDE cables around screw up Windows XP, Ubuntu, or the boot loader that dual-boots them? I know linux has an hda, hdb, hdc etc thing going and so I'm worried if I change the cabling that I won't be able to reboot.

---

### Post by koenn on 2006-11-10
i don't think it's worth the trouble. 
It will probably don't make the system any faster. WinXP an Ubuntu will never run at the same time, and DVD is on an other controller, so there's nothing to gain (IMHO). 
Swapping disks will mess up the system:
1- with a HD master on IDE channel 1, BIOS may expect to find MBR/Boot loader there unless you change BIOS boot settings
2- hdd will become hda so /etc/fstab needs updating or you won't see any files, and probable won't be able to boot linux
3- Windows might expect a C: partition on master at channel 1, so you risk WinXP won't boot either
4- boot loader wil probably be pointing to wrong disks/partitions

However, you might still want to go ahead (having your OS master of first IDE channel feels cleaner), and take the oportunity to improve performance by
- partition the disks : seperate partitions for /boot, /, /var, /home, ...
- sufficient swap space - possible with multiple swap partitions on 1 or both disks

---

### Post by kidders on 2006-11-10
I agree with koenn. Jumbling your cables around will have no effect on performance ... just in case a second opinion is useful! lol.

It does seem odd not to use as many physical disks as you can at the same time though. *That* would boost performance. Why are Windoze and Ubuntu on separate devices?

---

