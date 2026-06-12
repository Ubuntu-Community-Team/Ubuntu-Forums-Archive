---
title: "Reformatting an external HDD with Ubuntu installed on it"
date: 2017-07-25
forum: General Help
---

### Post by conormullins3 on 2017-07-25
Hello,

As an experiment a few months ago I installed Ubuntu on an external HDD to see if I could run it off of an external HDD. I played around with it for a while but I've decided it's not for me. I now want to reformat my external HDD so it can be once again used as storage media for backing up files. However, because the disk is now an Ubuntu boot disk, I can't seem to get Windows to recognise it as an HDD. Is there any way to wipe the disk from within Windows using third-party software (I'd feel more secure doing it that way) or do I have to boot into Ubuntu and format the disk from in there? And if so, how can I go about doing that?

Best,

Conor

---

### Post by yancek on 2017-07-25
You're looking at some potential problems here.  If you have Ubuntu on an external, did you separate it's bootloader from windows?  Can you unplug the external and boot to windows?  I don't really use windows but I would think you could use Disk Management to format the partitions.  You should see the drive/partition there but since windows doesn't have the capability of reading or writing to any Linux filesystem, it will probably just show as 'Healthy Partition'.  I don't know how you would know which partition it is since windows doesn't identify Linux partitions by their standard drive letter system.  I would dis-connect the Ubuntu drive and verify that you could boot windows first.  You should be able to format any partition with any Linux Live DVD or flash drive but obviously can't do that from a running system.

---

### Post by vocx on 2017-07-25
> **conormullins3 said:**
> Hello,

As an experiment a few months ago I installed Ubuntu on an external HDD to see if I could run it off of an external HDD. I played around with it for a while but I've decided it's not for me. I now want to reformat my external HDD so it can be once again used as storage media for backing up files. However, because the disk is now an Ubuntu boot disk, I can't seem to get Windows to recognise it as an HDD. **Is there any way to wipe the disk from within Windows** using third-party software (I'd feel more secure doing it that way) or do I have to boot into Ubuntu and format the disk from in there? And if so, how can I go about doing that?

Best,

Conor

As mentioned by yancek you can probably do it with the Windows Disk Management. It will be evident that a second hard disk is installed but with an unrecognizable file system; it should just say Healthy Partition. So, just select it, and format it to NTFS, and that should be it.

The other way is using a live CD or live USB with Ubuntu, the same disk or USB image that you used to install Ubuntu. When you boot the computer with the live CD or USB, the live session will come up, and you will have access to a partition editor called "gparted". Open that, and in the same fashion as the Windows Disk Manager you can select the external hard disk and erase its partition. The resulting space will look like "Unallocated space". If you don't format it with another file system, then next time you boot into Windows you will have the option of formatting that external drive with NTFS.

Also mentioned by yancek, very important question: can you boot the Windows computer without the Ubuntu external hard drive connected? The bootloader of your computer is typically installed in the first few sectors of your primary hard drive, which means, if you have a Windows drive A, and an Ubuntu drive B, the bootloader "grub" is installed into the first sectors of drive A. If the bootloader is installed in drive B, then you should not be able to boot into the computer when you disconnect this drive. You need to double check this. The bootloader is installed in space that is not visible from the operating system, that is, Windows or Ubuntu cannot see this space. It is only touched during the original installation of the operating system.

Ubuntu normally installs the bootloader in such a way that you can boot multiple operating systems, so it shows you a black screen with different options. Windows on the other hand overwrites the bootloader and just boots Windows. Usually, if you have a problem booting Windows, guides suggest using your Windows installation DVD to run a repair mode to reinstall the bootloader for Windows. You should do this if you don't want to see any trace of Ubuntu, or the black screen boot menu that it presents.

You may do the bootloader repair before or after erasing the Ubuntu partition as explained before. It's up to you. Depends on if you need to repair the bootloader at all. If you don't need to repair the bootloader, that is, if Windows boots fine, without any issues, then just go ahead and delete the external disk partition as explained above, with the Windows Disk Manager, or with "gparted" in an Ubuntu live USB session.

---

### Post by conormullins3 on 2017-07-26
Hello,

I have been using Windows without the external HDD plugged in for some time now and I have experienced no problems booting into Windows. So wiping the HDD shouldn't cause me any problems! I shall give the diskmgmt.msc method a try. If that doesn't work, I'll try the live USB method.

Thanks for the help!

---

