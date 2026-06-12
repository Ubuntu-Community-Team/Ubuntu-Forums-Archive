---
title: "Compressing a dd image in a way that allows mounting"
date: 2014-08-20
forum: General Help
---

### Post by terminator14 on 2014-08-20
One of the best techniques for backing up any linux system (in terms of data integrity) is dd.
No matter what OS(s) you have, what boot loader you have or how it's configured, whether you have a USB, HDD, SSD, CD, or DVD, an MBR or GPT partition table, or almost anything else, dd will back it up.

Everyone knows the downsides of using dd for backups:
[LIST]
[*]	It takes forever for obvious reasons
[*]	It's backups are huge for obvious reasons
[*]	If you want to compress it later, you need to fill the empty space with zeros ahead of time, which also takes a while
[/LIST]

A big advantage of dd backups however, is the ability to mount the dd image, giving you access to individual files from the backup. You would think that this would be something that every backup solution offered, but last I checked, many standard tools admins use to backup linux drives/partitions (partclone, partimage, etc.) do NOT allow you to restore files separately.

Another great thing you can do with dd is compress the image on the fly by piping the output of dd through a compression algorithm. This can be done with 7zip, gzip, zip, rar, or bzip2, as seen here: [https://wiki.archlinux.org/index.php/disk_cloning](https://wiki.archlinux.org/index.php/disk_cloning)

Unfortunately, using ANY compression algorithm I've ever come across on a dd image pretty much means you can no longer mount it to retrieve individual files.
The only way to compress a dd image while still being able to mount it that I've ever seen is mksquashfs.

Using squashfs to compress a dd image has 2 big disadvantages:
	[LIST=1]
[*]Apparently, there's no way to pipe dd output to mksquashfs.
[INDENT]This means if you're backing up a 500GB drive (which is small by today's standards), you basically need to create a 500GB dd image, wait until that finishes, and then start compressing it with mksquashfs, and wait until that finishes. Not only can you not do these tasks in parallel, but the temporary space you need to do the backup = FULL_SIZE_OF_HDD_OR_PARTITION_YOU_WANT_BACKED_UP + COMPRESSED_SIZE_OF_THE_SAME_HDD_OR_PARTITION_YOU_WANT_BACKED_UP. If you happen to only have 30GB worth of stuff on your 500GB hard drive, you will need about 520GB of temp space, assuming your 30GB can compress to about 20GB. In contrast, if you were to pipe the dd output to gzip (for example), it would take a long time (as it processes the entire 500GB), but you would only ever need the 20GB of space to store your backup.
[/INDENT][*]To mount the dd image, you have to mount the squashfs image, and then mount the dd image from inside of that. This isn't a huge problem, but is annoying
[/LIST]

So my question is this: Is there a way to compress a dd image on the fly, while still retaining the ability to mount the compressed image so that individual files can be read and restored?
I basically want to get rid of dd's "It's backups are huge" disadvantage while not effecting it's "it can be mounted" advantage.

Note: I think I've clearly outlined the advantages and disadvantages of dd above - repeating them in the replies is not going to make me reconsider using dd for backups, so please don't turn this thread into a place to argue for your favorate backup software - I'm aware that dd isn't the only backup solution out there, and that it's disadvantages make it unpopular with many people.

---

### Post by sudodus on 2014-08-20
This is interesting :-)

I have scripts using the method you describe including zeroizing free space to make compressed dd images with gzip and xz. And I reverse the process to create cloned systems (using [mkusb]("https://help.ubuntu.com/community/mkusb")). But I have not found any shortcut, to mount the compressed image. I'm afraid most such tools would need expanding the compressed dd image in order to use it. And then you need the space anyway, which is possible for small systems for USB pendrives, but not for your example with a 500 GB HDD.

So my solution to your problem is simply to ***expand it to a mass storage device, a 'drive', and to mount partitions as usual*** (on that drive). I know that you are good at using ramdrives, and with enough RAM, that method might be a good solution (***expanding into a ramdrive***).

I can also mount/map an expanded image file (file.img.xz --> file.img) as a USB device in a ***KVM & virt-manager*** virtual machine. It works quite well.

---

### Post by terminator14 on 2014-08-20
Expanding into a ram drive might work for a very small backup (like you said - USB drives), but even the most RAM-filled system (mine has 16GB) has no where near the room to expand a full blown 500GB hard drive (which, again, is pretty small for an HDD). Even a backup of a very small SSD (32GB) would be way too big to fit on a RAM disk of most systems.

