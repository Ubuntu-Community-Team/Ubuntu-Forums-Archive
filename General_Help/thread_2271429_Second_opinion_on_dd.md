---
title: "Second opinion on dd"
date: 2015-03-30
forum: General Help
---

### Post by s.fox on 2015-03-30
Hello everyone,

I'm trying to create an image of a partition using dd. I have read some horror stories on the topic so I would very much value a second opinion.

This is my setup:

```
-sh-3.00$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            237152860  86503024 138603096  39% /
/dev/sda1               101086     92498      3369  97% /boot
none                    517204         0    517204   0% /dev/shm
/dev/sda2              2063536     45988   1912724   3% /tmp

```

I am trying to backup /dev/sda5.  This makes me believe this should work:

```
dd if=/dev/sda5 of=~/sda5disk.img
```

Does this look okay to you?

Many Thanks :)

---

### Post by sudodus on 2015-03-30
No, it would make an image of /dev/sda5 onto itself. But there are better ways than using dd for that purpose. dd is slow and dangerous.

You can use ***rsync*** or ***Clonezilla***, which would not copy the free space of the partition.

Why do you want to backup only sda5?

You can also use some GUI front end using rsync (or a small script if you prefer command line tools).

You can also make a ***tarball***, a compressed tar file.

***Edit***: dd can be used, but you should not read from a mounted partition or a device with mounted partitions. And you should write to another device (or at least another partition). Typically, boot from an external drive when making an image of the internal drive.

---

### Post by kerry_s on 2015-03-30
that is going to take forever, then fail.
your copying a huge disk to the same disk, not enough space will be the error.
are you using standard ubuntu ? you can use settings-> backup or disks-> create image
but your going to need an equal amount of space to put it.
it's been a long held practice just to back up home, 1 folder & you can compress it if need be.

---

### Post by s.fox on 2015-03-30
Thanks all for the advice :)

CloneZilla might be better suited to my needs afterall. Thank you for the suggestion.  Just reading into it now.

The reason I only want sda5 is because that is where /home is.  I don't really want to keep anything else.

Thanks also for catching the space problem, that would have been an issue. I'll get that sorted with another hdd and adding a partition :)

---

### Post by The Cog on 2015-03-30
I would suggest using tar as this will:
* only copy used files (not the empty disk space), 
* will not try to copy its own output file (you are writing to the filesystem you are trying to image)
* will use compression to reduce the output file size

```
sudo tar -czf sda5disk.tar.gz --one-file-system /
```

The one-file-system option stops it from descenting into /proc, /sys etc.
I have succesfully restored  a system from a tar file before, and booted it succesfully.

EDIT:
You replied while I was typing the above reply.
If you only want /home, then I would definitely use tar like this:
```
sudo tar -czf sda5home.tar.gz /home
```

---

### Post by Bucky Ball on 2015-03-30
Hey, s.fox, these might help on your Clonezilla trek:

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

I have these links in Zim for these very occasions. ;)

One thing to remember is that if you clone a 50Gb partition with only 20Gb on it, you need to clone it back to a 50Gb partition, regardless. I thought Clonezilla did clone unused space because of this fact. Happy to be enlightened.

---

### Post by s.fox on 2015-03-30
> **The Cog said:**
> I would suggest using tar as this will:
* only copy used files (not the empty disk space), 
* will not try to copy its own output file (you are writing to the filesystem you are trying to image)
* will use compression to reduce the output file size

```
sudo tar -czf sda5disk.tar.gz --one-file-system /
```

The one-file-system option stops it from descenting into /proc, /sys etc.
I have succesfully restored  a system from a tar file before, and booted it succesfully.

EDIT:
You replied while I was typing the above reply.
If you only want /home, then I would definitely use tar like this:
```
sudo tar -czf sda5home.tar.gz --one-file-system /home
```

Thanks, will it actually fit on the same partition?  If it will then this looks ideal to me.  df indicates that I've used 39% of /sda5 but i'm not sure I understand the blocks info.  The used appears to be a lot more than 39%.

---

