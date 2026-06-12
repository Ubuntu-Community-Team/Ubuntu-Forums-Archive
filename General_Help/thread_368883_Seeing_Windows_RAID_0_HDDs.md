---
title: "Seeing Windows RAID 0 HDDs?"
date: 2007-02-23
forum: General Help
---

### Post by Anelysium on 2007-02-23
Hello, I recently got the ol' blue screen o' death on my Windows setup: unmountable_drive_volume. The boot sector is corrupted, but I was told that I could most likely save the files by booting ubuntu and copying them onto another drive. The drives are both SATA in RAID 0 using the mobo. When I boot up Ubuntu 6.10 off the disk I see my floppy drive, cd drive, dvd drive, and 'File System' in "Computer", but not the HDDs. 

I'm new to Ubuntu, so I'm not sure if I should be able to see it, or if I need to do something more. I've looked around the forums, but either just missed something or was too dense to see it.

Also, if I choose to install Ubuntu, it gives me the option of installing it on either of the 160gb HDDs.

Any help would be greatly appreciated, thank you.

---

### Post by ofek on 2007-02-23
The wiki is your friend and so is the forum search ill give u the first clue and u will probably handle from there: [Clue =)]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29%7C%28windows%29#head-fb8716b5d667b443f5dda66c63dd39375260a9d9")

---

### Post by chalex on 2007-02-23
Hey Anelysium, what disk controller is that on your motherboard?  Since you're using onboard RAID, you probably want to look at using the "dmraid" driver for Linux which can understand the fakeraid on your mobo.

Using the dmraid driver you should be able to see the array.

Also, you probably shouldn't be using RAID-0 unless you have a REALLY good reason and a reliable backup system.

---

### Post by Anelysium on 2007-02-24
The RAID controller is Silicon Image. I looked up dmraid, I'm just having a hell of a time figuring it all out, I've never really used linux, heh.

I understand the use of the terminal, I have the RPM files for dmraid, I just don't know what to do with them.

---

### Post by der_joachim on 2007-02-24
RPM will not help you my friend. The good news is that dmraid is in the repositories. A *sudo aptitude install dmraid *will do the trick. The bad news though is that you'll have to install Ubuntu first on a hard drive, which you do not want to do on one of your disks. :( 

IIRC, most motherboard RAID controllers are so-called fakeraid controllers. Search the Ubuntu wiki for fakeraid configuration.  

I do not know anmything about recovering from a livecd though.

---