When you say "I know that you are good at using ramdrives", I assume you mean this: [http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694). That project uses mksquashfs to boot from a compressed filesystem. Using mksquashfs is possible on dd drives, but has the disadvantages I outlined above.

And ya - expanding to a temporary drive is possible, but it has 2 huge disadvantages.

Ex: If you have a compressed dd image of a small, 500GB drive and you want to recover a 500 byte config file, or worse yet, check if the backup has the 500 byte config file you're looking for because you're not sure, you have to:

[LIST=1]
[*]find 500GB of temporary storage
[*]wait until 500GB extracts to the temporary storage
[/LIST]

Compared to the convenience of a regular dd image that you can mount in 2 seconds, this is terrible.

Is there some rule of nature that prevents compressed archives from being mountable?
Is it because compressed images stop being block files?

---

### Post by sudodus on 2014-08-20
> **terminator14 said:**
>  ...
Ex: If you have a compressed dd image of a small, 500GB drive and you want to recover a 500 byte config file, or worse yet, check if the backup has the 500 byte config file you're looking for because you're not sure, you have to:

[LIST=1]
[*]find 500GB of temporary storage 
[*]wait until 500GB extracts to the temporary storage 
[/LIST]

Compared to the convenience of a regular dd image that you can mount in 2 seconds, this is terrible.
Yes, but at least you need not store the huge uncompressed file for a long time. For fast access, I think uncompressed alternatives are the best.> 
Is there some rule of nature that prevents compressed archives from being mountable?
Probably not. You have succeeded with squashfs. Was that with a 500 GB drive, or only a small one (like an iso file for an installer)?

 -o-

Compressed tarballs can be browsed easily with ***file-roller***. ***tar*** makes an archive, that is supposed to be easy to manage. And except for the bootloader and partition table, linux systems work well, when restored from a tarball. I use this feature in the [One Button Installer]("https://help.ubuntu.com/community/OBI").

But I know, you wrote that this is not what you want.

-o-

***Let us hope we get a good tip from someone reading this thread :-)***

---

### Post by sudodus on 2014-08-20
> **terminator14 said:**
> ...
Is it because compressed images stop being block files?

Maybe this is the problem. So if we can find a compression system, that preserves some structure, it might work.

---

### Post by terminator14 on 2014-08-20
> **sudodus said:**
> Yes, but at least you need not store the huge uncompressed file for a long time.
True

> **sudodus said:**
> You have succeeded with squashfs. Was that with a 500 GB drive, or only a small one (like an iso file for an installer)?
I've seen people suggest the method online, but it's disadvantages kept me from trying it. I'm pretty sure it works with any sized disk.

> **sudodus said:**
> Compressed tarballs can be browsed easily with ***file-roller***. ***tar*** makes an archive, that is supposed to be easy to manage. And except for the bootloader and partition table, linux systems work well, when restored from a tarball.
I'm not 100% sure on this, but I think that compressed tarballs work on smaller archives well, but get much worse on massive files. I've seen file-roller take several minutes to open up an archive (not extract - just show its contents) on a relatively fast computer because the archive had a lot of subfolders with files (I think it was the sources for the kernel, or a full linux backup or something). I'm pretty sure that compressed archives like .tar.gz need to be read fully by the system before you can be given a list of its contents. That works for small archives, or even ones that are several GB in size (modern systems can read several GB pretty quickly), but once you start hitting 100s of GB archives, I think gz is no longer a viable option. If anyone knows that this is or is not true, please let us know. I'll see if I can look this up later.

> **sudodus said:**
> ***Let us hope we get a good tip from someone reading this thread :-)***

Yup - that's what I was hoping for :)

Also, I think I may have stumbled onto something interesting:

[QUOTE=http://unix.stackexchange.com/a/75590]**Streaming Compression**

To avoid making a separate temporary file the full size of the disk, you can stream into a squashfs image.

```
mkdir empty-dir
mksquashfs empty-dir squash.img -p 'sda_backup.img f 444 root root dd if=/dev/sda bs=4M'
```
[/QUOTE]

I was under the impression that you couldn't stream into a squashfs image, but I suppose that was only because I hadn't seen it done before.
I gotta try this out.

---

### Post by sudodus on 2014-08-20
Great, let us hope you find it possible to stream into  a squashfs image :-)

---

