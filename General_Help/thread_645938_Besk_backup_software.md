---
title: "Besk backup software"
date: 2007-12-20
forum: General Help
---

### Post by fizikz on 2007-12-20
What backup software would be recommended for making backups of my laptop hard drive? I have several partitions, including a windows partition, a few linux partitions and a FAT32 data partition.

Previously under windows, I used Acronis True Image (version 10, I believe). I think they also have a version for linux servers. But I would like to know what others use and recommend. 

Thanks!

---

### Post by HermanAB on 2007-12-20
Bacula or just rsync.

Cheers,

Herman

---

### Post by mellowd on 2007-12-20
tar

---

### Post by fizikz on 2007-12-20
I suppose I'll look into Bacula. It seems like it has several features, many of which I don't need, but besides that they report there is a serious bug at the moment.

As for tar, that would be a bit tedious, and also how would you back up a whole partition? One of my partitions is encrypted too...

---

### Post by mellowd on 2007-12-20
> **fizikz said:**
> I suppose I'll look into Bacula. It seems like it has several features, many of which I don't need, but besides that they report there is a serious bug at the moment.

As for tar, that would be a bit tedious, and also how would you back up a whole partition? One of my partitions is encrypted too...

```
sudo tar zcvf backup.tgz --exclude=backup.tgz --exclude=/whatever_needs_excluding /
```


That would back up everything on / into one file except whatever has been excluded. If you only wanted to backup a partition just put the partition at the end instead of the /

---

### Post by noynac on 2007-12-20
I use Acronis TrueImage 10 Home. It's been rock solid and allows me to restore individual files, folders, partitions, and the entire drive. I dual boot WinXP and Gutsy, and I have a separate Fat32 partition for data. I store the images on an external hard drive and periodically save an image to a DVD.

---

### Post by fizikz on 2007-12-21
For the tar approach, would I have to first mount the partitions I want to back up? Because I have an encrypted partition that I don't always mount. Acronis TrueImage took care of that when I used it in windows.

Also, is TrueImage available for linux? I also dual boot linux and XP, but I find I rarely need to boot into windows anymore, so I prefer to use linux equivalents of the software I'm used to using in windows.

---

### Post by FuturePilot on 2007-12-21
There's a program called Partimage. As the name suggests it will image your drives. It's in the repos
```
sudo apt-get install partimage
```
However if you want to image your system drive you'll need the CD for that since it needs to be unmounted in order to be imaged.
More info here
[http://www.partimage.org/Main_Page]("http://www.partimage.org/Main_Page")
[http://www.partimage.org/Download]("http://www.partimage.org/Download")

---

### Post by fizikz on 2007-12-21
Partimage looks like the type of program I'm looking for. Unfortunately, its support of NTFS filesystems is in the experimental stage. I need to back up a variety of filesystems, including NTFS, FAT32, and ext3.

---

### Post by mellowd on 2007-12-21
> **fizikz said:**
> For the tar approach, would I have to first mount the partitions I want to back up? Because I have an encrypted partition that I don't always mount. Acronis TrueImage took care of that when I used it in windows.

Also, is TrueImage available for linux? I also dual boot linux and XP, but I find I rarely need to boot into windows anymore, so I prefer to use linux equivalents of the software I'm used to using in windows.

Yes it would have to be mounted first unfortunately. You could probably create a script that mounted, backed up and then unmounted all in one.

---

### Post by fizikz on 2007-12-21
The problem is not so much the mounting. That particular partition is encrypted with truecrypt. If I back it up while it's mounted, then I'm backing up the data unencrypted (or I'll be using other encryption options associated with tar, and not the original encryption). Aside from that, I think it might be easier to have a disk image. That way restoring should be easier, at least according to my current understanding.

---

