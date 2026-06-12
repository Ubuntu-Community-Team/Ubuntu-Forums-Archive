---
title: "Need help to access home folder from previous Ubuntu installation"
date: 2013-05-20
forum: General Help
---

### Post by tester1204 on 2013-05-20
Hello, I've used Ubuntu 12.04 for about a year alongside Windows XP (on separate physical HDDs).
On the Ubuntu 12.04, I had separate partitions for home, root, boot and swap and for data. I was also able to access these partitions from Windows XP through IFS Drives. Ubuntu sometimes reported some problems with the HDD it was installed on, while Windows didn't.

After a Windows XP reinstall, Ubuntu couldn't be started at all. During the reinstall, I had disconnected all other HDDs, except the Windows XP. From the new XP installation, all the partitions on the Ubuntu HDD, except the home and the swap partition, were visible as one common unformatted free space through IFS Drives. The home and swap partitions were visible as separate unformatted partitions. As most important data was on my home partition, I decided to install a new Ubuntu 12.04 on the common unformatted free space. After successfully doing that, the home partition from the previous Ubuntu 12.04 is not visible at all. It is also not visible from Ubuntu 12.04 Live CD, while other partitions (including the newly installed Windows XP on the separate HDD) are visible and fully accessible. From Windows XP, I have tried accessing the home partition from the previous Ubuntu 12.04 through IFS Drives and Ext2Fsd - they both recognize it as a linux partition, but the file system is not recognized (should be ext3 but these tools recognize it as RAW) and therefore the partition is recognized as unformatted and Windows always asks to format it.

Is there any way I can access and copy my data from this home folder, either from another Ubuntu 12.04,Ubuntu Live CD or Windows?
Any help would be highly appreciated!

---

### Post by oldfred on 2013-05-20
After your Windows install, are you sure you were working with unallocated space? Windows does not see Linux partitions and often in rewriting MBR & partition table it changes everything to unallocated.

If it really is your partition and it is RAW, that is Windows saying it is NTFS but unformatted. It expects a PBR or partition boot sector to have NTFS boot & configuration data in it, Linux PBR's are usually just empty.
You then may be able to use Disk Utility or Disks in newer versions and just change partition type from 07 (NTFS) to 83 (Linux). That will not reformat it but just change partition table entry. If you reformat then data will more than likely be gone.

Post this
sudo fdisk -lu

---

### Post by MrSteve on 2013-05-20
use a live ubuntu cd and when its loaded open a terminal and write
sudo nautilus
press enter 

this will open the file manager with root permissions and you should then be able to move the required files to a usb key drive ...

---

### Post by tester1204 on 2013-05-21
> **oldfred said:**
> After your Windows install, are you sure you were working with unallocated space? Windows does not see Linux partitions and often in rewriting MBR & partition table it changes everything to unallocated.

If it really is your partition and it is RAW, that is Windows saying it is NTFS but unformatted. It expects a PBR or partition boot sector to have NTFS boot & configuration data in it, Linux PBR's are usually just empty.
You then may be able to use Disk Utility or Disks in newer versions and just change partition type from 07 (NTFS) to 83 (Linux). That will not reformat it but just change partition table entry. If you reformat then data will more than likely be gone.

Post this
sudo fdisk -lu

Disk utility shows that partiotion type is 83 (Linux) already. However, Disk utility is the only place under Ubutnu where the existence of this partition is visible at all. Nautilus cannot detect it. Another thing that worries me is that Disk utility shows an alarming message DISK FAILURE IS IMMINENT.

---

### Post by oldfred on 2013-05-21
You can try fsck. But if disk failure is imminent, then that is the internals of the drive reporting major issues.

If you can get to data back it up and look for a new hard drive.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by tester1204 on 2013-05-21
> **MrSteve said:**
> use a live ubuntu cd and when its loaded open a terminal and write
sudo nautilus
press enter 

this will open the file manager with root permissions and you should then be able to move the required files to a usb key drive ...

I managed to start Nautilus with root permissions as you have written above (from a Live CD), however the partition is not visible there.
Also, in the terminal, I get the following message:

"root@ubuntu:/home/ubuntu# sudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing."

I googled the net in order to install samba but I found no way how to do that from Live CD.
I also noticed that the newly installed Windows XP sees the newly installed Ubuntu partition in the same way - as unformatted space.
The I got OS uninstaller and uninstalled the new Ubuntu 12.04 from there (from a Live CD, no OS from HDD started), but I chose to keep my files and not format the drive. OS uninstaller moved them to some folder called "Old files" or somethnig like that. And then I made a reboot, started Windows XP and the whole partition with these "Old files" was fully accessible from Windows!
For that reason, I believe that there is some kind of protection of the user folders in Ubuntu 12.04 that prevents them from being seen and accessed from other Ubuntu or Windows installations and from Live CDs. However, I do not remember ever being asked to encrypt or protect these folders when I installed Ubuntu - both the old and the new one. As the new one was unistalled by this OS uninstaller I have no problem accessing the files that were in its home folder, while for the old one the installation was lost in the way I have described in th opening post of this topic and can find no way to access them. I may be wrong, but that seems to me very similar to a prblem I've had with wto Windows XPs installed on one PC where the second one detects some user files and folders on the first one as protected. However, in these Windows cases, the second Windows detects the partitions and folder structure at least, while in this Ubuntu case Windows detecst it as unformatted space and in Ubuntu only the Disk uitility detects it as 83 (Linux), while Nautilus does not detect it at all.
So, is there any default protection in 12.04 that is applied once the OS is installed without asking me? Or the reason culd be problems with the HDD (however I have no problems with other logical partitions on it)?

---

### Post by tester1204 on 2013-05-21
> **oldfred said:**
> You can try fsck. But if disk failure is imminent, then that is the internals of the drive reporting major issues.

If you can get to data back it up and look for a new hard drive.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Here is the result (doing it from Live CD):

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

At the same time, there is no problem in accessing files from the newer 12.04 on another partition in the same HDD, but only after the newer 12.04 was uninstalled through OS uninstaller as I explained...

---

### Post by oldfred on 2013-05-21
Unless you clicked on the checkbox to encrypt /home you should not have encrypted your partitions. But if you did the only way to access it would be with the pass phrase. I do not use encryption so I do not know details.

Have you tried testdisk and deeper search to see if it sees any data?

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

      
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

