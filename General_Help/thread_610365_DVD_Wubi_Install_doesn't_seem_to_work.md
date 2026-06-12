---
title: "DVD Wubi Install doesn't seem to work"
date: 2007-11-11
forum: General Help
---

### Post by pwright2 on 2007-11-11
Posts: 69


View Profile Email Personal Message (Online) 	
	
No luck with DVD Wubi install
« on: Today at 09:43:15 pm » 	Reply with quote Modify message Remove message
I downloaded the Kubuntu 7.10 DVD.  Having problems with BitTorrent.  Excruciatingly slow.  Took 1 1/2 days.  DVD works, though.  Boots like a live-cd just fine.

As another message mentioned, there is a Wubi installer on the DVD readable by Windows.  I ran the installer and it did things and then told me to reboot.  Rebooting with the DVD in the drive resulted in a standard live-CD boot.  Without the DVD I do indeed get offered the alternative of a Wubi-Linux boot but selecting that gets me a failure stating it cannot find /ubuntu/something/wubiwinldr.??

(Yeah, I know, I should have written it down.  But I'm getting bored with rebooting.  Too much like windows.)

Then when I reboot into windows it informs me that Linux is already installed and do I want to uninstall it.

I discovered that the first time it had installed the files to my N: drive which is an NDAS network drive that would not be accessible at boot.  So I disconnected the N: drive and my two USB drives and reran the Wubi installer.  This time it installed to C: but I get the same results on rebooting as above.

Any ideas?

-----Paul-----

---

### Post by ago on 2007-11-12
The Wubi version that ships with the CD/DVD only allows to boot the CD (it's called "cdboot" for a reason) in order to help people booting without having to edit the bios.

I do not have DVD support at the moment, but I may add it in the future. Wubi works with CD DESKTOP ISOs.

---

### Post by pwright2 on 2007-11-12
Ah, well, that does explain some things not explained elsewhere.  So, shouldn't it be possible to copy the DVD to the hard drive and boot from that?  That would be useful.  Or, even better, to boot from the ISO.

-----Paul-----

---

