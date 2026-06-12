---
title: "Fail to boot into Windows 7 after installation of Xubuntu."
date: 2014-07-12
forum: General Help
---

### Post by zra on 2014-07-12
Hey Ubuntu forums!

First of all, I shrinked my SSD partition from Windows 7, shat off the computer and booted Xubuntu installation from an 8GB usb.
I installed Xubuntu along with Windows 7 on different partitions but on the same HDD. It gave me an error that was critical, that it couldn't place the boot sector, I placed it manually on SDA2( i think it was called that)
I rebooted the system, and I could now see the Ubuntu styled boot menu, I can select Xubuntu and boot up properly. I updated the Xubuntu and turned on Hardware accelerated graphics for the browser.
I rebooted the system again, and tried to boot into windows 7, and it worked, so I ignored that, and then I shat off and booted into Xubuntu again.
I installed Spotify, Steam, Wine and IMVU through Wine. I listened on some music, and browsed some random forums on the web. I rebooted the system and I was going to play some games, but when I tried to boot into Windows this time, it said that there was a problem with the harddrive, and it launched the Windows repair, then it rebooted the system, and launched windows, but the screen only goes black now when launching windows.
(EDIT) Safemode DOES NOT work.
Any idea's on how to fix? Sorry if it's the wrong forum part, or if it's not (X)ubuntu related. but I believe it is, because it first happened after I installed the DualBoot.

System info:
SSD: 256gb, 2 partitions, 156GB Windows, 100GB Xubuntu
HDD: 1x 1tb, 2x 256gb in raid 1 managed of Windows.
6gb ram
r9 280x graphicscard
MOBO imedia s3220 from Packardbell


Thanks in advance, -Zra.

---

### Post by oldfred on 2014-07-12
Post the link that this gives.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But your Windows may need chkdsk from your Windows repairCD or Flash drive.

---

