---
title: "GParted partition help."
date: 2013-06-06
forum: General Help
---

### Post by sports fan Matt on 2013-06-06
Is there any way with GParted since I'm not sure which of my partitions went south to see them and then delete the bad partition and use the functioning to free up space and have more room on the drive?

---

### Post by Irihapeti on 2013-06-06
Gparted will often mark a partition as "unknown" or with a black icon if there's something wrong with it. Is that what you have in mind?

---

### Post by sports fan Matt on 2013-06-06
..not exactly.  I have two areas for Ubuntu. Thing is, one of them doesn't work.  It;s broken.  I had to put Ubuntu on a smaller footprint on the drive and what I'd like to do is successfully remove the one that is broken and allocate the broken space to the working Ubuntu install.

---

### Post by Irihapeti on 2013-06-06
That would depend on where the good install is in relation to the broken one. If they are next to each other, and the good install is to the left (as seen in the GParted gui), then you can delete the broken install and then expand the good partition to take up the unallocated space. That's usually a fairly quick and safe (as far as any partitioning can be) operation.

But in any other case, it's going to be tricky and risky. Shifting the beginning of a partition (the left-hand end in the gui) works in theory, but is horrendously slow and at considerable risk of going wrong. In that case, it's easier to backup your install using tar, rearrange your partitions, and then restore the tar archive to the new partition.

---

### Post by ajgreeny on 2013-06-06
When you are booted into your current working Ubuntu OS run command **mount**, which will tell you which partition is being used as root, as /home, if you have it separate from root, and any other mounted partitions.  That should let you know which partition is which if you compare it with the gparted info and let yopu delete the bad one.

What you can then do with the empty space will, as Irihapeti says, depend on the disk and partition layout.

---

### Post by greatsirkain on 2013-06-06
you want to be carefull that the bad install wasn't due to a disk fault in that area too otherwise you'll be giving the faulty sectors to the good install. It would be best to delete the bad but keep it partitioned away from the good as isolated storage space by reformatting it to ext2, 3 or 4. 
Make sure you know which is which first though and to format a partiton on the drive you have to unmount it so you might have to boot from a live ubuntu cd/usb to be able to unmount the drive and use gparted, or you can make live versions of gparted itself

---

### Post by sports fan Matt on 2013-06-07
Here is the output:  dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matty/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matty)


AS I recall DEV5 was my bad partition.  If that helps.

---

### Post by sports fan Matt on 2013-06-07
Any ideas?

---

### Post by Irihapeti on 2013-06-07
Can you post the output of:
```
sudo fdisk -l
``` (lower case L, not a "one")

or a screenshot of the relevant drive from GParted, if you prefer.

Then we can see what else is on the drive and how it's laid out.

---

### Post by sports fan Matt on 2013-06-07
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xff14f3c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2         3074048   339240040   168082996+   7  HPFS/NTFS/exFAT
/dev/sda3      1221519360  1250263039    14371840   17  Hidden HPFS/NTFS
/dev/sda4       339244605  1221518339   441136867+   5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       634663953  1205485469   285410758+  83  Linux
Partition 5 does not start on physical sector boundary.
/dev/sda6      1205485533  1221518339     8016403+  82  Linux swap / Solaris
Partition 6 does not start on physical sector boundary.
/dev/sda7       339244731   622583009   141669139+  83  Linux
Partition 7 does not start on physical sector boundary.
/dev/sda8       622583073   634663889     6040408+  82  Linux swap / Solaris
Partition 8 does not start on physical sector boundary.

Partition table entries are not in disk order

---

### Post by Irihapeti on 2013-06-07
I have to go out in a few minutes, so can't give this the concentration I need to.

You can figure out the physical order of the partitions from the beginning and end block numbers. At a quick glance, I think it goes sda7 sda8 (swap) sda5, but I'd need more time to double check.

I'll be back in 2-3 hours, but in the meantime someone else can feel free to weigh in.

---

### Post by sports fan Matt on 2013-06-07
That's cool. I'll wait to see if anyone has any other suggestions

---

### Post by sports fan Matt on 2013-06-07
Had a thought.  Can I delete SDA 5 in Gparted (and in theory)that space goes to SDA 7?

---

### Post by Irihapeti on 2013-06-07
The partition order on disk is sda7, sda8 and sda5.

You could delete sda8 and sda5 and add the free space to sda7. That still leaves you with one swap partition (sda6). You could enlarge that if you think it's necessary. If you don't hibernate the computer, it's probably not all that important.

However, keep in mind what an earlier poster said. How did your corrupted Linux partition get that way? If you know that you just fiddled with something and it went wrong (easy enough to do!), then there should be no problems. If there's some possibility that the disk itself is faulty, then you might want to rethink using sda5. The best way to find out would be to use smartmontools to check the disk health. The Disk Utility on the 12.04 live CD includes that capability.

