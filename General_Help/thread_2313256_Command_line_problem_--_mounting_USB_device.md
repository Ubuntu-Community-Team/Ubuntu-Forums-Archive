---
title: "Command line problem -- mounting USB device"
date: 2016-02-10
forum: General Help
---

### Post by de Bacon on 2016-02-10
I am attempting to mount a usb drive with the command line.  I successfully did this one time in the past hour, but it won't work any more.

command used:    'mount -t LabelName'   where the label name is the name of the usb stick.  
 I have also used the option -L in the command since the original time when it worked.  That doesn't bring results either. 
I have tried using superuser in the attempts with this issue, still no success.  When it worked the one time, I did it without using the sudo prefix.  

At this point i am trying to prove I can do this before I actually do it in another OS where I have no GUI to look at file systems and the such thus the need to be able to do it in a terminal editor.  I did it once.  I mounted it, then unmouted it with command umount.  Then tried again but nothing happens when trying again.  

thanks,

---

### Post by saifulpbn on 2016-02-10
Hi Mr.

You can update your system and re-try !

Thanks

---

### Post by de Bacon on 2016-02-10
The system is updated

---

### Post by haplorrhine on 2016-02-11
How do you get the device name?  It might be listed in /media.

ls /media

---

### Post by de Bacon on 2016-02-11
It is listed in /media if it is mounted and has a partition Label.  

That doesn't help me a bit, I hope it did you though....

---

### Post by vasa1 on 2016-02-11
> **de Bacon said:**
> ... I hope it did you though....
No need for that please :)

---

### Post by de Bacon on 2016-02-11
> **vasa1 said:**
> No need for that please :)

It was a seriously stated comment.  Meaning, that I actually hope it answered the question that the person asked.

I am not trying to offend anyone here.  I am actually quite flummoxed in this situation.  I have tried so many different ways of writing out the command that will mount this USB drive and although it worked one time, I can't repeat that one time success.  It could be that I am going crazy, but I don't think so.  Something in the syntax I am attempting is incorrect, but I don't know what it is.  I keep looking for the answer, it has been many hours now looking through different websites that offer info on command line, but what I have seen doesn't make much sense yet and trying them has yet to resolve the question, "how to mount a usb drive from the command line.  

Again, I am frank, yet well intended.

---

### Post by QIII on 2016-02-11
Hello!

Can you have a look [here]("https://help.ubuntu.com/community/Mount/USB")?  This may not be new to you.

Judging from the abbreviated process you describe in your first post, I wonder if you hit all the points in the section "Manually Mounting".  That is, a file system type, a device and a directory to mount to.  There are shortcuts, of course, but the best thing to do sometimes is to do it all the long-hand way to make sure.

I have servers that I only interact with via SSH in the terminal.  I do not have problems mounting USB devices when using a formula similar to

```
sudo mount -t <file system type> /dev/<foo> /<some_directory>/<bar>
```

It only takes a simple thing one forgets sometimes to make things blow up.  We all do it.  Sometimes over and over until we slap ourselves on the forehead.  Show me someone tells you they don't make simple mistakes and get stuck in a rut thinking they are doing everything just right when they aren't -- and I'll show you a liar.  I have 3 leather bound Moleskine notebooks chock full of stuff that I forget from time to time and have to check my notes on.

---

### Post by de Bacon on 2016-02-11
QIII,
The link you provided is new information to me at least the source is.  I have much difficulty finding things with searches.  I speak a different language in my brain and can seldom find what I want and sit around for a day reading nonsense supplied that doesn't answer my situation.  I will look through it later today and see.  

I will say now in looking at the command you provided, there are things that I don't understand in the use of symbols, brackets and their ilk specifically.  I will look through it later today.  Life brings other demands for a while.

Thanks for the assist, hopefully I can figure it out.  If not, I'll be back with another description of the same.  I know it is my ignorance that stands between my situation and the solution.  I have no education in computers!

---

### Post by sudodus on 2016-02-11
you should replace <xxx> with an actual expression. I can give an example, but it might not work, because it must match a real file system and real directories in your computer. Sometimes the file system can be omitted, and the mount command will find it automatically. So for a FAT32 file system, you should use something like this:

1. create a mount point in the /mnt directory

```
sudo mkdir /mnt/one
```

2. mount the first partition in the drive b

```
sudo mount /dev/sdb1 /mnt/one
```

or (sometimes necessary)

```
sudo mount -t vfat /dev/sdb1 /mnt/one
```

From ```
man mount
```

we find possible file system types (vfat for FAT32)

```
       -t, --types vfstype
              The argument following the -t is used to indicate the filesystem type.   The  filesystem
              types  which  are currently supported include: adfs, affs, autofs, cifs, coda, coherent,
              cramfs, debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus, hpfs,  iso9660,  jfs,
              minix,  msdos,  ncpfs,  nfs,  nfs4,  ntfs, proc, qnx4, ramfs, reiserfs, romfs, squashfs,
              smbfs, sysv, tmpfs, ubifs, udf, ufs, umsdos, usbfs, vfat, xenix, xfs, xiafs.  Note  that
              coherent,  sysv  and xenix are equivalent and that xenix and coherent will be removed at
              some point in the future &#8212; use sysv instead. Since kernel version 2.1.21 the  types  ext
              and  xiafs  do  not exist anymore. Earlier, usbfs was known as usbdevfs.  Note, the real
              list of all supported filesystems depends on your kernel.
```[B][I]

Notice:[/I][/B] You must use the actual names of the file system and directories, I am only showing an example, and you may have to change it.

If you want help to identify what to write, please post the output of the following commands in a reply (mark and paste the text)

```
sudo parted -ls  # ... space minus ell ess

sudo lsblk -fm
```

---

### Post by de Bacon on 2016-02-11
QIII,

The answers I needed to resolve came through the link you provided.  It took a while to work through it, yet it worked out.  I learned some important methodology that I hope to never need again, but who knows. I have recorded this information in case I do need it again.  I have thus been able to accomplish the task that required this method of interface.  That blind sort of working remains odd to me, yet it is required now and again.  Thanks for the time to create the post of information for me.

sudodus,

 I also appreciate the information you passed along with an understanding of the time required to do the work you did in putting all that code together for me.  I am making record of it too as it can be valuable in the future if it is needed.

Thanks to all who took the time to read also.  This site is really a wonderful resource.  

Regards

---

