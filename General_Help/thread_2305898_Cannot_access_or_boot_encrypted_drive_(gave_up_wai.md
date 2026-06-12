---
title: "Cannot access or boot encrypted drive (gave up waiting for root device...)"
date: 2015-12-10
forum: General Help
---

### Post by David4321 on 2015-12-10
I cannot access or boot from my C drive. I'm running Zorin 9 and the drive is a Samsung SSD. The disk was encrypted on install, and that has not given me any problems before.


When I start the system it gets to the memory test page, and does not then load the password prompt, which it used to. I can go to password manually by pressing "Enter (Boot)", but it does not accept correct password. I have tried cap lock. I know keyboard is good, I have tried wired and wireless keyboards. I checked the disk recently with GSmartControl, and it passed with no comments. Upon attempting password I get "cryptsetup failed". After several attempts I get an error "gave up waiting for boot device". [http://bluelight.us/files/20151209_172715.jpg](http://bluelight.us/files/20151209_172715.jpg)


When plugged into windows externally, this drive with the data I want doesn't show up in the drive list as searchable, but it does show up in "safely remove hardware", and in drive management. In drive management, it shows as 2 partitions, both reporting as healthy, one at 243mb, the other at 232.65gb. The drive is formatted to ext2, and with windows drivers, the smaller partition (with grub) displays in drive list, but not the data partition, formatted to raw.


Questions:
1) Does this seem most likely to be a software or hardware problem?
If a software problem:
2) I noticed that it lists the OS it is looking for as being on sda5_crypt, not sure how there could be 5 partitions on that device (it's only 250gb) unless that is part of the encryption protocol. I never noticed the partition designation before, the only thing I put on that drive is the OS, I never manually created any other partitions. Could it just be looking for the wrong partition? Is there a way to check this?
3) Is there a way to repair the boot sector, change the encryption key, or reinstall the OS from DVD without booting up, AND preserve all existing personal data? (fortunately, there's not that much on this drive)
4) I've been thinking of moving from Zorin to Ubuntu OS anyway, and my first thought was that this is an opportunity for that. Is there a way to install Ubuntu and preserve the data?
If a hardware problem:
5) Is there a way to back up and salvage the encrypted data on this disk?

Thanks for any help!

---

