---
title: "mounting external harddrive (NTFS)"
date: 2008-05-10
forum: General Help
---

### Post by Achilles124 on 2008-05-10
I am new with Linux and Ubuntu and I now have to get into some hard-core coding in order to get access to my external harddisk (NTFS-format).

when i plugin my external harddisk into my computer, Ubuntu cannot mount it. I get the following message:
$LogFile indicates unclean shutdown (0,1). Failed to mount '/dev/sdf1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.
Choice2: If you don't have Windows then you can use the 'force option for your own responsibility. For example type on the command line: mount -t nfts-3g/dev/sdf1/media/disk -o force.
Or add the option to the relevant row in the /etc/fstab file: /dev/sdf1/media/disk ntfs-3g defaults, force o o

I dont know about forcing but I looked on the net and I found the following Ubuntu-page about it:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-3c27b1fe906b037b438cebcdcdb702d0afa5bd3d]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-3c27b1fe906b037b438cebcdcdb702d0afa5bd3d")

the automatic way doesn't work so I come to the manual way:
I downloaded the ntfs-3g package for drivers and other tools (step1).

I found the names of the drives (step2):
/dev/sdf1
/dev/sdf2
/dev/sdf3

I made a copy of the /etc/fstab file.

So far so good but now encounter some problems caused by my lack of experience.

<your partition> /media/<mount point> ntfs-3g defaults,locale=en_US.utf8 0 0
"locale=en_US.utf8 0 0"...eh, what is that. Strange, is it about the version of Ubuntu that I use? What is it?

Almost there, but not quite.

---

### Post by danwood76 on 2008-05-10
You need to make sure you cleanly remove your hard disk.
Plug it into a windows box and safely remove it, then ubuntu will mount it automatically.

That is why you got the error in the first place, always safely remove or unmount the drive.

---

### Post by Achilles124 on 2008-05-10
okay, I will try that first.

ty for answering.

---

### Post by Achilles124 on 2008-05-14
I did what you told me and it worked. Ty again for answering, Danwood.

---

