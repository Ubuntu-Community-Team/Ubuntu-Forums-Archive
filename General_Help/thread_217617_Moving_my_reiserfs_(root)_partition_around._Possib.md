---
title: "Moving my reiserfs (root) partition around. Possible? Safe?"
date: 2006-07-17
forum: General Help
---

### Post by mycelo on 2006-07-17
I currently have 2 HDs, one (master, 120g) for WinXP with some NTFS partitions (games, mp3, etc) and another (slave, 40g) for my Ubuntu over reiserfs, swap and fat32 for sharing files with VoleWares. My Ubuntu sees his root partition as /dev/hdd2 and the XP's boot partition appears as /dev/hdc1.

Before Ubuntu, both HD's had a working MBR (the slave had a bootable DOS previously) and I noticed that Ubuntu installed Grub in both disks, for my suprise, even though I told my bios to boot from the slave. But no big deal, I just have to keep my slave disk plugged if I want to boot my from my master disk (since Grub will look for its data in the slave disk). Comments?

Anyway, now I have a brand-new third HD (250g) and I want to replace my old 40g slave disk. I plan to use Partition Magic or something to move ubuntu to my current master disk (120g) and grow it. So I'll have a master disk with my two OSes (60g XP ntfs, 60g Ubuntu reiserfs) and a non-bootable slave disk with fat32 for games and other huge things like DVD images, mp3, etc. I know that I can rebuild my Grub config/menu by forcing an Ubuntu reinstall without reformating its partition.

That said, I feel really unsure and I have some concerns:

1) Will I have some problem if Ubuntu root partition suddenly change from /dev/hdd2 to, say, /dev/hdc2? Does it have something "hard-coded" in its config files pointing to /dev/hdd2? And how about the installed apps?

2) Is it safe to rebuild the Grub config by reinstalling Ubuntu over an existing partition? Will it see my installed OSes and kernels?

3) Is it safe to copy/move/grow reiserfs partitions? Which is the recommended tool to safely accomplish this?

4) If reinstalling Ubuntu from scratch is a better solution, is it safe to copy my home directory so I can keep most of my configs, custom desktop settings, etc?

5) Any other advices?

Thanks in advance.

mycelo

---

### Post by mycelo on 2006-07-18
bump?

---

### Post by joft on 2006-07-18
Hi,

> **mycelo said:**
> 
1) Will I have some problem if Ubuntu root partition suddenly change from /dev/hdd2 to, say, /dev/hdc2? Does it have something "hard-coded" in its config files pointing to /dev/hdd2? And how about the installed apps?


If the device name changes, you will get problems - at least the device (/dev/hdXX) is used by GRUB, of course. So you need to reconfigure GRUB (/boot/grub/menu.lst) - and of course you have to install GRUB again (into MBR) since you have a new harddisk.
Last but not least the device name appears in /etc/fstab - where you should change it, too - also after moving.

> **mycelo said:**
> 
3) Is it safe to copy/move/grow reiserfs partitions? Which is the recommended tool to safely accomplish this?


I doubt that PartitionMagic is able to resize reiserfs. GParted is able to resize (see gparted's homepage [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php) ) reiserfs.
Usually I do this task by booting with a rescue system. From there I backup my root partition into a normal tar file. Then I create the new partition and untar the whole thing into it. Then I adjust etc/fstab and the GRUB config, "chroot" into the new partition and call "grub-install" .

> **mycelo said:**
> 
4) If reinstalling Ubuntu from scratch is a better solution, is it safe to copy my home directory so I can keep most of my configs, custom desktop settings, etc?


Yes, it's safe to do copy your home directory.

---

### Post by citylife on 2006-07-18
Thank you for your knowladge

---

### Post by mycelo on 2006-07-18
> **joft said:**
> If the device name changes, you will get problems - at least the device (/dev/hdXX) is used by GRUB, of course. So you need to reconfigure GRUB (/boot/grub/menu.lst) - and of course you have to install GRUB again (into MBR) since you have a new harddisk.
Last but not least the device name appears in /etc/fstab - where you should change it, too - also after moving.
Ok, but appart from Grub and fstab, where else I should expect problems?

