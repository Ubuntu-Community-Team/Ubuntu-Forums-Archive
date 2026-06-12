---
title: "Ubuntu does not boot anymore"
date: 2022-04-20
forum: General Help
---

### Post by pzeiner on 2022-04-20
Since my laptop crashed after it ran out of power, it does not boot anymore. boot-repair gives the following message [https://paste.ubuntu.com/p/9hR4Ctg4m6/](https://paste.ubuntu.com/p/9hR4Ctg4m6/) after run on liveUSB (I think it is on sdb1). Is it save to run the suggested repair?

---

### Post by tea for one on 2022-04-20
Before we go any further, does Windows still boot?

---

### Post by oldfred on 2022-04-20
Configuration looks correct.
Did you have UEFI Secure Boot on when installing Ubuntu?
There are signed versions of grub, kernel & drivers for Secure Boot and standard versions.

Windows update may have updated UEFI or fwupd in Ubuntu may have updated UEFI.
That update may have reset some UEFI settings back to defaults including turning Secure Boot on?

Often abnormal shutdown damages file system and then you need fsck for ext4 or Windows chkdsk for NTFS.
But it looks like the report showed all partitions.

---

### Post by pzeiner on 2022-04-20
No, Windows did not boot anymore either.

---

### Post by pzeiner on 2022-04-20
I cannot remember whether I had [COLOR=#000000]UEFI Secure Boot on when installing Ubuntu. I certainly used default settings. The laptop is a Lenovo, but it was bought in 2019. I installed a new Ubuntu version in 2021.

I was using Linux when the system crashed.[/COLOR]

---

### Post by oldfred on 2022-04-20
I would try with UEFI Secure Boot off.
You can use Boot-Repair to reinstall grub as it is suggesting to install the signed version. That should then work if Secure boot is on or off in UEFI settings.

There is a report that many Lenovo's need UEFI updates.
[https://www.zdnet.com/article/lenovo-patches-uefi-vulnerabilities-impacting-millions-of-device-users-worldwide/](https://www.zdnet.com/article/lenovo-patches-uefi-vulnerabilities-impacting-millions-of-device-users-worldwide/)

---

### Post by pzeiner on 2022-04-20
Thanks for the help.

I have reinstalled grub as suggested. But it still does not boot. I do not get the message with kernel panic and missing init anymore, but I just get the Lenovo logo, then nothing happens anymore.

---

### Post by oldfred on 2022-04-20
Can you then boot recovery mode or second line in grub menu?

If you do not get grub menu, you may need to press escape right after Lenovo logo & before grub menu normally would appear. Timing is important. 

And if fast boot on in UEFI settings, you may not have time to press any keys, and have to do a cold boot or full power down to get system to give just enough time to press a key.

---

### Post by pzeiner on 2022-04-21
I can get into the grub menu and select booting in recovery mode. But then booting ends with a message [end Kernel panic - not syncing: No working init found. Try passing init= option to kernel ...

It does not matter whether I disable SecureBoot or not, in both cases I get the same result.

---

### Post by oldfred on 2022-04-21
I would try fsck on your ext4 partitions and Windows chkdsk on your NTFS partitions.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

You need your Windows repair flash drive to run chkdsk.

---

### Post by pzeiner on 2022-04-23
Nothing helped. Ubuntu still does not boot. e2fsck did not report any errors. If I try to reboot Ubuntu in normal mode, I often just get the Lenovo logo. If I try to boot in recovery mode, I get the message kernel panic, no init found, try to pass init= ..., but I never get the recovery menu.

As I have made a backup of my date, it seems I have to reinstall Ubuntu, unless some other idea emerges.

Thanks for your help anyway. Even if it was not successful, I have at least learned something. I will mark this thread SOLVED tomorrow, unless anybody has any further idea

---

### Post by oldfred on 2022-04-23
You could try from Boot-Repair's advanced mode, the full reinstall of grub and newest kernel to get it to update settings.
Beyond that a new install?

---

