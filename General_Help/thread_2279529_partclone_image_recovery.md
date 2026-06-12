---
title: "partclone image recovery"
date: 2015-05-24
forum: General Help
---

### Post by mastablasta on 2015-05-24
is there any way to get the data out of partclone image?

i just had a server failure and i created image along with damaged files and i have an older image. but older image don't want to restore, while the new image restores, but gives this at the end ```
Syncing... fsync error: errno = 5
```.

i can't boot it. so i would liek to get the config files out. i learned that backup is not as important as restore. :)

also i have a question - if i create normal .img file from the OS can that be more easily used as backup? i mean from .img file you can usually extract individual files as needed. i am not sure why partclone would make that thing difficult.

---

### Post by VMC on 2015-05-24
Have you tried mounting the image then exacting your config files? Maybe this will help:
[http://blog.christosoft.de/2012/05/mount-clonezilla-image-to-restore-single-file-browse/](http://blog.christosoft.de/2012/05/mount-clonezilla-image-to-restore-single-file-browse/)

---

### Post by mastablasta on 2015-05-24
that might work in this case as the image is about 3GB (what i mean is files when they were not compressed). Even at max space with all emtpy space it was about 7.4 GB. heh conversion - never though of that.

waiting for the replacement and in the mean time i think i will have a go at conversion into IMG. if i coudl just get the setup files out i think that would help plenty.

---

### Post by mastablasta on 2015-05-26
this line doesn't seem to be working:

sudo cat /dir-to-images/sdb1.ntfs-ptcl-img.lzo.* | sudo lzop -d -c | sudo partclone.restore -C -s - -O /dir-to-new-image/hda1.img


shouldn't there be only one sudo?

anyway looks like it's doing something now. let's see....

edit: doesn't seem to be working. 

I am going to try it in a different way. by extracting the image manually from gzip...

---

### Post by VMC on 2015-05-26
Here's the command I use for 'gz' compressed file:

**zcat ubuntu.gz | sudo ./partclone.ext4 -N -r -o /dev/sdaX**

What error did yours give?

---

### Post by mastablasta on 2015-05-27
I didn't finish the task and pointed to partclone log, however the log didn't really hold much clue. I expected it to be filled with some errors or at least one like syntax error or something but no...

what is **/dev/sdaX** in your command? is this this the place where image is based? I mean why is there disk stated?

---

### Post by VMC on 2015-05-27
"X" is to be renamed for your partition number, for example sda6.

---

### Post by mastablasta on 2015-06-02
new disks arrived and i managed to restore the image to them however they don't boot. ok so i though better i copy all the files to the disk. when i was doing that it couldn't read certain files such as access keys, some file s ofrm postgresql database, sudoers file and a few others. kind of strange after getting the message that image was succesfulyl restored. and it makes sense something's woul dbe damagd in new image but the old one should be 100% ok.

---

### Post by mikodo on 2015-06-02
> **mastablasta said:**
> this line doesn't seem to be working:

sudo cat /dir-to-images/sdb1.ntfs-ptcl-img.lzo.* | sudo lzop -d -c | sudo partclone.restore -C -s - -O /dir-to-new-image/hda1.img


shouldn't there be only one sudo?

Not relevant to your concerns now but, I was told once that to do pipe commands, one must use root, not sudo. I guess that is why it has the 3 sudo's. ???

---

### Post by sudodus on 2015-06-02
How did you create the partclone image? I have never used partclone 'as is', only wrapped in Clonezilla.

I agree 100% with you, I have also learned that 'backup is not as important as restore'. So I have tested that it works to restore what I back up with Clonezilla.

Anyway, I wonder why there are errors in your restored system, why you cannot read certain files. There should be some warnings during the backup process. In Clonezilla I select the option to test that it is possible to restore from the backup image. I don't know exactly how it works, but I hope and think it would detect errors, and give me a chance to repeat the process until there is a good backup.

---

### Post by mastablasta on 2015-06-02
I used Redo Backup which has a nice frontend for partclone. perhaps it is time to switch to clonezilla. Anyway it works kind of in same way - I booted live on another PC and used the program to create backup image.

I too do not understand why the files can not be read (though they are present on disk). /root and /lost+found directories can't be read as well. the may image was made when disk had reading errors. ok - it gave errors during backup  so image might not be good. fine. but the February image was made after I resolved the bug in owncloud. it never gave any errors. and now it gives one upon restore, but the error is only some cat bad pipe error or something like that. while at the same time the bad image from May gives no errors on restore. despite having many during backup :)

anyway aside from keys and some files handling access (passwords, sudoers, postgreSQL) it looks ok. oh yeah all cron setup files also - errors so at least I can use the old config files which was my biggest worry as I can't remember all the stuff I did. I plan to document it now and I plan to put some sort of monthly backup.

the one thing I am a bit worried is will I be able to mount the RAID 1 array. I guess I will find out, but if not I will nuke it all. too bad it seem I won't have the time to do it this week. 

I also plan to checkup all logs for anything suspitions but I did occasionally check the access logs and they don't show anything strange. no logins form outside of LAN also the 22 was closed to outside world since January, but fail2ban was still running and blacklisting (well it didn't add any to blacklist since there were no attempts). :)

---

### Post by sudodus on 2015-06-02
I think it is important to have good file systems, so I run ```
sudo e2fsck -f
``` if there is a reason to suspect problems, or maybe even ```
sudo e2fsck -cf
``` to engage ***badblocks***. When I have had problems with failing disks (last time my 1 GB disk with mainly a data partition), I have been able to save all files with ddrescue (from the package gddrescue). See Examples 1 and 2 in ```
info ddrescue
```

I have ***no*** experience of RAID arrays, but I guess each disk device can be backed up separately, when booted from a separate drive (for example using a Clonezilla live CD/DVD/USB drive). I understand that RAID systems have built in redundancy against logical and physical damage

[http://www.dedoimedo.com/computers/linux-raid.html](http://www.dedoimedo.com/computers/linux-raid.html):

> RAID is used to increase the logical capacity of storage devices used, improve read/write performance and         ensure redundancy in case of a hard disk failure. All these needs can be addressed by other means, usually more         expensive than the RAID configuration of several hard disks. The adjective Inexpensive used in the name is not without a reason.

but you should not allow the disks to get too bad before replacing them.

Could it be that there were errors on that disk, and another part of the RAID array has been covering up for it? Maybe people with more experience of RAID can explain these things better (or tell us that I'm wrong) :-P

---

### Post by mastablasta on 2015-06-02
no, the RAID disks are made for redundancy purpose. in my case they held /data /var/log and /swap (swapiness was reduced), system was on separate disk. so I need to load the system and then only assign it the previous partitions (not format them). so all write stuff was on hard disk, while system disk was a USB flash drive with 5 years warranty & certified for linux. i mean since Rpi is working nicely on SD card.... i am not sure what made 2 sectors on the system disk bad and throw out reading errors and blocked the writing. updates were automated once a week and various writes removed. so the write cycles came nowhere near USB life limit. furthermore disk had about 6 GB free space and it could have easily used other parts of disk. so looks like some component inside it completely failed.

but we did have a power outage and maybe it was some fluctuation that damaged it. who would know.

perhaps I will get a UPS but it's an investment.

fun fact:  fsck didn't find any errors on damaged drive. after running it i could do the updates back then, but when I repeated the process (sudo apt-get update) it threw read errors again. i then found a windows program for testing USB drives which showed error on read test. i have not yet performed the write test. i plan to when have the time to see what it will show. write test destroys all data on that disk.

---

### Post by sudodus on 2015-06-02
It is hard to find out exactly what causes a hardware damage, but a power outage is certainly a 'good' candidate.

Please tell us what USB flash drive with 5 years warranty you are using!

Good luck with the write test :-)

---

### Post by mastablasta on 2015-06-03
The flash drive is Kingston DataTraveler G4 8 GB (now we also got another 16 GB version). It's a USB 3.0 drive (fully compatible with USB 2.0) with 5 year warranty. and they claim to support it with spare parts 3 year after the warranty period expires. :)

the drive is nothing special though it was graded good on reviews. It also has specifically stated it supports Linux form kernel 2.6 onwards or something like that.

as i read Ext4 can cause drive to brick if it is a cheap low quality drive that has low number of writes. however this drive is nothing special in price segment. and the article that has this info is 2 years old now.

I am checking some other options for this server that has only USB plugs - one would be USB drive, SSD drive (i am not really sold on it for server OS) or normal hard drive inside the CD drive area. however they are more costly. I can get 10 of these USB drive for one of those :). plus the way internal sata plug is made is kind of strange - it runs at IDE speed. though 3rd party BIOS supposedly can get it sataa speed. another option is PCI sata card. maybe later and I can stuff more 2.5" disks into that 5" CD drive space. 

and USB drive works very well otherwise as system disk. I didn't really notice it being extra slow or anything. ok normal hard disk or SSD would be faster but in this use the difference is maybe not so big that is worth the cost. HDD via USB makers little sense (apart from write cycles) as the speed would be same as on USB flash drive (the bottle neck is USB 2.0 plug).

---

### Post by sudodus on 2015-06-03
I have a Kingston Datatraveler Ultimate 3.0  G3 (32 GB), that has been reliable for me (but not as fast as another USB 3.0 pendrive, Sandisk Extreme). But any drive can fail, even an enterprice class HDD. I think pendrives fail mainly when they write data, not when they read data, or if they get too hot, so I agree that it should work with the operating system in a pendrive, if you avoid unnecessary writing.

But an HDD or an SSD in a USB or eSATA external box (enclosure with good cooling at least for the HDD) might be a good alternative with a longer expected lifetime, however more expensive. You can wear out many USB pendrives for the same cost as one HDD or SSD, so it depends how important it is to keep the server running for years without a failure.

---