### Post by sudodus on 2015-03-30
> **s.fox said:**
> [QUOTE=The Cog;13255351]I would suggest using tar as this will:
* only copy used files (not the empty disk space), 
* will not try to copy its own output file (you are writing to the filesystem you are trying to image)
* will use compression to reduce the output file size

```
sudo tar -czf sda5disk.tar.gz --one-file-system /
```

The one-file-system option stops it from descenting into /proc, /sys etc.
I have succesfully restored  a system from a tar file before, and booted it succesfully.

EDIT:
You replied while I was typing the above reply.
If you only want /home, then I would definitely use tar like this:
```
sudo tar -czf sda5home.tar.gz --one-file-system /home
```

Thanks, will it actually fit on the same partition?  If it will then  this looks ideal to me.  df indicates that I've used 39% of /sda5 but  i'm not sure I understand the blocks info.  The used appears to be a lot  more than 39%.[/QUOTE]

The Cog's command line is good, if you must write to the same partition. You might get the message 'tar: .: file changed as we read it' because the target file is in the source directory.

But there are better ways to make backups

1 - If the file system is corrupted, it would be better to have the backup in another partition.

2 - If the drive is damaged (electronically or mechanically) or stolen or burned in a fire, it would be better to have the backup in another drive, even in another house.

So I suggest that you get an external drive for your backup.

---

### Post by s.fox on 2015-04-01
> **sudodus said:**
> The Cog's command line is good, if you must write to the same partition. You might get the message 'tar: .: file changed as we read it' because the target file is in the source directory.

Wouldn't the --one-file-system argument stop this?

> **sudodus said:**
> 
1 - If the file system is corrupted, it would be better to have the backup in another partition.

2 - If the drive is damaged (electronically or mechanically) or stolen or burned in a fire, it would be better to have the backup in another drive, even in another house.


Thankfully the system is not corrupt, neither is the drive damaged. :)

So willl it fit?  I'm concerned by df showing 39% used, but blocks used seems to be a lot more. 

Thanks again for all the help everyone

---

### Post by sudodus on 2015-04-01
> **s.fox said:**
> Thankfully the system is not corrupt, neither is the drive damaged. :)

The system is good now and the drive is good now, but if you need the backup because of a damage, and the backup is lost too ... :-(
> 
So willl it fit?  I'm concerned by df showing 39% used, but blocks used seems to be a lot more. 

Thanks again for all the help everyone

A compressed image will need less space than than it's source, and the source is the /home directory tree with files, which contains less than 39 % of the drive space. So the compressed image will need [much] less than that, and the available drive space is 61 %, so according to ***df***, yes. You should always have at least 10% free space to avoid fragmented files.

Maybe it is easier to interpret the output of

```
df -h   # in Gibibytes, Mibybytes ...
```

---

### Post by s.fox on 2015-04-01
Ah, I see what you are saying now. The backup will not be kept on the same box for very long at all so I am not super concerned.

Going for human readible on df shows it will fit. I think I need to look into blocks though, the original output still concerns me. 

```
-sh-3.00$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             227G   83G  133G  39% /

```

Thanks again for the quick reply :)

---

### Post by sudodus on 2015-04-01
> **s.fox said:**
> Hello everyone,

I'm trying to create an image of a partition using dd. I have read some horror stories on the topic so I would very much value a second opinion.

This is my setup:

```
-sh-3.00$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            237152860  86503024 138603096  39% /

```


Also here, {used: [COLOR=#0000ff]86[/COLOR][COLOR=#ff0000]503[/COLOR]024} is less than {available: [COLOR=#0000ff]138[/COLOR][COLOR=#ff0000]603[/COLOR]096}

---

### Post by s.fox on 2015-04-01
> **sudodus said:**
> Also here, {used: [COLOR=#0000ff]86[/COLOR][COLOR=#ff0000]503[/COLOR]024} is less than {available: [COLOR=#0000ff]138[/COLOR][COLOR=#ff0000]603[/COLOR]096}

**Edit**

Got my head around it, misunderstanding the output on the blocks. Thank you :)

I was reading available as the total! D'oh ;)

---

### Post by sudodus on 2015-04-01
You are welcome :-) Good luck with the tarball, and remember to copy it somewhere else before you need it ;-)

---

