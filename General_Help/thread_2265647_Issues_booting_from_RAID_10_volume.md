---
title: "Issues booting from RAID 10 volume"
date: 2015-02-16
forum: General Help
---

### Post by mc1175 on 2015-02-16
Hi all,

I'm a bit new to ubuntu, but not new enough from a techie standpoint to say I'm a noob per-se (I come from Windows, I mean no harm). Basically I've been having issues with this one Server/workstation for the last few weeks and its been driving me absolutely insane. For the sake of the story, I'm my living group's IT guy.  The machine is a Dell Precision 690 originally running Windows repurposed to run Debian as a media server, website host and psuedo security system for our home's doors (using Arduinos, not pertinent to the story but this server used to be near essential to our house's security, which was a dumb idea from the beginning). 

Here comes me, naive, foolish mc1175 thinking I could simply fix a problem with a raid system. How wrong was I...

I come across this machine when I moved into the living group. A few weeks after I got there, people were reporting the website was offline and that the door system was doing some weird things. That's my cue to check out the server, and the beginning of the nightmare that I self-selected myself to be a part of. 

I try booting and pretty quickly get to a screen that gives me the message...

error: no such disk
grub rescue>

Alright, so there's some issue preventing me from booting. Not something I haven't come across before, and not too hard to get around, or so I thought. I find out pretty quick that one of the drives is causing the issue. It must have failed after continual use for months, maybe years consecutively. Normally this wouldn't cause a problem because the system is RAID 10, one set of drives should still be working, and as far as I can tell that is still true. So I try using the boot menu to choose a different drive, and it gives me the same message. Sometimes it throws me to BusyBox (initramfs) depending on which drive I pick, or if I modify BIOS settings like the SAS controller. At this point I was just trying to get *something *to work. I create a usb live CD with Ubuntu 13.04 installed to get a better look. Boot repair did nothing as I could tell, and I looked at the partitions using fdisk -l and found one of the partitions was down. I tried to mount the drive or assemble the raid with no luck (may not have done it right). This was a few months ago so my recollection of this is a bit spotty, but somehow I was able to go back to the boot menu, select a drive and get the Debian boot menu (with standard boot and recovery options). It actually boots, and I start to check out the files. The stuff is intact so I take a few backups trying to save the info. I get most of what I need but end up missing a few important documents. I leave the machine on because it still works and I'm sure rebooting will cause the problem again. 

I come back the following week and the machine is back where we started. Tried everything from before to regain access to the data but nothing is working. I can get to the debian menu and edit the kernel options for bootdegraded=true but it makes no difference. It spits a couple of notices saying only 3/4 metadata found and still asks if I want to boot degraded [y/n?]. It ignores me when I type y then dumps to initramfs. Can't exit busybox. 

Are there any commands I can use to rebuild the raid from within the live cd? I don't know much about mdadm but I tried a few things with no luck. Do I need to update grub or edit the boot information? 

Is there any way I can recover this blasted system?

Thanks in advance, I've been working on this system for an accumulated 30 hours and I could use a miracle right now. If there is another place to post this let me know, the repair isn't time sensitive but I'd like to get as much help as possible.

- mc1175

---

