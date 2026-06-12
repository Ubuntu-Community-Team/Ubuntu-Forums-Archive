---
title: "OS rescue"
date: 2006-12-12
forum: General Help
---

### Post by Jason Argo on 2006-12-12
I have windows XP home (OEM) installed on my computer with no partitions. I’m getting the Blue screen of death and have been advised to recover my data and do a reinstall. Can I use Ubuntu to recover my data from windows before I do a repair install of windows, so I can partition my HDD to run both Ubuntu and windows. I’m completely new to Ubuntu and to recovering data from a broken OS so I know very little, though I’m reading as many threads as I can. All help very much appreciated.

---

### Post by taurus on 2006-12-12
I guess you can use the LiveCD to boot your machine, mount your Windows partition, save the important stuff to a USB thumbdrive, and repartition your harddrive again...

---

### Post by wpshooter on 2006-12-12
Might want to try the "**Ultimate Boot Disk**"

---

### Post by drpaul on 2006-12-12
Don't forget to format the external medium in something other than ntfs. Otherwise the Live CD may not want to write to it.

I used fat32 when I did it.

Paul:)

---

### Post by Sef on 2006-12-12
If you have any problems with Ubuntu's Live CD in pulling anything off, get [Knoppix]("http://knoppix.com/").  I used it and it worked without a hitch (i.e., without any problems.)

---

### Post by mcglnx on 2006-12-12
> **Sef said:**
> If you have any problems with Ubuntu's Live CD in pulling anything off, get [Knoppix]("http://knoppix.com/").  I used it and it worked without a hitch (i.e., without any problems.)
May be an already answered question, but what is the benefit of Knoppix vs Ubuntu???

---

### Post by maxamillion on 2006-12-12
Knoppix is made to be a LiveCD. While Ubuntu's liveCD is more of just a tool to allow users to preview the system before installing it (and in some cases fixing current installs) but yes, I too would recommend Knoppix. It comes with alot more applications that might help too (i.e. photorec and scandisk).

/me

---

### Post by Jason Argo on 2006-12-12
> **maxamillion said:**
> Knoppix is made to be a LiveCD. While Ubuntu's liveCD is more of just a tool to allow users to preview the system before installing it (and in some cases fixing current installs) but yes, I too would recommend Knoppix. It comes with alot more applications that might help too (i.e. photorec and scandisk).

/me

Thanks guys, I've been looking at the free (open source) version of Knoppix, would I be able to use the Foxfire in Ubuntu to download it, I only have one external media drive (CD ROM) though. So before I start to download it can I take out the Ubuntu CD and put in a blank one. Or will I need to install Ubuntu onto my HDD? If I do that is there ANY chance I could loose data from my windows OS? I'm thinking there is, so is there anyway of downloading onto an OS Live disk?

---

### Post by altonbr on 2006-12-12
Guys, he can use the Ubuntu LiveCD to recover his data... Aysiu always has the answer [Mount Partition with LiveCD]("http://ubuntuforums.org/showpost.php?p=1093585&postcount=3").

Just make sure to change "ext3" to "ntfs" since it's a Windows drive. Also, your drive might not be "hda1", so make sure to check that out. Here's my revised suggestion: 
> sudo mkdir /recovery
sudo mount -t ntfs /dev/hda1 /recovery
gksudo nautilus

