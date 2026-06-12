---
title: "help me to solve GParted error"
date: 2015-12-03
forum: General Help
---

### Post by onlineaddy on 2015-12-03
If it ain't broke, don't fix it. Argh... ;)

I was trying to resize my [COLOR=#a52a2a]/home[/COLOR] partition in GParted to give my root [COLOR=#8b4513]/[/COLOR] more space. Of course, something went wrong and now I'm getting the following: 
```
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.
```

I googled and tried some solutions, but honestly I'm not even sure how to go about that. Eventually, when everything else failed, I tried reinstalling my buntu, but the installer quits after I manually partition the table and assign "home" to /home partition. It says: 
"*ubuntu installer needs to remove operating system files from the install target, but was unable to do so. The install cannot continue.*" 

First off, I cannot mount my /home partition anymore (to recover my files). 
Second, I'm currently running testdisk utility as I'm typing and it looks like it's making a dd copy of my /home partition - I just hope I will be able to restore the files afterwards? 

So, my question: 
How can I fix the error without resorting to WIPING my entire hard disk drive - that's the only solution I can think of, but I will lose my data, so I don't want to do that before I tried anything better. 

Thanks for any input helping me to resolve this puzzling issue.

---

### Post by buzzingrobot on 2015-12-03
Did you try to install the e2fsprogs package?  It's in the repos.

---

### Post by onlineaddy on 2015-12-03
> **buzzingrobot said:**
> Did you try to install the e2fsprogs package?  It's in the repos.

e2fsprogs is already the newest version.

---

### Post by oldfred on 2015-12-03
What was error message from gparted?
And system knows if you have good backups of partitions. If you did backups then you do not have issues. But if you are in a hurry and forget the backups it likes to corrupt system. :) 

#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb5

---

### Post by matt_symes on 2015-12-03
Hi

> **onlineaddy said:**
>  Of course, something went wrong...

What exactly went wrong ?

> I googled and tried some solutions

What exactly did you try ?

> How can I fix the error without resorting to WIPING my entire hard disk drive

You have no backup ?

Kind regards

---

### Post by onlineaddy on 2015-12-03
> **oldfred said:**
> What was error message from gparted?

```
Unable to read the contents of this file system! Because of this some operations may be unavailable. The cause might be a missing software package. The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.
```

> **oldfred said:**
> 
#From liveDVD/Flash so everything is unmounted,swap off if necessary, 
sudo e2fsck -C0 -p -f -v /dev/sdb5

```
~ $ sudo e2fsck -C0 -p -f -v /dev/sdb5
/home: The filesystem size (according to the superblock) is 20559175 blocks
The physical size of the device is 17927424 blocks
Either the superblock or the partition table is likely to be corrupt!
/home: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
```

```
 ~ $ sudo fsck /dev/sdb5
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
The filesystem size (according to the superblock) is 20559175 blocks
The physical size of the device is 17927424 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes
```

```
~ $ sudo e2fsck -f -y -v /dev/sdb5
e2fsck 1.42.9 (4-Feb-2014)
The filesystem size (according to the superblock) is 20559175 blocks
The physical size of the device is 17927424 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes
```

---

### Post by Portaro on 2015-12-03
You only can resize a partition with security when you have a space on left or right that is a free space , for example in your extended /dev/sdb2 you have a /home a / and finally the swap , so you dont have any partition between /home and / so to you have a possibility to resize your / you always need to delete /home or /swap , to have free space to / can be resized.

But your question is very strange because in that case you cant resize anything because gparted always delete a partition to do a resize to other free space I dont see any option on gparted to resize without any free space inside your extended, so maybe the problem is on your /dev/sdb2  and you need to delete this and then extend this to the left partiton create a new ext and then resize to the free space the /home ( **in this case you cant resize / to the space to left because the free space is located beside your /home and not your / !!!)**.

Ok I think your problem now is that the /dev/sdb5 is corrupted the partition cant be read the solution appear here ->
[http://askubuntu.com/questions/640903/the-installer-needs-to-remove-operating-system-files-from-the-install-target-bu](http://askubuntu.com/questions/640903/the-installer-needs-to-remove-operating-system-files-from-the-install-target-bu)

sudo e2fsck -f -C 0 /dev/sdx(y)in your case is sudo e2fsck -f -c 0 /dev/sdb5

Your data on /home can be deleted!!!;)

