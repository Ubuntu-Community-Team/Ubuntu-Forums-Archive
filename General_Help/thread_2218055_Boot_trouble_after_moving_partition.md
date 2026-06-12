---
title: "Boot trouble after moving partition"
date: 2014-04-19
forum: General Help
---

### Post by alex184 on 2014-04-19
Hi,

I've run into a bit of trouble with my fathers' notebook. Apparently he has Ubuntu and Windows 7 installed on the same partition, which ran out of space. To add some I booted Ubuntu from a USB so I could unmoun the disk, and tried resizing it. Little did I know that if you resize it from the left it moves the whole content of the partition to the new start point. Now when we start up the normal choice between Ubuntu and Windows is displayed, but if he hit either we get an error saying "Status: 0xc0000225" with "Info: Error at the Startup choice. Accessing the required Device not possible" (translated from german).

Where do I go from here? I'm not quite sure what I can do without causing more damage.

Thanks for you help!
All the best,
Alex

---

### Post by oldfred on 2014-04-19
Is this a NTFS partition?
You should use Windows tools for Windows as it special requirements and only sometimes do Linux tools work better.
All NTFS partitions have to have the same start and size info as the partition table. Usually running chkdsk from your Windows repairCD or flash drive will update that info. You cannot run chkdsk from Linux, but may from some of the third party Windows partition tools.

Not sure what else may have been corrupted if Ubuntu does not boot, as if in the NTFS partition that is a wubi install. And that is just a file inside the NTFS partition. If a separate partition other repairs may be needed.

---

### Post by alex184 on 2014-04-19
Hey,

it is a NTFS partition.

I burned a windows repair CD and ran chkdsk. Now I can start Windows, but if I try to start Ubuntu I still get the same error code with the Info : "The selected entry could not be loaded because the application is missing or corrupt" and File : "\ubuntu\winboot\wubildr.mbr". After I tried running repair from the CD it said it couldn't solve the issue.

On the other hand if I try to run the live Ubuntu Usb now and hit run without installing it restarts before it can load every time. What can I do now?

---

### Post by oldfred on 2014-04-19
I do not know much about wubi. Its last supported version is 12.04 as it does not work with gpt partitions which all new UEFI systems have. 
You can install it with newer versions but are on your own.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Do you have this file? Error message says you may not?
\ubuntu\winboot\wubildr.mbr

Wubi is intended as a bit of a test for those who are not sure if they want Ubuntu or not. You do not have to partition and can uninstall just like any Windows application. It uses Windows boot loader.

Most that like Ubuntu and want to keep using it, convert to a full partitioned install.

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by alex184 on 2014-04-20
Hey,

thanks! I ended up using the file recovery from Wubi and installed a fresh ubuntu. Everything works fine now.

---

