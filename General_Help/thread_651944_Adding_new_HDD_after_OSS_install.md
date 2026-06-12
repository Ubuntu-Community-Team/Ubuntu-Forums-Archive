---
title: "Adding new HDD after OSS install"
date: 2007-12-28
forum: General Help
---

### Post by Ins3rtKoin on 2007-12-28
Hi there.

I've moved one HDD formatted as extended NTFS with stuff in it from one computer to another running Gutsy and although it shows up in the device manager(no partitions though) as dev/sdc plugged into the onboard ICH5 SATA controller along with another drive taking the first slot, I can't seem to be able to mount it.
Neither do fdisk and gparted list it and I have also attempted to manually add it to /etc/fstab with no success. Maybe I'm not doing it right. I've been following: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) as a reference.
The drive seems to be working fine. Under Windows it was auto detected straight away, and as I'm not really into Hardware configuration issues under Linux I don't really know how to proceed :confused: My next step might be emptying it and wipe the partition to see what happens but theres quite a lot to back up first :popcorn: :beer: :cigarette: :popcorn: :beer: :cigarette: :popcorn: ....... 

Any suggestions?
Thanks for your help.

---

### Post by ajgreeny on 2007-12-28
Have you got the disk jumpers set right?  Slave, master etc etc?  Worth checking, but it seems likely something like that as I would expect gparted to see it.

---

### Post by Ins3rtKoin on 2007-12-28
Yes, jumper looks all right. It's an IDE plugged into Abit's Serillell SATA adaptor ........

It's throwing some Buffer I/O errors on boot. Bah, screw it. i'll just wipe from Windows and we'll see how it goes from there.

Thanks anyway

---

### Post by Ins3rtKoin on 2007-12-28
Well, it looks line the Serillel SATA won't do the trick and the drive remains now as IDE, dunno why though.
It's showing up now and it seems to be up and running.

---