---

### Post by matt_symes on 2015-12-03
Hi

If i were you i would image the hard drive from a live CD/USB to a file. I would then run all potential fixes on that file.

You can use losetup to access it as a loopback device, mount the partition after using parted or fdisk to get the partition table.

After that you can run fsck using one of the backup superblocks (although i'm not sure if this will work if the primary is corrupt) or run mke2fs using the -S swicth to rewrite the superblocks. This may work for you.

>        -S     Write superblock and group descriptors only.  This is useful if all of the superblock and backup superblocks
              are corrupted, and a last-ditch recovery method is desired.  It causes mke2fs to reinitialize the superblock
              and group descriptors, while not touching the inode table and the block and inode bitmaps.  The e2fsck  pro&#8208;
              gram  should  be  run immediately after this option is used, and there is no guarantee that any data will be
              salvageable.  It is critical to specify the correct filesystem blocksize when using this option, or there is
              no chance of recovery.


As you'll be using a dd image backup it will not mater if it gets more corrupted as you can get another image if necessary.

If you use dd then don't forget to change the number of bytes copied. The default is only 512.

oldfred and other forum members  may have other suggestions as well.

Kind regards

---

### Post by oldfred on 2015-12-03
That you tried to resize it and it failed, it would not be abnormal for partition table size to not match file system size. You have to get those back into sync. But there always is the risk of losing data.

Try the dd backup & repair with it or the advanced superblock repairs suggested above.

---

### Post by onlineaddy on 2015-12-04
> **Portaro said:**
> You only can resize a partition with security when you have a space on left or right that is a free space

I shrunk my /home partition to get additional space in front of it and take this space over by my root. Unfortunately, the freed up space was created after my /home partition and that's when I could not access it (/home) any more. 

I guess my only concern at the moment, having tried all of your suggestions is: **will the dd image of my /home be recoverable** after I wipe out everything and do a fresh install? If it's corrupted now and I'm making a dd image of it, will the restored image be corrupted as well? 
 I'm not too sure what other things I could try to restore /home. 

> **matt_symes said:**
> 
If you use dd then don't forget to change the number of bytes copied. The default is only 512.

I don't understand this, could you elaborate on this a bit further? How  would I change the number of bytes copied? I used this command: 
```
sudo dd if=/dev/sdb5 of=/media/mint/Elements/sdb5_backup.img
```

Thanks!

---

### Post by matt_symes on 2015-12-04
Hi

> I don't understand this, could you elaborate on this a bit further? How would I change the number of bytes copied?

I'll post back some instructions later today/evening for you.

I'm a bit busy at the moment.

I'll post an example for you. 

Kind regards

---

### Post by ptn107 on 2015-12-04
You can try this from a Live CD environment. Keep in mind that at any point your /home data can be lost. Make an image beforehand.

See where the backup superblocks are:
```
sudo mke2fs -n /dev/sdb5
```

and try to restore one of the backup blocks:
```
sudo e2fsck -b block_number /dev/sdb5
```
where block_number is the first number from the first command.

Reboot then fsck your drive again.

---

### Post by oldfred on 2015-12-04
Just make sure you always double check you typed dd command correctly.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

   from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

Shows and example with larger block size, but this is for erasing drive:
[http://www.anti-forensics.com/disk-wiping-with-dcfldd](http://www.anti-forensics.com/disk-wiping-with-dcfldd)
Zero out drive, larger block size than default is faster
sudo dd if=/dev/zero of=/dev/sda bs=1M

---

### Post by onlineaddy on 2015-12-04
> **ptn107 said:**
> You can try this from a Live CD environment. Keep in mind that at any point your /home data can be lost. Make an image beforehand.

See where the backup superblocks are:
```
sudo mke2fs -n /dev/sdb5
```

and try to restore one of the backup blocks:
```
sudo e2fsck -b block_number /dev/sdb5
```
where block_number is the first number from the first command.

Reboot then fsck your drive again.

I've done this:
Restored one of the backup blocks, rebooted, fsck my drive again. The result: 
```
~ $ sudo fsck -a /dev/sdb5
fsck from util-linux 2.20.1
/home: clean, 75731/4489216 files, 15496118/17927424 blocks

```

I've performed a second dd backup of my /dev/sdb5/home to an external drive (just to be on the safe side). 

And I don't know what to do next... I thought I was able to do a lot of stuff in Linux, but apparently I'm just not too bright when it comes to this one. I'm sorry, I know you guys are doing your best to help me here, and I'm really grateful to all of you, but I think I'm kinda slow on the uptake here. I need a moment to think.. :\

---

### Post by onlineaddy on 2015-12-04
Heeeeeeey, **ptn107**!
I can see my /home partition contents now after doing what you advised. WOW! A million thanks. 

Wait, wait.. I don't want to get too excited. Let me try something here, will get back to this thread. :)

---

### Post by matt_symes on 2015-12-04
Hi

Sorry for the late reply. It's been a busy day.

oldfred posted some great links for dd. It's what i use but there's another option.

It may be easier if you use ddrescue to image the drive. It gives you feedback, has a bigger default block copy size and will handle errors on the hard drive such as bad block automatically.

```
sudo apt-get install gddrescue
```

```
sudo ddrescue /dev/sdb5 /media/mint/Elements/sdb5_backup.img
```

As you know, this will create the file

```
/media/mint/Elements/sdb5_backup.img
```

cd into the directory.

```
cd /media/mint/Elements/
```

At this point to can associate the image with a loop back device

```
sudo losetup /dev/loop0 sdb5_backup.img
```

It's not mounted yet so you can't access it but you can run fsck and other commands on the device /dev/loop0.

Here's an examples of what you have tried.

```
sudo e2fsck -f -y -v **/dev/loop0**
```

Anyway, as expounded by ptn107, to try to use a backup superblock.

```
sudo mke2fs -n /dev/loop0
```

```
sudo e2fsck -b block_number /dev/loop0
```

The default extX block size is 4096 bytes (4K) so you can usually find the first backup superblock block at 32768.

```
sudo e2fsck -b 32768  -f -y -v /dev/loop0
```

To run the mke2fs with the -S switch you'll need the block size. You can find this with

```
sudo dumpe2fs /dev/loop0 | grep "Block size"
```

... but as i said above, this is usually 4096.

Then you can run

```
sudo mkfs.ext4 -b 4096 -S /dev/loop0
```

After that you'll need to run fsck.

```
sudo e2fsck -B 4096 -f -y -v /dev/loop0 
```

Finally you can mount it.

```
sudo mkdir /mnt/tmp && sudo mount /dev/loop0 /mnt/tmp && ls /mnt/tmp
```

If you're lucky then your files will be displayed.

After you can unmount and release the loopback device

```
sudo umount /mnt/tmp && sudo rm /mnt/tmp && sudo losetup -d /dev/loop0
```

The good thing about using an image file is you can run all kinds of commands on it and you don't break the original image on the hard drive. 

You can also make a second copy of the image before running any commands and work on the second copy so you don't need to dd the drive again if the commands cause you problems.

There's reasons why forensics and data recovery are (usually) performed on drive images :) 

Here's a post from Theodore Ts'o where he mentions the mke2fs -S command, one of the main developer of the extX file system.

> 
> Would it be better if I ran mkfs.ext4 -S ?

Probably note.  This is useful when the superblock and block group
descriptors have been destroyed, and that's not the case here.  The
fact that the volume name is the original means that you have at least
the original superblock, and the real problem here is that damage that
was caused by the portions of the inode table that were wiped out.  

[https://www.redhat.com/archives/ext3-users/2002-January/msg00018.html](https://www.redhat.com/archives/ext3-users/2002-January/msg00018.html)

BTW: I've never had much luck with mkfs.ext4 -S or mk2fs -S but you might. I really hope you can get your files back.

**EDIT** Seem's i posted while after you fixed it. Well done :)

Kind regards

---

### Post by onlineaddy on 2015-12-04
Big THANK YOU to all the contributors to this thread. My problem is officially solved! My system runs perfectly now. :)

---

