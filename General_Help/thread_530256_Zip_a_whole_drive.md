---
title: "Zip a whole drive"
date: 2007-08-20
forum: General Help
---

### Post by shavenlunatic on 2007-08-20
Hi,

I have a relatively fresh install of Ubuntu with the basics installed and set up exactly how I want it... 

I do like to play though, and I am prone to screwing things beyong a point of no return.. 

basically, as I have only took up about 9gb of a 120GB HDD with my current install (apps, backgrounds, essential downloads etc.) I would like to ZIP the whole HD.. (i have a storage drive in this pc too)

I know it's possible to create an ISO of the HDD, but this will be the same size as the HDD and I simply don't have 120GB to spare ... plus it seems inneficcient to make an ISO of this size when there's only 9GB of data :)

basically.. i wanna "zip hda1 > mystuff.zip"  (or whatever compression software makes sense... ), so I have ALL my software, installs and settings preserved

I didn't wanna go down the ghost route as it just doesn't seem to do what I was hoping for..

any ideas?

thanks in advance

---

### Post by Ted_Smith on 2007-08-20
gzip /dev/hda1 hda1.tar.gz

(check which way round they go - cannot remember off the top of my head and looks up options for compression etc)

or

rsync -arpgtvz /dev/hda1 MountsFolder/MyExternaLdRIVE The -a invokes 'archive'. By far the most useful option is -a (--archive). The other switches retain permissions, group permissions, compresses, gives you verbose output etc. See 'man rsync' for more details. 

Ted

---

### Post by southernman on 2007-08-20
another option is this link:

[How to backup and restore your system]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by jakev383 on 2007-08-20
It's some more work, but I back up my drives over the local network to my RAID system.  I use the System Rescue CD to create images of my partitions (it only uses what you've used).  The link is here:
[www.sysresccd.org](www.sysresccd.org)

---

### Post by southernman on 2007-08-20
> **jakev383 said:**
> It's some more work, but I back up my drives over the local network to my RAID system.  I use the System Rescue CD to create images of my partitions (it only uses what you've used).  The link is here:
[www.sysresccd.org](www.sysresccd.org)That's a very good tool to have in your arsenal for a variety of things... I use it too.

---

### Post by shavenlunatic on 2007-08-20
don't have a network at home.. so that's out of the question

will have a play with the zip command though, thanks :)

incidentally.. will it gzip to an ntfs drive or will it be best to gzip it to a linux drive and copy the gzip file over? (my storage is ntfs so it can be shared by both o/s)

---

### Post by shavenlunatic on 2007-08-20
```
shavenlunatic@shitheap:~$ sudo gzip /dev/hda1 hda1.tar.gz
gzip: /dev/hda1 is not a directory or a regular file - ignored
gzip: hda1.tar.gz: No such file or directory
```

:(



currently reading thread posted by southernman.. cheers, will post results :)

---

### Post by southernman on 2007-08-20
Do let us know. It will work like a champ as long as you have write support to your ntfs storage.

> incidentally.. will it gzip to an ntfs drive or will it be best to gzip it to a linux drive and copy the gzip file over? (my storage is ntfs so it can be shared by both o/s)It should work fine, providing you have ntfs-3g installed... least I think it will.

---

### Post by shavenlunatic on 2007-08-21
> **southernman said:**
> another option is this link:

[How to backup and restore your system]("http://ubuntuforums.org/showthread.php?t=81311")

this worked like a charm, didn't go for high compression but I think I'll create another one tomorrow night and see how small I can get the tar file

thanks much for everyones advice :)

---