### Post by terminator14 on 2014-08-20
Apparently, as of squashfs tools 4.0, mksquashfs supports pseudo-files.
As a result, incredibly, the following does actually work:

[QUOTE=http://unix.stackexchange.com/a/75590]**Streaming Compression**

To avoid making a separate temporary file the full size of the disk, you can stream into a squashfs image.

```
mkdir empty-dir
mksquashfs empty-dir squash.img -p 'sda_backup.img f 444 root root dd if=/dev/sda bs=4M'
```
[/QUOTE]

The pseudo-files option of mksquashfs is explained here: [http://sourceforge.net/p/squashfs/mailman/message/22031858/](http://sourceforge.net/p/squashfs/mailman/message/22031858/)
And this link has a few examples: [https://tjaldur.nl:8443/repos/gpltool/trunk/bat-extratools/squashfs4.2/pseudo-file.example](https://tjaldur.nl:8443/repos/gpltool/trunk/bat-extratools/squashfs4.2/pseudo-file.example)

But basically:

**empty-dir** - "source" dir. Basically in our case, just an empty dir to satisfy mksquashfs' input arg format
**squash.img** - the destination and filename of the output squashfs file
**sda_backup.img** - the name of the dd backup INSIDE the squashfs file
**f** - specifies that sda_backup.img is a regular file (as opposed to a directory, block device, or char device)
**444** - permissions of the sda_backup.img file inside the squashfs image
**root root** - UID and GID for the sda_backup.img file inside the squashfs image. Can be specified by decimal numbers, or by name
**dd if=/dev/sda bs=4M** - the dd command used to read the device we want backed up

**Note**: Unfortunately, squashfs filesystems are read only (unless you do some trickery with Unionfs), so keep that in mind.

**GETTING ACCESS TO YOUR DD IMAGE:**

To access your dd image (sda_backup.img), mount the squashfs image (squash.img):

```
sudo mount squash.img /mnt
```

now you have your read-only dd image at /mnt/sda_backup.img, which you can do with what you normally would with a dd image:

**DD image is of a partition**

[INDENT]Either do a full recovery:[/INDENT]
[INDENT]```
# WARNING: Don't run this dd command unless you know exactly what it's doing
sudo dd if=/mnt/sda_backup.img of=/dev/sdaX bs=4M
```[/INDENT]
[INDENT]Or mount it[/INDENT]
[INDENT]```
sudo mount /mnt/sda_backup.img /some/mount/point
```[/INDENT]
[INDENT]now you have access to your files at /some/mount/point.[/INDENT]
[INDENT]At this point, you can either browse to /some/mount/point to find/recover files individually, or use rsync to do a fast recovery:[/INDENT]
[INDENT]```
sudo rsync -n -aAXSH -hv --delete --progress --stats /some/mount/point/ /path/to/mounted/original/fs --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*",/lost+found}
```[/INDENT]
[INDENT]The "-n" will make sure that the only thing that happens on the first run is rsync telling you what it will do. Remove "-n" when satisfied that it'll do what you expect.[/INDENT]

**DD image is of a full drive**

[INDENT]Either do a full recovery:[/INDENT]
[INDENT]```
# WARNING: Don't run this dd command unless you know exactly what it's doing
sudo dd if=/mnt/sda_backup.img of=/dev/sda bs=4M
```[/INDENT]
[INDENT]OR attach your dd image to the first available loop device:
```
sudo losetup -f /mnt/sda_backup.img
```
See which loop device it attached to:
```
sudo losetup -a
```
Tell the kernel to scan the loop device for partitions:
```
sudo kpartx -a /dev/loopX
OR
sudo partprobe /dev/loopX
```
Now you have access to those partitions under /dev/mapper/loop...
You can mount them to gain access to the files:
```
sudo mount /dev/mapper/loopXpY /partition/mount/point
```

If one of those partitions has LVM, it will either automatically show up under /dev/mapper/, or you must do:

```
sudo vgscan
sudo vgchange -ay
```

to have it show up.
[/INDENT]

---

### Post by sudodus on 2014-08-21
This is great news :-)

Please also describe how to mount it in order to access the backed up files.

---

### Post by terminator14 on 2014-08-21
> **sudodus said:**
> Please also describe how to mount it in order to access the backed up files.


I think that covers it :)

---

### Post by sudodus on 2014-08-21
Yes, it looks quite complete. I have only read it, but I will certainly try it.

Thanks a lot for sharing your solution :KS

---

