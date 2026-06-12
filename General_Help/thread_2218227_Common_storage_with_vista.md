---
title: "Common storage with vista"
date: 2014-04-19
forum: General Help
---

### Post by jamchamp on 2014-04-19
Hi

I was on ubuntu 13.04, moved to 14.04 yesterday. Its dual boot with Vista 32 bit. When I was on 13.04, I had managed to have common User folders (Desktop, Documents, Music etc) through an article on ubuntuforums. This time I can't locate it. Can someone please help/guide me how to make my existing windows user folders as /home in ubuntu?

---

### Post by oldfred on 2014-04-20
I normally suggest a separate shared NTFS data partition. I have seen where some may try to link directly into the Windows system partition but that can lead to issues.
Did you have a separate partition?

Post this:
sudo parted -l
 sudo blkid -c /dev/null -o list

---

### Post by jamchamp on 2014-04-20
> **oldfred said:**
> I normally suggest a separate shared NTFS data partition. I have seen where some may try to link directly into the Windows system partition but that can lead to issues.
Did you have a separate partition?

Post this:
sudo parted -l
 sudo blkid -c /dev/null -o list


I have a separate NTFS partition for this data. The results are below:

sudo parted -l

Model: ATA WDC WD5000BPVT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  53.5GB  53.5GB  primary   ntfs            boot
 2      53.5GB  458GB   405GB   primary   ntfs
 3      458GB   500GB   41.9GB  extended
 6      458GB   496GB   37.7GB  logical   ext4
 5      496GB   500GB   4196MB  logical   linux-swap(v1)



sudo blkid -c /dev/null -o list

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs             (not mounted)  24D15A0456D26DFF
/dev/sda2  ntfs    data     /media/anshuman/data 746F61075CB6FEF5
/dev/sda5  swap             <swap>         d0c524ff-6d95-4185-94ea-2e79422394e4
/dev/sda6  ext4             /              2a304e7c-de4a-4d63-a3bb-69d3ed98e4c7

sda1: Windows, sda2: data, sda5/6; Ubuntu

The folders are on sda2: /users/anshuman/Desktop, /users/anshuman/Documents etc

---

### Post by jamchamp on 2014-04-20
> **monkeybrain20122 said:**
> Do people still use Vista?

Got it in 2007. haven't felt the need to scale up. windows is primarily used for (a) editing word docs/ppts (libre/open office change the format) (b) watching movies via HDMI (I had HDMI sound issues in 13.04, now resolved in 14.04)

---

### Post by monkeybrain20122 on 2014-04-20
Though I am against perpetuating MS's formats but if you have to work with them KingSoft Office is reported to have high level of compatibility with MSO so in this instance I will hold my nose to suggest it (it doesn't support open formats) MSO itself can be installed in Wine. If either of the above works for you it would be better than the your awkard dual booting setup IMO.

---

### Post by jamchamp on 2014-04-20
Wine doesn't support all forms of MSO. Mine is a 2010 student edition and not supported by Wine. In fact I had to make it dual boot for the 2 reasons stated earlier

---

### Post by oldfred on 2014-04-20
I do not know if you used linking or binding. Links to both.

 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

I have my data partitions several levels up or when not mounted the data partition has just folders for Documents, Videos, Music etc. not /home/fred/Music.
But when mounted in /home it is seen as /home/fred/Documents.

---

### Post by jamchamp on 2014-04-20
thanks.. Liked the rsync. but I messed up something and can't log back to my user profile.. may have to reinstall

---

