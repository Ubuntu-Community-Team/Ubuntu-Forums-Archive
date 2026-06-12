---
title: "Problem with Hardy ISO"
date: 2008-05-09
forum: General Help
---

### Post by saratchandra on 2008-05-09
I downloaded ubuntu 8.04 alternate CD using bittorrent. Checked the md5sum and it matched with the original one. So I wrote it to a CD and checked the cd for errors and it said my cd is corrupted. Tried it on another cd and gave me the same error. I mounted the iso in windows and checked the sums for individual files and it says 9 files could not be read and a few didn't match the md5 sums. Did the same in linux with no success. The md5 of the original iso is still matching with the official one. What is the problem exactly?

---

### Post by macaholic on 2008-05-09
That sounds like a burning problem, try using a different burner, or a different configuration, ie slower burning speed.

---

### Post by saratchandra on 2008-05-09
Its not a burning problem. I extracted the iso file and checked the md5sums of individual folders and a few of them did not match.

> \install\netboot\pxelinux.cfg\default 
ERROR: H:\.\install\netboot\pxelinux.cfg\default does not exists.
.\install\netboot\pxelinux.0 
ERROR: Checksum did not match.
.\pool\restricted\l\linux-restricted-modules-2.6.24\linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_amd64.deb ERROR: H:\.\pool\restricted\l\linux-restricted-modules-2.6.24\linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_amd64.deb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.24\nic-restricted-modules-2.6.24-16-generic-di_2.6.24.12-16.34_amd64.udeb ERROR: H:\.\pool\restricted\l\linux-restricted-modules-2.6.24\nic-restricted-modules-2.6.24-16-generic-di_2.6.24.12-16.34_amd64.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.24\nic-restricted-firmware-2.6.24-16-generic-di_2.6.24.12-16.34_amd64.udeb ERROR: H:\.\pool\restricted\l\linux-restricted-modules-2.6.24\nic-restricted-firmware-2.6.24-16-generic-di_2.6.24.12-16.34_amd64.udeb does not exists.
.\pool\main\l\linux\pcmcia-storage-modules-2.6.24-16-generic-di_2.6.24-16.30_amd64.udeb ERROR: H:\.\pool\main\l\linux\pcmcia-storage-modules-2.6.24-16-generic-di_2.6.24-16.30_amd64.udeb does not exists.
.\pool\main\l\linux\storage-core-modules-2.6.24-16-generic-di_2.6.24-16.30_amd64.udeb ERROR: H:\.\pool\main\l\linux\storage-core-modules-2.6.24-16-generic-di_2.6.24-16.30_amd64.udeb does not exists.
.\pool\main\l\linux\fs-secondary-modules-2.6.24-16-generic-di_2.6.24-16.30_amd64.udeb ERROR: H:\.\pool\main\l\linux\fs-secondary-modules-2.6.24-16-generic-di_2.6.24-16.30_amd64.udeb does not exists.
.\pool\main\l\linux\firewire-core-modules-2.6.24-16-generic-di_2.6.24-16.30_amd64.udeb ERROR: H:\.\pool\main\l\linux\firewire-core-modules-2.6.24-16-generic-di_2.6.24-16.30_amd64.udeb does not exists.
.\pool\main\x\xfree86-driver-synaptics\xserver-xorg-input-synaptics_0.14.7~git20070706-1ubuntu4_amd64.deb ERROR: H:\.\pool\main\x\xfree86-driver-synaptics\xserver-xorg-input-synaptics_0.14.7~git20070706-1ubuntu4_amd64.deb does not exists.

---

### Post by macaholic on 2008-05-09
That was my point... A burner can screw up and corrupt discs, and lose files in the process, that's why the checksums are there, adn that's why burners usually verify discs after they burn them.

---

### Post by hairfarmer88 on 2008-05-10
I think I'm having the same problem as Saratchandra.  I've tried different media.  Burning at different speeds.  Burning on different computers.  I have confirmed the initial downloaded ISO check out with the MD5.

The way I read Saratchandra's post he was checking the MD5's for the packages inside of the ISO before he burned that said ISO and was finding errors.  That would explain my problems when trying to install from this ISO.  I get errors about packages being corrupted.

Is there a bad ISO image of Ubuntu-Alternate-i386.iso out there possibly?

---

### Post by hairfarmer88 on 2008-05-10
OK maybe it is a burning issue.  I just tried using the ISO image in VMware workstation.  I was able to successfully test the CD.  And now and performing a install in VMware with that same ISO image, which is working correctly.

One of the burning errors I got was something about overburn.  It looks like that image is probably very close to the max size for a CD.  Are there packages I can remove to save some space to make the burn more reliable for me?  Perhaps language files or something?  I only need English personally.

Thanks.

---

### Post by Exsecrabilus on 2008-05-10
I tried doing this on CD also. 700 MB CDs, I'm assuming you guys are using?

Then I resorted to like 4.7 GB DVDs. It worked fine.

When you burn a disc with just a few MB left (since the .iso file is like 697 MB or something like that) it kinda gets hard and messy.
This is my theory, not proven or anything. But this has happened to me and I've dealt with it, so why not?

So use a DVD with more than 700 MB of space and it'll be guaranteed to work.

---

