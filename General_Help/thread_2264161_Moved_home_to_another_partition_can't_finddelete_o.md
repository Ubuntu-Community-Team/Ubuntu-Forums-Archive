---
title: "Moved /home to another partition can't find/delete /old_home"
date: 2015-02-05
forum: General Help
---

### Post by l-l-pajuelo on 2015-02-05
[IMG]http://i.imgur.com/uZUqGLo.png[/IMG]

I just upgraded from an old mint to Trusty Tahr. I moved my /home to a separate partition using the [ubuntu wiki instructions.]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

/sda4 is a newly created partition /sda5 is where 14.04 sits now. 

I had some problems with rsync  and had to try several times. Instead of overwriting I think it duplicated my /home. My current /home is 15GB and fstab points it to /sda4. From gparted it looks like 120GB are being used on sda4 when it should only be 15 GB or at most 45GB (I had to retry rsync 3 times). 

In /media there is a locked empty /home and a locked /myusername with the Windows partitions (sda1 and sda3)


Is there anyway to browse by /sda# or uuid? 

fstab: ```
# / was on /dev/sda5 during installationUUID=a2b23579-2b86-459f-822f-b8c540a3087a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ef58263e-bb4b-4ea7-84ee-39cab92cb378 none            swap    sw              0       0


# (identifier)  (sda4)   (format, eg ext3 or ext4)      (some settings) 
UUID=eb5083e2-d0ec-4b86-96b7-a03eb1ae94e2  /home    ext4          defaults       0       2 
```

---

### Post by Impavidus on 2015-02-05
If you followed that guide /old_home will be a directory on sda5. All contents of sda4 will be visible in /home. The only thing I can imagine that may have gone wrong is that maybe you didn't correctly rename your old /home directory, instead mounting the new /home partition on top of it. That's easy to fix from recovery mode or a live disk, when the /home partition is not mounted.

The empty /media/home is a remnant of the move procedure. It can be deleted.

---

