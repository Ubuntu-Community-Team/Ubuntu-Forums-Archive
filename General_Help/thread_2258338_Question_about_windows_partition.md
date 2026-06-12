---
title: "Question about windows partition"
date: 2014-12-26
forum: General Help
---

### Post by John_Combe on 2014-12-26
I have installed Lubuntu 14.04.1 onto a usb drive as part of my testing out different distributions for somewhat decent response times when running from a flash drive. My question is that I do not like my windows hard drive being mounted automatically as I have read that the C: drive (in windows) could be corrupted by linux having read write access to my windows partition. Is it safe to unmount my windows partition within lubuntu to prevent data corruption and how do I permanently stop Lubuntu (as in no access within Lubuntu) from mounting my windows partition?

---

### Post by yancek on 2014-12-26
A Linux system isn't going to do anything to your windows system as it limits itself to its own partition(s) and system.  The user on the other hand, can do all kinds of damage.  I would not expect your Lubuntu normal user to have write privileges to the ntfs partition but I don't use so am not sure.  Permssions/access to ntfs systems is different and the standard Linux permissions don't apply.  The link below gives a pretty detailed explanation of it.  

[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by John_Combe on 2014-12-26
The windows OS is XP and thus uses the FAT filesystem with one or two hidden ones Fat16 and some other ones FAT32, which were already setup that way by Dell (learned when using GParted from a LiveUSB with Persistence to format another flash drive for Lubuntu). I am worried that since LiveUSB with/without Persistence use FAT32, Lubuntu 14.04 does have the ability to affect my Windows XP OS as it was setup by Dell with the FAT filesystem.

---

### Post by grahammechanical on 2014-12-26
> [COLOR=#000000] I am worried that since LiveUSB with/without Persistence use FAT32, Lubuntu 14.04 does have the ability to affect my Windows XP OS[/COLOR]

The file system that the live session is running on is immaterial. When a Ubuntu ISO image is burned to a DVD disc, what is the file system on the DVD? It does not matter what it is. We can still instruct the installer to install Ubuntu by using the entire disk and in this way affect an existing Windows OS. There are other things we could do with the partitioner that would affect not only Windows but any OS installed. For example, we could delete the partition table.

If none of this was possible we would not be able to install any Linux distribution on to a hard disk with Windows already on it. I do lots of installs of Ubuntu for testing purposes. I always worry. Not because of the file system of the DVD or USB but because of my own stupidity in not double checking what I am doing. We users are a greater risk to the operating system than anything else.

Regards.

---

### Post by John_Combe on 2014-12-27
So from the last post lubuntu would not damage windows xp, but what would damage it would be me. So to ease my mind I could just unmount the windows partition each time I use Lubuntu and just forget about that partition during each session? I have OCD and only within the last two weeks decided to give Linux a serious try, but obsessing over what could mess up my windows computers is an issue that plagues me even while using windows, so I am aware that I may ask questions about what is obvious to others.

---

### Post by Yellow Pasque on 2014-12-27
Couldn't you just edit the entry in /etc/fstab to mount the partition as read-only?

---

### Post by John_Combe on 2014-12-27
I am a Windows user with some troubleshooting experience on XP and 7, I am not a Linux user. What I have memorized safely so far is using GParted, the installation process, and where to put nomodeset option within the edit function of grub when booting from usb to make nvidia displays not go crazy with blinking colors. I do not know how the linux filesystem works or where to locate configuration files.  I ask questions because Linux is new to me and sometimes I need more details for an issue that was answered in another person's post.

---

### Post by Yellow Pasque on 2014-12-27
Well, it's been a while since I played with /etc/fstab, so I don't know everything about it off the top of my head. This is how I would approach your issue -
First, get the UUID (i.e. copy it so you can paste it later) for your FAT partition with this command:
```
sudo blkid
```
Next, open up /etc/fstab for editing:
```
gksu leafpad /etc/fstab
```
Add this line to the end, replacing "pasteUUIDhere" with the UUID and /mountpoint with the actual location you would want the partition mounted if you did so.
```
UUID=pasteUUIDhere      /mountpoint        vfat        noauto,ro      0         0
```
Save the file and quit leafpad (the text editor). If my theory is correct, the partition should no longer be mounted automatically and be mounted read-only by default if it is mounted.

---

### Post by Yellow Pasque on 2014-12-27
I should also point out that if you already have a line in your /etc/fstab for that UUID, you would just edit that line instead of adding a new one.

---

