---
title: "Z77 RAID5 array does not show in Ubuntu"
date: 2015-02-23
forum: General Help
---

### Post by John_Demco on 2015-02-23
Hello fellow Linux users!

I have a selfbuild NAS running Ubuntu 14.04 which I use for local filesharing, uploading files and multimedia processing. It has samba for sharing files on my LAN.

The specs:
Gigabyte Z77X-UP4 TH
Intel i7 3770 LGA1156
8GB Corsair Vengance DDR3 RAM
Startech 4-port SATA-expansioncard PCI-e

For Storage I have:
3x WD RED NAS 3TB
2x Seagate 3TB
3x Misc 1TB drives

I went to my BIOS and chose "RAID" and after reboot I went to the "Intel Rapid Storage Technology" BIOS. Before hand I made sure my 3 WD RED drives were on the same chipset and they were wiped clean. Back in the IRST BIOS I chose RAID5 and 64KB stripe block size. I confirmed my settings and created the RAID-array. After a reboot and Im back in Ubuntu but when I check Disk's I see all of the drives as individual drives. On one drives it says "3.0 TB IMSM RAID Member (1.3.00)" and the other two appears as regular mountable HDD's

So what could be the problem? I've been googleing for the past three hours but with no luck....

Your help is greatly appreaciated and will be looking forward to your opinion!
Thnx

John Demco

---

### Post by oldfred on 2015-02-23
I do not know RAID, other than there are a lot of different versions. 

ISRT uses its own RAID configuration. Not sure if that is the normal "FakeRAID" or BIOS RAID or not.

       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

      
Many prefer using Software RAID or Linux RAID as then it is not dependant on any specific hardware. When hardware fails (When not if) then you can use different hardware but same software. With hardware RAID you really want another set of the RAID or motherboard for redundancy. 

 [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by oldos2er on 2015-02-23
Moved to General Help.

---

