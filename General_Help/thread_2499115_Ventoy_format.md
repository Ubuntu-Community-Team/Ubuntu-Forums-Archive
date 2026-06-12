---
title: "Ventoy format"
date: 2024-07-13
forum: General Help
---

### Post by angel mike on 2024-07-13
I have used Ventoy for making a bootable usb with Windows iso. Ventoy has made 2 partitions on the usb but they are in exfat32. The Windows iso is in NTFS . I cannot copy/drag the downloaded iso onto the usb. Is this because of the exfat32 and how do I change the partitions to NTFS ?

---

### Post by vanadium on 2024-07-13
Current linux kernels natively support exfat, but if you are using an older version of the distribution, you will need to install exfat support.

---

### Post by guiverc on 2024-07-13
I use ventoy on some of my thumb-drives for QA testing Ubuntu ISOs.   I have no issues with ISOs of Ubuntu for current releases (*including oracular*), though currently Ubuntu 24.04 LTS Desktop is the largest at 5.7Gb (*oracular* currently is 5.5gb; *flavors* are all smaller).

I'm not *dragging/dropping* from a GUI, I do it regularly and its done from CLI or command line, when I run a script (*it copies & runs a diff afterwards*).

---

### Post by The Cog on 2024-07-13
I get the impression from [https://www.ventoy.net/en/doc_disk_layout.html](https://www.ventoy.net/en/doc_disk_layout.html) that provided the Windows version ***in*** the ISO can understand ExFAT, then you can continue to use ExFAT on the USB, you just need to use a more modern OS (recent Linux or Windows) to write the ISO file to the stick. 

If the ISO contains an old version of Winows that can't read ExFAT then you can reformat the partition 1 to NTFS and then write the ISO file to that.

---

### Post by angel mike on 2024-07-14
Thank you all for those responses- the windows 10 iso is from the Microsoft download site so is upto date. Using ubuntu 22.04 so from your comments it should be possible to put the iso onto the usb and run it. 

1.If I cannot use a drag and drop what is the command to use in the terminal.

2. How do I change from exfat32 to NTFS in the Partition 1 on the usb

---

### Post by guiverc on 2024-07-14
> **angel mike said:**
> Thank you all for those responses- the windows 10 iso is from the Microsoft download site so is upto date. Using ubuntu 22.04 so from your comments it should be possible to put the iso onto the usb and run it. 

1.If I cannot use a drag and drop what is the command to use in the terminal.



An example command I'll use to update a *oracular* ISO to Ventoy thumb-drive is

```

cp -puv oracular-desktop-amd64.manifest /media/guiverc/Ventoy/
cp -puv oracular-desktop-amd64.iso      /media/guiverc/Ventoy/

```

It's a simple COPY where I preserve file-stats (-p) and only update (-u) the files if they already exist on the media.Those commands are run from the directory in which I want the files copied from (ie. it'll copy Ubuntu Desktop, Lubuntu, Ubuntu-MATE, Xubuntu etc. or whatever directory I'm currently in).  If the filename looks different to yours, its only because I'm usually writing *daily* ISOs rather than releases ISOs.

---

### Post by yancek on 2024-07-14
Iso files are usually iso9660 filesystems and can be booted from any partition regardless of the partition filesystem type.   I've never used Ventoy so I don't know it's requirements or limitations.  If you think you need/want an ntfs filesystem, you can format it with Disk Management in windows or any Linux partition manager such as gparted.  If you don't have it installed on your system, just do:  sudo apt install gparted.  When it is installed, open a terminal and run:  sudo gparted to start it.  If you think copying it to a partition on the flash drive will work, just navigate to the directory where the iso file is and use the cp command.  Create a mount point and mount the partition first.  If the device partition is sdb1 just do these steps replacing windows.iso with the actual name of the iso file :

> sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
sudo cp windows.iso /mnt/sdb1 

---

### Post by angel mike on 2024-07-15
Thanks for those responses- will follow them through and hopefully close the thread

---

### Post by angel mike on 2024-07-17
Sorry to come back but still having problems copying the windows 10 iso to the ventoy usb.
It is mounted at /media/michael/Ventoy . If I follow yancek instructions assuming I can put the iso which is in NTFS on the usb partition1  which is in exFAT - how do I change the mount point and when do I insert the usb?

---

### Post by angel mike on 2024-07-17
I have checked the Ventoy usb and now have the windows iso file loaded - a step forward! The mount point is media/michael/Ventoy

However when I close the co0mputer down and reinsert the usb and restart with the F2 key sequence and go the boot order the usb is not showing. Why is this ?

---

