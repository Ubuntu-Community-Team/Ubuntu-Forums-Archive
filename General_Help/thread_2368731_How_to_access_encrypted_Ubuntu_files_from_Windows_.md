---
title: "How to access encrypted Ubuntu files from Windows 10?"
date: 2017-08-14
forum: General Help
---

### Post by jotar910 on 2017-08-14
[COLOR=#242729][FONT=Arial]Hi, I had dual boot Windows 10 and Ubuntu on my computer, but I didn't liked ubutu OS so I uninstalled it. The problem is that when I copied all the files to an usb drive, I copied it encrypted. Now that I want to access the files on windows 10, I can't do it. If you have a solution please help me! 
Thank you.[/FONT][/COLOR]

---

### Post by TheFu on 2017-08-14
How was it encrypted?  That would normally be either eCryptfs or dm-crypt w/ LUKS.

Do you have unencrypted backups?  Whenever any encryption is used, having great backups is mandatory.

I don't know of any method for non-Linux systems to access dm-crypt storage. If you installed it with whole drive encryption, accessing the dm-crypt partition is just the first hurdle, usually, inside that will be LVM with physical volumes, volume groups and logical volumes.  These make the storage extremely flexible. But harder to access for the non-expert from outside.  I don't know of any method inside Windows to gain access to storage setup in this way.  That doesn't mean it isn't possible, just that I've never seen a tool that supports all the different layers necessary ...

* dm-crypt
* LVM partitioning
* ext4 (or other Linux file system)

If you really, really, really, want to get to the data, you can run a live-boot Linux, manually install the necessary tools , then manually open the dm-crypt storage, manually open the PV, VG, and LV parts of the LVM, and manually mount the LV to gain access.  It is a hassle - I've done it a few times in the last few months.  When I got it down pat after the 3rd time, it took me about 3 minutes to get to my data.  The first time was about 30 minutes.  I'm not new to Linux and have been using dm-crypt and LVM for years.  NONE OF THIS IS POINT-N-CLICK and every option, for every command, has to be well understood.

---