1) create a folder name "recovery" in the root directory "/"
2) mount a ntfs partition in "/dev/hda1" in "/recovery"
3) launch nautilus as a graphical root (I'm not sure if this is needed.. it may just show up on your desktop as "recovery" and you can double-click that)

Good luck!

---

### Post by Jason Argo on 2006-12-12
> **altonbr said:**
> Guys, he can use the Ubuntu LiveCD to recover his data... Aysiu always has the answer [Mount Partition with LiveCD]("http://ubuntuforums.org/showpost.php?p=1093585&postcount=3").

Just make sure to change "ext3" to "ntfs" since it's a Windows drive. Also, your drive might not be "hda1", so make sure to check that out. Here's my revised suggestion: 


1) create a folder name "recovery" in the root directory "/"
2) mount a ntfs partition in "/dev/hda1" in "/recovery"
3) launch nautilus as a graphical root (I'm not sure if this is needed.. it may just show up on your desktop as "recovery" and you can double-click that)

Good luck!

Thanks for that, two questions: 

Where do I type in the script? 

Will this mean I cannot do a windows repair install? as it will change the location of windows on my computer, is there a way of changing it back again after the data recovery? What I'm looking at doing is recover my data with a Live CD, do a windows repair install (most likely loose data) then partition and install Ubuntu and windows.

---

### Post by altonbr on 2006-12-12
Go to: Applications >> Accessories >> Terminal (this is similar to Command Prompt or MS-DOS). You then type in those 3 lines above, one at a time, hitting enter after each line. If there is a problem, post the error in this thread, and I will try and help you.

What you will be doing is mounting your Windows hard drive, finding all the documents you want to backup, then transferring them to another Computer or a USB Flash Drive. If you need help with that, please post in this thread.

Then you will re-install Windows, or do a recovery. Recoveries don't always loose data unless you're doing a serious fix. If you are typing in "fixmbr" or a similar command, you will most likely not loose your data. If you have to re-install, install Windows first, THEN install Ubuntu. Ubuntu will install a Boot Loader called GRUB in your Master Boot Record (MBR) overtop of the Windows Boot Loader, but this loader, GRUB, will give you a choice to which Operating System you would like to launch, where as Windows' Boot Loader, doesn't. That's why we install Ubuntu AFTERWARDS. If you made the mistake of installing Ubuntu first, post in this thread and I will try and help you.

Good luck!

---

### Post by Jason Argo on 2006-12-13
> **altonbr said:**
> What you will be doing is mounting your Windows hard drive, finding all the documents you want to backup, then transferring them to another Computer or a USB Flash Drive. If you need help with that, please post in this thread.


I only have one CD ROM drive for removable media, so I guess I can’t save my data unless I purchase a USB Flash Drive? If I get my copy of Ubuntu onto a 4gb DVD can I save my data to the same DVD and transfer it over once I complete the whole partition & install thing?

---

### Post by seshomaru samma on 2006-12-13
Can your CD-ROM burn?
If so: 
Use Ubuntu to burn a copy of [PuppyLinux]("http://www.puppylinux.org/user/viewpage.php?page_id=1") which runs entirely on RAM -it's a small file (about 60MB) 
Boot from Puppy's CD
Mount the Windows partition (Puppy Does it automatically, just look for the 'drives' icon on the desktop)
Take the Puppy CD out- Puppy will still run
Burn the Windows data into a CD or DVD

---

### Post by altonbr on 2006-12-13
If that suggestion above, PuppyLinux, doesn't work, the next best thing you can do is find someone who is willing to do an SSH or FTP of all your data onto their computer. If you have 4GB, this could take some time, but at least it would be backed up.

Do you have a second computer that has a 10GB hard drive that could load Ubuntu and still have enough room for your backup? This would be best because then you wouldn't have to trust a total stranger with your personal data.

I'm more than willing to help you, but you should only consider this as an absolute LAST resort.

:-k 

What about a friend close by that also has some form of Linux?

---

### Post by Jason Argo on 2006-12-13
> **altonbr said:**
> If that suggestion above, PuppyLinux, doesn't work, the next best thing you can do is find someone who is willing to do an SSH or FTP of all your data onto their computer. If you have 4GB, this could take some time, but at least it would be backed up.

Do you have a second computer that has a 10GB hard drive that could load Ubuntu and still have enough room for your backup? This would be best because then you wouldn't have to trust a total stranger with your personal data.

I'm more than willing to help you, but you should only consider this as an absolute LAST resort.

:-k 

What about a friend close by that also has some form of Linux?

Both those ideas are great, thanks, I'm looking into Puppy now. I've got web space from my ISP which I could transfer files onto, does Ubuntu have FTP functions? If not, can I download an open source FTP program onto my Live boot CD?

---

### Post by altonbr on 2006-12-15
If you've ever used PuTTY (remote administration of UNIX command-line on Windows), WinSCP or any FTP program like SmartFTP or CuteFTP, then you'll be glad of this built-in function.

go to: Places > Connect to Server...

and enter all your relevant information in there. A shortcut to connecting to this server will be placed on the Desktop and in the "Places" menu.

This is the type of stuff Linux is made for!

---

### Post by Jason Argo on 2006-12-17
> **altonbr said:**
> Guys, he can use the Ubuntu LiveCD to recover his data... Aysiu always has the answer [Mount Partition with LiveCD]("http://ubuntuforums.org/showpost.php?p=1093585&postcount=3").

Just make sure to change "ext3" to "ntfs" since it's a Windows drive. Also, your drive might not be "hda1", so make sure to check that out. Here's my revised suggestion: 


1) create a folder name "recovery" in the root directory "/"
2) mount a ntfs partition in "/dev/hda1" in "/recovery"
3) launch nautilus as a graphical root (I'm not sure if this is needed.. it may just show up on your desktop as "recovery" and you can double-click that)

Good luck!

I've decided to mount my windows install and save the files on my web space (thanks altonbr for that idea) using the Archive Manager and Connect to Server features, which I've tested and found to work really well & are easy to use. When I try to mount my windows install, it states that the windows install doesn't exist. I asked on the windows support forum what is the name of the drive, the response was either hda0 or hda1, I've tried both and neither work. I've copied both attempts from the Terminal:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /recovery
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /recovery
mount: special device /dev/hda1 does not exist
ubuntu@ubuntu:~$

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /recovery
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hda0 /recovery
mount: special device /dev/hda0 does not exist
ubuntu@ubuntu:~$

Any ideas why it's not working?

---

### Post by bulldog on 2006-12-17
Can you give the outcome of ```
sudo fdisk -l (l as in like) 
``` so we can see which partitions are on your hard disk?
If you have just one partition you should use just hda to mount.

---

### Post by Jason Argo on 2006-12-18
> **bulldog said:**
> Can you give the outcome of ```
sudo fdisk -l (l as in like) 
``` so we can see which partitions are on your hard disk?
If you have just one partition you should use just hda to mount.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5       14589   117154012+   7  HPFS/NTFS
ubuntu@ubuntu:~$

So does that mean I should type:

sudo mkdir /recovery
sudo mount -t ntfs /dev/hda2 /recovery

or

sudo mkdir /recovery
sudo mount -t ntfs /dev/sda2 /recovery

---