> **joft said:**
> I doubt that PartitionMagic is able to resize reiserfs. GParted is able to resize (see gparted's homepage [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php) ) reiserfs.
Usually I do this task by booting with a rescue system. From there I backup my root partition into a normal tar file. Then I create the new partition and untar the whole thing into it. Then I adjust etc/fstab and the GRUB config, "chroot" into the new partition and call "grub-install".
And you do this with cat/dd command? Or?

> **joft said:**
> Yes, it's safe to do copy your home directory.
Thank you a lot, joft.

[EDIT] Btw, [this]("http://www.usalug.org/phpBB2/viewtopic.php?p=78936") thread seems to be helpful for this matter, hope it applies to my case. I really didn't find any complete solution in ubuntuforums.org.

---

### Post by joft on 2006-07-18
> **mycelo said:**
> Ok, but appart from Grub and fstab, where else I should expect problems?


I am not aware of any other places, where the device name might be stored (except in GRUB's config and /etc/fstab).
Ok, if you have setup RAID or something like that, the device name will appear in the RAID's config - but I assume that's not the case.

> **mycelo said:**
> 
And you do this with cat/dd command? Or?


No. As I already mentioned in my last post: I use "tar" to create a simple archive of the whole root partition. The important point is: I boot with a rescue CD (e.g. Knoppix, Timo's Rescue CD, ...) to avoid the problem of having to know what I have to exclude, because if you tar your root partition and also booted from it, you will have to make sure that you exclude specific files (/proc, /dev, ....). These specific files are in use then and tar'ing them doesn't work properly.
So, booting from such a rescue CD (or BTW: even a second ubtunu installation), mounting your old root partition and simply tar'ing it into a tar file on a FAT32 partition or some other partition is - IMO - the cleanest solution.

Then create your new partition, format (= "make filesystem") it, mount it and un'tar the tar file into it. Everything while being in the rescue system.

> **mycelo said:**
> 
[EDIT] Btw, [this]("http://www.usalug.org/phpBB2/viewtopic.php?p=78936") thread seems to be helpful for this matter, hope it applies to my case. I really didn't find any complete solution in ubuntuforums.org.

Well, it's similar. But if I see it right (the script), they make the backup from "the running" system, so they exclude the files I called "specific files" above ..... and IMO that's not clean - at least I wouldn't feel comfortable with that. Furthermore there might be Gentoo specific stuff ... :-k

---

### Post by mycelo on 2006-07-18
> **joft said:**
> I am not aware of any other places, where the device name might be stored (except in GRUB's config and /etc/fstab).
Ok, if you have setup RAID or something like that, the device name will appear in the RAID's config - but I assume that's not the case.
Sounds good. I am a Windows user and when you change, say, C: to D: it unleashes hell on you. That's the source of my concern.

> **joft said:**
> So, booting from such a rescue CD (or BTW: even a second ubtunu installation), mounting your old root partition and simply tar'ing it into a tar file on a FAT32 partition or some other partition is - IMO - the cleanest solution.
Good. That's also surprising for me, in Windows you can't just copy files from one partition to another.

This means that I can change my /root filesystem type, can't I? I'm dying to change back to ext3, I heard good things about reiserfs, but its tools seem to be somewhat experimental. e.g. I can't do a fsck to a partition mounted for r/w, I can't defrag, etc.

> **joft said:**
> Then create your new partition, format (= "make filesystem")
Or I could just use GPARTED from the live CD, right? (I'm a GUI guy)

> **joft said:**
> Well, it's similar. But if I see it right (the script), they make the backup from "the running" system, so they exclude the files I called "specific files" above ..... and IMO that's not clean - at least I wouldn't feel comfortable with that. Furthermore there might be Gentoo specific stuff ... :-k
No, no, sorry for not being clear enough, I'm talking about this command (which is meant to be run from a rescue system):

```
(cd /first-distro-root; tar cvpf - . ) | (cd /newmount; tar xvpf -)
```
Does that sounds safe for you?

Thank you for your endless patience again, joft, I appreciate.

---

### Post by SuSUntu on 2006-07-18
Re: ReiserFS resizing
 
I recently (successfully) re-sized and moved around a couple of ReiserFS partitions (Ubuntu 6.06 /usr & /opt). This particular PC currently has the following partition set-up:

sda - Windows, Program Files
1 Primary (NTFS)
1 Extended 
- 4 Logical (FAT32, NTFS)

sdb - documents, data, music, Ubuntu, etc.
1 Extended
- 12 Logical (FAT32, NTFS, ReiserFS)

hda - backups, disk images, etc.
1 Extended
- 2 Logical (FAT32, NTFS)


More specifically, the Linux partitions on "sdb" were as follows prior to re-sizing:

swap
/root 2000MB
/usr  4000MB 
/opt  4000MB
/var  1000MB
/home 4000MB

On other Linux distros I've used, /opt was utilized much more heavily than it is by Ubuntu, but I had initially stuck with my "standard" sizing so I could easily switch partition images out between distros if desired. However, with this Ubuntu installation, the /usr partition was rapidly getting filled while /opt was hardly used at all. So I decided to re-size.

Firstly, I thought it would be as simple as using GParted, so I downloaded the Live CD ISO and burned it to disk. After booting into the Live CD, which was easy enough, I realized that what I wanted to achieve wasn't possible with this utility. The goal was as follows:

re-size: /usr from: 4000MB to: 6000MB
re-size: /opt from: 4000MB to: 2000MB

While GParted would allow me to queue the shrinking process of /opt, it would only allow me to create the free space below (i.e., after) the /opt partition. This would have been fine if GParted would have allowed me to move the newly created free space ahead of /opt (and behind /usr) so I could then "grow" /usr. All the necessary options were available in GParted, but the frustrating part was that they were "grayed out" / inactive, so I could only get as far as queueing the re-sizing of /opt with a chunk of free space following that partition.

So, on to Phase II with my usual, trusty partitioning tool (the partitioning module in BootIt NG) PLUS resize_reiserfs. The main reason I didn't go this route to begin with is that BootIt NG required using two tools (its partitioner and resize_reiserfs). While I had been assured from a several sources that GParted would do all the processes transparently (the partition resizing and file system resizing), I could not get to that point as noted above.

Here's how I ultimately achieved my goal:

1. Created partition images just in case;

2.a. Booted from Stax Live CD (any CD with resize_reiserfs will do) ;
2.b. Unmount the /opt partition (if mounted):
umount /dev/sdb13
2.c. Shrink /opt's file system
resize_reiserfs -s -2000M /dev/sdb13
2.d. Reboot into BootIt NG;
2.e. Use BootIt NG to re-size /opt partition (-2000MB);
2.e. Use BootIt NG to move free space ahead of /opt (and behind /usr);

3.a. Use BootIt NG to re-size /usr partition (+2000MB)
3.b. Reboot into Stax Live CD
3.c. Unmount the /usr partition (if mounted):
umount /dev/sdb12
3.d. Grow /usr's file system
resize_reiserfs -s +2000M /dev/sdb13 

4. Reboot into Ubuntu - DONE

If your partition manager handles re-sizing the partition and re-sizing the file system transparently, then your work is simplified. BootIt NG is primarily a boot manager and secondarily a partition manager (as well as other things), so I don't fault it for requiring multiple steps on Linux ReiserFS partitions. It at least got the job done (and support docs explained how) whereas I could not get GParted to do what I needed. **By the way, here is an unsubstantiated caveat: some Linux partition managers are claimed to have trashed ReiserFS partitions because they required the two-step partition re-sizing + file system re-sizing process, but they attempted to re-size the partition without prompting / warning about the need to re-size the file system using a separate tool. I have read this, but have no direct knowledge of it actually occurring.** However, it does point out the inherent dangers in manipulating partitions in this way, so be sure that you have backups (or that you don't care if something goes wrong). However, based on the relatively trouble-free experience I had (plus having backup images), I wouldn't hestitate doing this process as often as required.

---

### Post by mycelo on 2006-07-19
> **SuSUntu said:**
> If your partition manager handles re-sizing the partition and re-sizing the file system transparently, then your work is simplified. BootIt NG is primarily a boot manager and secondarily a partition manager (as well as other things), so I don't fault it for requiring multiple steps on Linux ReiserFS partitions. It at least got the job done (and support docs explained how) whereas I could not get GParted to do what I needed. **By the way, here is an unsubstantiated caveat: some Linux partition managers are claimed to have trashed ReiserFS partitions because they required the two-step partition re-sizing + file system re-sizing process, but they attempted to re-size the partition without prompting / warning about the need to re-size the file system using a separate tool. I have read this, but have no direct knowledge of it actually occurring.** However, it does point out the inherent dangers in manipulating partitions in this way, so be sure that you have backups (or that you don't care if something goes wrong). However, based on the relatively trouble-free experience I had (plus having backup images), I wouldn't hestitate doing this process as often as required.
Nice, SuSUntu. I'm deciding if I'll make mirrors of my partitions or if I'll do a mere file-copy (tar, cp, wherever). The later seems to be easier and allows me to move things to a brand-new partition with any filesystem and size, and it would defragment my files as a bonus. However, I'm still not sure if a *tar* command would copy things exactly how they were, I have to learn something about this command first. I'm trying to understand the single-line script that I posted above, if I learn that it won't be assured enough, I'll try your method.

I'm also researching and deciding if I'll keep reiserfs or go back to the well-know ext3.

---

### Post by joft on 2006-07-19
> **mycelo said:**
> 
This means that I can change my /root filesystem type, can't I?


Yes, after creating a new partition - in theory - you can format it with any filesystem ubuntu supports for root filesystems.

> **mycelo said:**
> 
Or I could just use GPARTED from the live CD, right? (I'm a GUI guy)


Yes. Shouldn't be a problem.

> **mycelo said:**
> 
```
(cd /first-distro-root; tar cvpf - . ) | (cd /newmount; tar xvpf -)
```
Does that sounds safe for you?


Yes. Perfect, in fact that's the way I do it - except that I save the data into tar file and untar the file into the new partition (as I already wrote) ... but you can use the above line, too. There, the "tar file" exists in memory only and is directly piped (character | ) to the "untar" command (option x).

To learn more about "tar", do

```

man tar

```

---

### Post by mycelo on 2006-07-19
Well after lots of research and the great advices of the kind people in this thread, I think I'm going to recreate my partition in the new location and "tar" my files there, following joft unmistakable directions. Seem easy, safe and straightforward enough.

As for the filesystem choice, I'm going to keep reiserfs. My hours of research revealed that its reliability, recoverability, performance, space efficiency and compatibility are good enough for everyday desktop use.

---

### Post by mycelo on 2006-07-21
Last night I crossed my fingers and started messing with my partitions. As I said I decided to tar/untar my files into the new partition which I kept using reiserfs.

The direct-piped taring worked like a charm, I just didn't expect that many files from a recent installed distro. But that's ok, it took about 40 minutes to copy everything.

My big problem was when I tried to install Grub. That HD had a WinXP MBR, an NTFS partition and the new reiserfs partition. But for some reason, "grub-install /dev/hdc" (live CD chroot'ed into the just copied partition) immediately returned an "unknown format" error :confused: **Comments?**

I also tried reinstalling Ubuntu without formating (as I've read in other threads) with no avail, the installer crashed and screwed the partition, and the M$ MBR was still there.

Finally, I decided to reinstall Ubuntu with reiserfs from scratch. After confirming that it was bootable and working, firstly I backed-up the fstab and grub/menu.lst files to another partition. From the live CD I deleted all its files "rm -rd *" and performed again that command to tar-pipe all my files there again. Then I restored fstab (since my old fstab wasn't correspondent to my new drive/partition structure anymore). As for the grub/menu.lst, I had to kind of merge it with the old one, since it was pointing to an old kernel version (the one installed by live CD). So I adjusted the hd(x,x) things and the /dev/hdxx references in my old one.

Well, that worked :D, everything seems fine now. If someone is going through this, expect about 2-3 hours of work.

---

### Post by mycelo on 2006-08-03
Well it seems that Ubuntu writes its root physical location everywhere else. Now, whenever I reconfigure or upgrade my kernel, I have to manually change grub/menu.lst since it assumes the hdd(x,x) and /dev/hdxx as pointing to where I previously installed this distro.

So, where else should I change so it completely forgets about its previous drive/partiton?

mycelo

[UPDATE][Solution here.]("http://ubuntuforums.org/showthread.php?t=228001")

---