Also, BACKUP sda7 (your working system) before you do anything else, just in case something goes wrong. Using tar is fine and is able to cope easily with restoring to a different partition size. See [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

### Post by sports fan Matt on 2013-06-07
I don't think the disk is faulty, It got that way by trying to slim down my partition and when trying to fix broken packages, I couldnt get the held packages removed.

---

### Post by sports fan Matt on 2013-06-07
Unable to delete /dev/sda5! Please unmount any logical partitions having a number higher than 5

---

### Post by sports fan Matt on 2013-06-07
My thinking is though if I unmount my working partition (7) it will become unreadable when I next boot up and then i'll have problems. Also, the only option for SDA5 now is swapoff.

---

### Post by Irihapeti on 2013-06-07
I'm not sure why sda7 would become unreadable (unless something goes haywire during repartitioning). Could you post a screenshot taken in GParted? That might clarify things.

---

### Post by sports fan Matt on 2013-06-07
Sure can I relearn how?  (Been gone for a few years, had to get a new laptop)

---

### Post by Irihapeti on 2013-06-07
No one is too old or out of practice to learn/relearn.

But it you really get stuck, try the old standby of using a digital camera to literally take a shot of the screen.

---

### Post by sports fan Matt on 2013-06-07
There

---

### Post by Irihapeti on 2013-06-07
The layout is what I thought. You should be able to delete sda5 and sda8 and expand sda7. But not while sda7 (and the extended partition sda4) is mounted/in use. That's why the little key icons are there.

You need to use a liveCD to do this. The ubuntu liveCD has GParted on it. If you haven't got an optical drive, make a liveUSB.

---

### Post by sports fan Matt on 2013-06-07
Even one from all the way back in 9.04?

---

### Post by Irihapeti on 2013-06-07
No, I wouldn't use one from that far back, because GParted doesn't have the "align to MiB" function which you need for aligning the partitions on large HDDs.

Get hold of 12.04.2 or even the latest Parted Magic liveCD if download bandwidth is a problem.

---

### Post by sports fan Matt on 2013-06-07
Bandwith isn't a real problem.  However I have never burned a CD before :)  This shall be interesting

---

### Post by Irihapeti on 2013-06-08
OK, burn it at the slowest speed that's available. Some people report better success with CD or DVD read-only rather than RW. And run the error check when you first boot with it. I can't remember what it's called but it's in the main menu on the Ubuntu CD.

---

### Post by sports fan Matt on 2013-06-08
Downloading now..will report back.

---

### Post by sports fan Matt on 2013-06-08
I got up this morning and the disk was ejected (which I think is a good sign) I then booted into the disk and it brought up the logo (and really started spiing,using disk a lot and not in a good way, almost like it was clicking, and never booted up)  It had gotten stuck at checking midsum5hash.

---

### Post by Irihapeti on 2013-06-08
Sorry, I'm not much use with troubleshooting bad CDs/DVDs, because I don't think I've ever had a bad burn. Maybe someone else could help.

Alternatively, if the computer will boot from USB, you could make a liveUSB.

---

### Post by sports fan Matt on 2013-06-08
No big deal, it can honestly wait until I can purchase a CD (Really need to anyway since the last Ubuntu released CD I have is from 9.10) Is there a chance after 13.10 is released they will make CD's for purchase?  I looked at Canoical's store and the only thing close is a DVD of 12.10.  (for $8 it's right for the price)

---

### Post by Irihapeti on 2013-06-08
I don't know what Canonical's plans might be, but maybe you could find someone in your area who will burn a DVD of 12.04 or 13.04 for you.

---

### Post by sports fan Matt on 2013-06-08
I just bought a Ubuntu 12.04 disk off Ebay.  When it arrives I shall solve this thread.

---

### Post by greatsirkain on 2013-06-09
You bought a ubuntu disk off ebay? You just gave someone free money. If I'd had a blank DVD I'd have posted you one for free. I prefer live USBs to DVDs unless I'm going to be using it heavily every day then I don't want a USB stick hanging out the laptop 24/7, they're just faster and easier to make/fix/change etc

---

### Post by sports fan Matt on 2013-06-09
It's OK. super cheap (less then $5) and I wanted to have a disk close to the newest release.

---

### Post by sports fan Matt on 2013-06-10
Ok, when upgrading to Ubuntu 13.04 I was able to delete the bad partition SDA5.  Now just to allow the data to go into the good partition.

---

### Post by sports fan Matt on 2013-06-10
Whoops!  In doing that,  I have a error : unknown files stem.  I screwed up and now can't boot to anything,  not even Windows 7.  Any advice?

---

### Post by Irihapeti on 2013-06-10
I think I need to leave this to someone else. It's above my pay grade, so to speak.

Hopefully one of the boot experts will come along soon.

---

### Post by sports fan Matt on 2013-06-10
Understandable.  Let me ask this though. (As long as I have a prompt for grub rescue, it can be fixed pretty easily)?

---

### Post by sports fan Matt on 2013-06-10
2,000 beans :)

---

### Post by Irihapeti on 2013-06-10
> **sox fan Matt said:**
> Understandable.  Let me ask this though. (As long as I have a prompt for grub rescue, it can be fixed pretty easily)?

Yes. That's not as bad as I'd feared. I had thought it might have been something worse. However, I do need to check: does this machine have Secure Boot / UEFI?

---

### Post by sports fan Matt on 2013-06-10
As I'm Windows 8? No

---

### Post by sports fan Matt on 2013-06-10
In,  Sheesh.  Typos galore

---

### Post by sports fan Matt on 2013-06-10
No have Secure Boot / UEFI present.  I assume that is a W8 feature.

---

### Post by Irihapeti on 2013-06-10
Then that should be fairly easy to fix.

You need to boot with your live CD and chroot into your working Ubuntu install.

I've linked to a post where I've shown someone else how to do this: [http://ubuntuforums.org/showthread.php?t=2149797&p=12672492#post12672492](http://ubuntuforums.org/showthread.php?t=2149797&p=12672492#post12672492)

Where I've mentioned /dev/sdxy, you substitute /dev/sda7

When you've done that part, you can do
```
grub-install /dev/sda
```
Note that there's no number after sda.

Then:
```
update-grub
```

Assuming that it all works without errors, you can reboot, cross fingers, and it should give you a grub screen with Ubuntu and Windows.

---

### Post by sports fan Matt on 2013-06-10
Ok, here is Model: ATA Hitachi HTS54756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags 
 1      1049kB  1574MB  1573MB  primary   ntfs         boot  
 2      1574MB  174GB   172GB   primary   ntfs               
 4      174GB   625GB   452GB   extended                     
 6      174GB   319GB   145GB   logical   ext4               
 7      319GB   325GB   6185MB  logical   linux-swap         
 5      617GB   625GB   8209MB  logical   linux-swap         
 3      625GB   640GB   14.7GB  primary   ntfs         hidden

---

### Post by sports fan Matt on 2013-06-10
So it's there :)

---

### Post by sports fan Matt on 2013-06-10
So, using what I have provided, it would be SDA4?  (Seems like I blew away the bad ubuntu partition 5)

---

### Post by Irihapeti on 2013-06-10
No, we want to get into your good Ubuntu partition, sda7.

---

### Post by Irihapeti on 2013-06-10
Scratch that: it looks like sda6

---

### Post by sports fan Matt on 2013-06-10
Ok. Will wait until someone has an idea.  The main thing I'm happy about is my W7 and SDA 7 partitions are present.

---

### Post by Irihapeti on 2013-06-10
The easy way is to launch GParted on the liveCD and take a look. That should make it clearer.

---

### Post by sports fan Matt on 2013-06-10
Screenshot of GParted

---

### Post by Irihapeti on 2013-06-10
Right, it's sda6. So put /dev/sda6 in where I've got /dev/sdxy

---

### Post by sports fan Matt on 2013-06-10
Ok, I ran sudo -i
root@ubuntu:~# mount /dev/sda6 /mnt
root@ubuntu:~# mount -o bind /dev /mnt/dev
root@ubuntu:~# mount -o bind /dev/pts /mnt/dev/pts
root@ubuntu:~# mount -o bind /proc /mnt/proc
root@ubuntu:~# mount -o bind /sys /mnt/sys
root@ubuntu:~# chroot /mnt

All look good so far?

---

### Post by Irihapeti on 2013-06-10
Looks good. If you run
```
ls
```
you should see the top level folders of a linux system, plus vmlinuz and initrd.gz

Assuming that's the case, go ahead and run the two grub commands.

---

### Post by sports fan Matt on 2013-06-10
Desktop  Documents  Music  Pictures  Public  Templates  Videos

---

### Post by sports fan Matt on 2013-06-10
grub-install /dev/sda
mkdir: cannot create directory `/boot/grub': Permission denied

---

### Post by Irihapeti on 2013-06-10
Then for some reason the chroot hasn't worked, and I can't think why at the moment.

Unless.... /dev/sda6 is just a data partition i.e. with just your files on it, and not a full install.

---

### Post by sports fan Matt on 2013-06-10
This could be.  Maybe mounting another partition would do the trick?

---

### Post by Irihapeti on 2013-06-10
If /dev/sda6 is just a data partition, then you may currently have no Ubuntu install at all on the disk. Not a major disaster, because you can install it.

You can check by mounting the partition in the liveCD gui, and seeing what's there. Exit the chroot first, because it's not doing what I thought it was going to do.

It would probably make sense in that case to backup your files, then get rid of that little swap partition between sda6 and unallocated, expand sda6 to take up all the free space, and then install to sda6. Doing the install would automatically take care of the grub thing.

---

### Post by sports fan Matt on 2013-06-10
Sounds good. When you have a few minutes I'd like some help in doing this (helping shrink then get rid of that little swap partition between sda6 and unallocated, expand sda6 to take up all the free space, and then install to sda6.  I'm glad it's not a major disaster.  (Thought at worst I'd have to reinstall two operating systems)

---

### Post by Irihapeti on 2013-06-10
Back up your files before you do anything else.

Once you've done that, you can delete the little swap partition and expand sda6 using GParted on the liveCD.

Then, when you go to install, take care to choose "Something else" when you get to the bit that asks you about partitions. That lets to select sda6 as the one you want to install to.

---

### Post by sports fan Matt on 2013-06-10
Got it.  SDA7 is 5.76 GIB'S where as SDA 5 is 7.65.  So, once I back up my files I can presumably delete SDA7 and then using Gparted use SDA5 and add it it to what SDA6 shows?

---

### Post by Irihapeti on 2013-06-10
Leave sda5, delete sda7 and then expand sda6 to fill the space. You'll need to make sure the partitions are all unmounted first.

If I'm a little slow responding, I'm working on another task at the same time.

---

### Post by sports fan Matt on 2013-06-10
No problem :)  New Size: 140500
Free Space after: 282470

I can do more but was wondering how much I should resize.

---

### Post by Irihapeti on 2013-06-10
How you resize is up to you. If you want, you can create a separate /home partition with some of that space. Then the system only needs to be something like 30GB - possibly less if you don't install masses of programs. My system partition on my main machine is about 24GB and it's nowhere near full, as you can see below.

```

ja@ja-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb5        22G  6.2G   15G  31% /
udev            715M  4.0K  715M   1% /dev
tmpfs           289M  1.4M  288M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            723M  200K  723M   1% /run/shm
/dev/sdb6        98G   19G   75G  20% /home/ja
/dev/sdb2        85G   42G   39G  53% /srv

```

---

### Post by sports fan Matt on 2013-06-10
Can I use my unallocated space towards my SDA6 or divide it between my SDA6 and my W7 install?

---

### Post by Irihapeti on 2013-06-10
Now that's where it gets tricky because if you try to resize your W7 partition with GParted, you'll very likely mess it up. Not good.

You could leave some blank space for resizing W7 from within Windows, but I don't quite know how well that would work, because Windows doesn't know anything about Linux partitions. Someone else would need to weigh in here.

An alternative might be to make a NTFS data partition, which W7 would probably see as D: drive. Quite a few laptops are set up this way.

---

### Post by sports fan Matt on 2013-06-10
So basically the easiest thing to do is install to SDA6 and leave the free space untouched?  Edit: it still sees my SDA 6 install (Ubuntu 13.04 as 195.3 GB)  not sure if that says much.

---

### Post by Irihapeti on 2013-06-10
Expand sda6 to the right to fill up the free space, unless you want to make a separate NTFS partition with some of it, which W7 will be able to use.

---

### Post by sports fan Matt on 2013-06-10
...and use it when formatting as EXT4?

---

### Post by Irihapeti on 2013-06-10
Yes, ext4 for Ubuntu.

---

### Post by sports fan Matt on 2013-06-10
I resized with around 100 GB for my new Ubuntu Partition.  Going to install and at least get 12.04 Precise on there sand then if needed I'll resize.

---

### Post by Irihapeti on 2013-06-10
Resizing an installed partition is always a bit of a risk, though if you resize the right-hand end (as seen in GParted) it's fairly safe.
Anyway, see how it goes. As long as you use the "Something else" in the partitions dialogue when installing, you should be fine. Double check that you've chosen the correct partition for Ubuntu before you continue - don't want to accidentally wipe out W7!

---

### Post by sports fan Matt on 2013-06-10
Everything worked as planned, however I have several Ubuntu installs and would like to be able to use the installs to increase my W7 partition.  (It's only 80 gb) and delete the other bad installs if necessary.

---

### Post by Irihapeti on 2013-06-10
Good to hear that you've got it working.

The one you just installed is the one that's controlling grub (I assumed that you installed grub during the installation.) So you should in theory be able to delete any other Linux partition and be OK.

Dealing with changing the size of Windows partitions is something I don't have much experience with, so I'd prefer to leave that part of it to someone else.

---

### Post by sports fan Matt on 2013-06-10
Indeed, I however have to reinstall from 9.10 ass this is the last disk I had available.  When I receive my 12.04 disk it will be much easier.  :)

---

### Post by Irihapeti on 2013-06-10
I hadn't registered that it was a 9.10 install. Probably best not to use that install in the meantime. If it's let you get back into Windows, at least you're not left high and dry.

---

### Post by sports fan Matt on 2013-06-10
I did see Windows so all is well.  (Yeah, wish I was something more current but eventually I will have a disk of 12.04) Since I'm not that great at burning disks, the nominal fee I pay, $2.35 was worth it in this case, just haven't gotten the disk yet.

---

### Post by Irihapeti on 2013-06-10
Re the disk, there's no law that says you can't pay a reasonable price for open source software. In fact, if you read through the GPL, you'll see that it's about freedom as in openness, not free as in zero price.

Since you've been away for a while, you might find it useful to browse around the wiki. You can use the NewDocs link in my sig for a more user-friendly index.

---

### Post by sports fan Matt on 2013-06-10
Precise is installed.  Anyone know how I can delete all my unused partitions with GParted so I can free up and give space to my W7 install.  (I'll post GParted in a few)

---

### Post by sports fan Matt on 2013-06-11
How can I add more partition space to my W7 install?

---

### Post by Irihapeti on 2013-06-11
Windows has its own partitioning tool, the name of which I can't remember at the moment. I'm thinking that, although Windows can't recognise Linux partitions (without an add-on), it probably does recognise that there's an extended partition. If it does, then you can use that program to extend C: drive into the unallocated space. In other words, boot into Windows, find that program and post a screenshot of what it shows.

---

### Post by sports fan Matt on 2013-06-11
I dug around for a free partitioning software last night in Windows, but didn't really find one.  (I know there is one that everyone seems to use but it's escaping me at the moment).  Would GParted work on Windows?

---

### Post by Irihapeti on 2013-06-11
Don't use GParted for Windows. That often causes problems because it's not a Windows tool.

Here are some useful links:
[http://www.makeuseof.com/tag/shrink-extend-volumes-partitions-windows-7/](http://www.makeuseof.com/tag/shrink-extend-volumes-partitions-windows-7/)
[http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/how-to-extend-system-drive-partition-c-to-get-more/6acd8697-4292-4280-8270-049691d14598](http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/how-to-extend-system-drive-partition-c-to-get-more/6acd8697-4292-4280-8270-049691d14598)
[http://www.sevenforums.com/general-discussion/1822-resizing-new-partition.html](http://www.sevenforums.com/general-discussion/1822-resizing-new-partition.html)
[http://www.tomshardware.com/forum/250553-32-solved-windows-expand-partition](http://www.tomshardware.com/forum/250553-32-solved-windows-expand-partition)

Between all of them, you should find something useful.

---

### Post by sports fan Matt on 2013-06-11
Resizing the partition in my C drive gave me the dreaded grub rescue. I used Easus partition manager in Windows

---

### Post by sports fan Matt on 2013-06-11
I have a feeling my Windows7 partition is gone.     

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2            4215       14677    84038626+   7  HPFS/NTFS
/dev/sda3           76037       77826    14371840   17  Hidden HPFS/NTFS
/dev/sda4           21118       76036   441136867    f  W95 Ext'd (LBA)
/dev/sda5           21118       34188   104992744+  83  Linux
/dev/sda6           34189       74040   320111158+  83  Linux
/dev/sda7           74041       75038     8016403+  82  Linux swap / Solaris
/dev/sda8           75039       76036     8016403+  83  Linux

---

### Post by Irihapeti on 2013-06-11
That is kind of odd. If Windows is going to do anything strange, it usually rewrites the mbr, meaning that you can only boot into Windows.

Check and see if your Ubuntu partition has changed its designation, by any chance. And for that matter, check that Windows hasn't managed to overwrite the beginning of the partition and erase some of the grub files. If it has, it's not the end of the world - it just means another install. You already have your data files backed up.

Anyway, I'm going to try something on my own machine. I'll be back in (we hope) half an hour or so.

---

### Post by Irihapeti on 2013-06-11
OK you posted while I did. Does not look good, I'm afraid. Is there any way you can restore Windows from the recovery partition? I've only done this once, and it was ages ago. I think you have to hit a Function-key when you turn it on.

Edit: and it will overwrite Ubuntu, I'm fairly certain.

---

### Post by sports fan Matt on 2013-06-11
I can.  Fortunately Toshiba has a recovery partition.  (that's all backed up)  I haven't bothered with backing up Ubuntu because I'd still have 9.10.  (Yes I know, but my other disk is not here yet)

---

### Post by oldfred on 2013-06-11
How did sda1 get changed to type 27 unknown. Usually NTFS is type 7 and since sda1 has boot flag it just about has to be type 7. You can use Disk Utility to change type in partition table without reformatting, but lets check a few things first.

May be best to see more details.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Irihapeti on 2013-06-11
I'll leave it to oldfred. He knows a lot more about this sort of thing than I do.

---

### Post by sports fan Matt on 2013-06-11
Sorry for the long wait in replying, I got locked out. Here is Gparted..any ideas?

No can do on the boot repair...I only have a copy of 9.10 so maybe that is why?

---

### Post by sports fan Matt on 2013-06-11
Gparted

---

### Post by sports fan Matt on 2013-06-11
This might be a better one.

---

### Post by Irihapeti on 2013-06-11
That's done something really weird to your partition layout! There's now 30GB of unallocated space before sda2 that wasn't there in your previous screenshot, a day or so ago.

Just pointing it out in case it's relevant.

---

### Post by sports fan Matt on 2013-06-11
I had taken old fred's advice and read on enlarging my W7 partition with easus partition free.  I just slid it over thinking it would make W7 bigger, (so I know how that occured).  

Off topic for a sec.  my Precise disk should be here tomorrow or the next day.  (is it good that W7 still shows, even that largely?  (not a huge concern I'm thinking, huge concern would be it was not there) at all/disappeared or deleted.

---

### Post by Irihapeti on 2013-06-11
I think I'm best off giving the short answer here: don't know. :) Wait for oldfred and see what he says.

---

### Post by sports fan Matt on 2013-06-11
:)  I am glad it still sees it.

---

### Post by oldfred on 2013-06-11
gparted says it still is NTFS which is good. But where did the type 27 come from?

Not sure I like using 9.10 for anything other than looking at partitions. gparted and other tools in that version are now old and have many updates since then.

---

### Post by sports fan Matt on 2013-06-11
When I shifted using (Easeus Partition Master Free Edition), just slid the partition thinking it would make W7 bigger.

---

### Post by oldfred on 2013-06-11
I have not used Easeus, but others have reported it has worked well for them. 

I do not have Windows anymore as I shut my old XP down about a year ago.

---

### Post by sports fan Matt on 2013-06-12
I don't think there is anything "damaged" or destroyed", I just can't get to boot.  I wonder how I could at least try and get something to boot, then I could work on with help shrinking/resizing...etc

---

### Post by oldfred on 2013-06-12
If you want to boot with Windows you need Boot-Repair or a version of Ubuntu that can download lilo. If you have a Linux repairCD they often include lilo on the CD. Lilo boots the same way Windows does by looking for partition with boot flag and jumping to the partition's boot sector. If you just install lilo's MBR it will boot Windows.
Or you can reinstall grub, are you running grub legacy or grub2? Many with 9.10 still had grub legacy as 9.10 was the first with grub2.

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by sports fan Matt on 2013-06-12
Gonna try downloading lilo now.  The Master Boot Record of  /dev/sda  has been updated.

---

### Post by sports fan Matt on 2013-06-12
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)   Which are my partitions that have 12.04 and W7 on them/?  Those are the ones that I'd like to save. the 13.04 can be allocated to either partition.  (in dire straits..I'd only want to save W7

---

### Post by sports fan Matt on 2013-06-12
At the very least I''d want to reinstall Windows 7, then reinstall Ubuntu.

---

### Post by sports fan Matt on 2013-06-12
Just took a look at this.  

Free size preceding: 31560
New Size MIB: 82069
Free Space Following:  50517

If I shrink the free space, would that make any difference?  (that is all I did in Windows to get where we are now)

---

### Post by sports fan Matt on 2013-06-12
..or when my precise 12.04 live cd comes, can I run [https://help.ubuntu.com/community/Boot-Repair?](https://help.ubuntu.com/community/Boot-Repair?)  (Sorry for al the questions, trying to figure this out as well)

---

### Post by Irihapeti on 2013-06-12
I assume that when you get your liveCD you can install and run Boot-Repair. Because it's only in RAM, the program will disappear when you reboot. Which may not matter if it's done what you want.

If all else fails, you still have the option of restoring Windows from the restore partition and then (re)installing Ubuntu.

I believe that some recovery software gives you the option to do a boot repair.

If anything oldfred says contradicts any of these remarks, go with what he says.

---

### Post by sports fan Matt on 2013-06-12
I use a cloud server in Windows for everything to be backed up.  I assume boot-repair was made available after 9.10. This is why at least to me, it's worth the few dollars to spend for new releases on EBAY.  I figure if I spend $5 on every LTS release, it's easier then pulling my hair out.  (Thanks for bearing with me, if I sounded harsh or rude I apologize)

---

### Post by sports fan Matt on 2013-06-12
Just a thought, If I deleted all my ubuntu partitions, would it read my W7 and then boot to it?  I can always install Ubuntu

---

### Post by sports fan Matt on 2013-06-12
Gparted

---

### Post by sports fan Matt on 2013-06-12
Funny, the man at Staples today told me if I deleted my Ubuntu, it could read the W7 partition.

---

### Post by Irihapeti on 2013-06-12
I think the beginning of your Ubuntu partition hasn't been altered (just did some adding up of partition sizes, starting from the end of the table).

You could try the following, from the grub rescue prompt, and see what happens. You may want to print it off or write it down first.

```

gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
linux /vmlinuz root=/dev/sda5 ro quiet splash $vt_handoff
initrd /initrd.img
boot

```
If it works, it should get you into your Ubuntu install. If it doesn't, error messages would be useful.

A lot of this will be easier once your 12.04 disk arrives. It would also be a good idea to figure out why you're having trouble with burning CDs/DVDs. Being able to do that would make life a lot easier. :)

I have to go out shortly for a few hours, so won't be around. Hopefully, oldfred will come along in the meantime.

---

### Post by sports fan Matt on 2013-06-12
Ok,  I'm tracking tornado warning in my hometown area as well, so trying to keep family and my loved ones informed.  (I know oldfred is from my area as well)

---

### Post by Irihapeti on 2013-06-12
Fair enough. Family and loved ones definitely come first.

---

### Post by sports fan Matt on 2013-06-12
Riddle me this, after I shut it down, it booted into Windows after finishing resizing Easeus Partition Master Free Edition

---

### Post by oldfred on 2013-06-12
Deleting does not automatically make Windows work. Whatever is in MBR is what will boot, but if you have a grub MBR, then the rest of grub is deleted and nothing boots. 
You need a Windows repairCD, Boot-Repair or install a Windows boot loader like lilo or syslinux's MBR which work like the Windows MBR boot loader.

I used to burn many CD whenever installing a system. I would have Windows repairCd, Ubuntu liveCD or current version I am installing but would also create a gparted, Knoppix, parted magic, Supergrub or others and with every install make a current version CD. But since converting to flash drives and multiple hard drives I rarely burn CDs anymore. I always want more than one way to boot something.

This is good to have.
 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

And these:

 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
supergrub itself is tiny, other supergrub versions are larger
      
 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by sports fan Matt on 2013-06-12
Once I get my 12.04 CD tomorrow I'll take a look at things. I figure at worst with the CD I can delete the Ubuntu partitions and then start again with 12.04.  (Off topic, hope the storms were not too bad)  I grew up northwest of the city so know it all too well.

---

### Post by oldfred on 2013-06-12
We just got a good heavy rain. 
Local reporting shows other areas in Chicago getting hail and severe storms, so it seems to depend on exactly where you are.

---

### Post by sports fan Matt on 2013-06-12
Yeah, I grew up in Crystal Lake.  When I get my CD tomorrow i'll run a shot with GParted and then wait to see what should be done :)

---

### Post by sports fan Matt on 2013-06-12
One thing I'm seeing from Easeus, the 305.28 GB Partition is my Ubuntu 13.04 install. 100.13 is my 12.04 precise install. and 80.15 is my W7 partition. Could I wipe the 30.82 GB partition (which belongs to something for Windows) and have it added to my 80.15 GB W7 install?  the 305.28 GB Partition is my Ubuntu 13.04 install which I can delete if need be (I want to use 12.04 anyway).

---

### Post by Irihapeti on 2013-06-12
According to the GParted screenshot, the 30.82 is blank space which was originally occupied by the W7 partition. If Easeus will let you add it back safely, you could do that. Just make sure that the power doesn't go off part way through. That's not good for partition health.

Re your earlier riddle, it might have been because Windows can sometimes need to run CHKDSK twice (or even more often) before it can boot properly. I vaguely remember that happening when I fiddled with my Vista partition years ago.

---

### Post by sports fan Matt on 2013-06-12
The other allocated space is also part of W7..It is what I used to attempt to have W7 have more space in the first place.

---

### Post by sports fan Matt on 2013-06-12
...and if I want to delete the 305.28 space that should be OK?

---

### Post by Irihapeti on 2013-06-12
The 305.28 looks like an Ubuntu partition. It all depends what's on it.

But, since you have your files backed up and you're expecting a disk in the mail shortly, if you do delete the wrong Ubuntu partition, it probably doesn't matter too much.

---

### Post by sports fan Matt on 2013-06-12
it is.  That's Ubuntu 13.04 on 305.28 partition.  12.04 is the 100 gb partition.

---

### Post by sports fan Matt on 2013-06-13
I have learned partitioning.  I slid it over to have about 150 GB for Windows from 80 (system booted right up).  Now I guess tomorrow I can try and figure out how to remove the allocated 305.28 space that was my 13.04 install.

---

### Post by sports fan Matt on 2013-06-13
So my disk failed to arrive today.  I'm going to take these matters into my own hands (W7 is working) so I'll just reinstall W7 when it's backed up anmd install Ubuntu at a later date.  (Yes I know this is drastic, but productivity has been nothing the last three days work wise).

---

### Post by sports fan Matt on 2013-06-13
(Not trying to be harsh of course)  Just have been losing work days. :) When my 12.04 disk arrives I shall reinstall.

---

### Post by sports fan Matt on 2013-06-13
I tried one last time to install 12.04 from a blank disc and it worked! Now the question is can I run boot repair on this or would it be just easier to  reinstall everything since I've got everything backed up and have disks.  what do you recommend?

---

### Post by Irihapeti on 2013-06-13
Can you boot from a 12.04 liveCD? You can install boot repair to the liveCD, though of course it won't persist after a reboot i.e. if you need to use the boot repair in the liveCD again, you'll need to reinstall it.

Instructions for doing this are at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sports fan Matt on 2013-06-13
I'm on onecurrently as I burned it.  I'm running a Boot repair  (it's scanning the systems)

---

### Post by sports fan Matt on 2013-06-13
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2          30,876,936   339,244,604   308,367,669   7 NTFS / exFAT / HPFS
/dev/sda3       1,221,519,360 1,250,263,039    28,743,680  17 Hidden NTFS / HPFS
/dev/sda4         339,244,606 1,221,518,339   882,273,734   f W95 Extended (LBA)
/dev/sda5         339,244,731   549,230,219   209,985,489  83 Linux
/dev/sda6       1,189,452,663 1,205,485,469    16,032,807  82 Linux swap / Solaris
/dev/sda7       1,205,485,533 1,221,518,339    16,032,807  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        02A4FE2BA4FE20B9                       ntfs       System
/dev/sda2        8E103FE9103FD6C5                       ntfs       TI106400W0E
/dev/sda3        0A7267AD72679C67                       ntfs       HDDRECOVERY
/dev/sda5        65a3d4cb-4ebe-42cd-bbdc-e4e4acf26cd8   ext4       
/dev/sda6        76f2dd6a-89b4-43c1-8979-135b66270344   swap       
/dev/sda7        29aee42d-d086-4f0e-ad82-396e0b6100dc   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04.2 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

---

### Post by Irihapeti on 2013-06-13
That looks like what I would have expected.

At the moment, exactly what is/isn't happening? What is booting successfully? What isn't?

I've not used boot repair. But I think there's an option to fix things. In the absence of oldfred, you could try running it if you need to.

---

### Post by sports fan Matt on 2013-06-13
Nothing Ubuntu related will boot.  W7 boots but has only 125 gb's space.  (So I'm wondering if it's easier to run a boot repair and go that way, because I'd rather have 12.04 installed then 13.04).

---

### Post by Irihapeti on 2013-06-13
You could go ahead and run it and see what happens. Ultimately, it's your decision.

---

### Post by oldfred on 2013-06-13
When you say Ubuntu does not boot, you are getting grub menu. Then it may be video issue or other boot parameter required. If you get grub menu then Boto-Repair will not be able to do much as you are booting grub and it is kernel or drivers issues. It can add a nomodeset if you need that.

What video card/chip?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sports fan Matt on 2013-06-13
Going to try and install 12.04 then delete 13.04...Then i'll figure about W7's space

---

### Post by sports fan Matt on 2013-06-13
Old Fred,

I was able to successfully boot and create a Ubuntu 12.04 disk.  I have now realized in my boot info script that I have 13.04 on SDA 5.  Would it be worth it it scrap 13.04, and reinstall 12.04 with my CD that I downloaded?

---

### Post by oldfred on 2013-06-13
In my 640GB drive I have several installs all in 25GB / (root) partitions with all my data in two 100GB data partitions. So you can replace 13.04 or install 12.04 in addition.

---

### Post by sports fan Matt on 2013-06-14
Has anyone used "OS Uninstaller?"  I downloaded it but need to see where where I'd need to format my SDA 5 partition to delete 13.04 and keep 12.04 (definately NTFS but NTFS fast or just NTFS)?

---

### Post by Irihapeti on 2013-06-14
For any Linux stuff, you can use GParted. You can remove and replace partitions with it before installing. When you install, grub should take care of the bootup side of things. If things are a bit messed up after installing, that's when you use Boot-repair.

---

### Post by oldfred on 2013-06-14
Like Irihapeti I prefer to use gparted. And I like to label my partitions, usually with gparted, but when I forget to label one, I use Disks or Disk Utility. But I do not use Disks for any other partition type changes as some have had issues with certain configurations.

---

### Post by sports fan Matt on 2013-06-14
Going to mark this solved.  I was able to get back all my space..One small question.  What is a good size to reinstall 12.04 at from my disk?  Going to include all my Windows items.  (25, 30 gb.) 100, 150?

---

### Post by oldfred on 2013-06-14
Partitioning is very personal as it depends on how you are using system. Even my own best optimal partitioning plan is not so good  a year or two later as I have changed what I am doing. 

One suggestion:

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by sports fan Matt on 2013-06-15
My HD is a 640 GB hard drive...Since I only want 12.04 and W7 on it

---

