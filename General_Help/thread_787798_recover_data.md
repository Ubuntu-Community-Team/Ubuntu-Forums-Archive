---
title: "recover data"
date: 2008-05-09
forum: General Help
---

### Post by Theleo on 2008-05-09
I managed to fdisk one of my hard drives that contained most of my data.
Have tried testdisk,diskinternals linux recovery,r-studio,Nucleus kernel linux.No luck.the filesystem on the disk was ext3.Any help,ideas would be appreciated

---

### Post by Moop on 2008-05-09
You can try this guide. [http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html]("http://www.xs4all.nl/%7Ecarlo17/howto/undelete_ext3.html")

---

### Post by cdenley on 2008-05-09
Did you just repartition? Did any data get written outside the partition table? Do you remember how your disk was partitioned?

---

### Post by Theleo on 2008-05-12
Hi guys thanks for the replies.


> [http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)
looks good but it will take me some time to digest and use it.Defenitelly will try for the fun of it if nothing else.

> Did you just repartition? Did any data get written outside the partition table? Do you remember how your disk was partitioned?

i formated my disk from bash using fdisk.
i answered the questions as usuall just gave the wrong disk and
then i told it to write  to disk.i had only one partition on the
disk /dev/sdc1 (an ext3 partition).

> I have used Stellar phoneix linux recovery software that helps in recovering data from Ext2, Ext3 & Reiser file system.

Running it the past 13 hours.seems to be recovering files here and there.All files are separed by type,i am guessing it uses magic numbers to find files inside the raw data of my disk.Big files like videos are each on seperate folders and broken in 2kb sizes.Wonder if it will join them later or i will do it manually?
unfortunatelly it can recover no file names.Guess u cant have it all.

---

### Post by cdenley on 2008-05-12
Did you try running fdisk again to recreate the original partitioning scheme? Since fdisk only changes the partition table, you should still be able to mount the filesystem if you tell it where to find it. If you post the output for this command, I could probably determine the correct offset. I think it varies from one drive to the next.

```

sudo od -N 5242880 -x /dev/sdc | grep "ef53 0001"

```

This command would work for my disk
```

sudo mkdir /media/recover
sudo mount /dev/sdc /media/recover -o offset=32256

```

---

### Post by Theleo on 2008-05-13
> od -N 5242880 -x /dev/sdc | grep "ef53 0001"

and here is my output.
0101060 caba 4829 0002 0023 ef53 0001 0001 0000

forgot to mention that after i fdisk the /dev/sdc
i did put a filesystem on it with...
mkfs -t ext2 -j /dev/sdc1

---

### Post by cdenley on 2008-05-13
> **Theleo said:**
> and here is my output.
0101060 caba 4829 0002 0023 ef53 0001 0001 0000

forgot to mention that after i fdisk the /dev/sdc
i did put a filesystem on it with...
mkfs -t ext2 -j /dev/sdc1

In that case, your filesystem is gone, and I think the only way to recover files would be tools like the one mentioned or photorec from the testdisk package. I think all the file paths/names would have been erased when you formatted it to ext2, so all there is left is the actual data.

---

### Post by az on 2008-05-15
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

---

### Post by Theleo on 2008-05-18
> [http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)
Tried most of the tools there.
Cant seem to be able to recover filenames,perhaps the only way
is 

> [http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)
but it is out of my league for the moment.
Since we are talking about mp3,photos etc mostly; it will be really time consuming to recover 100,000 files and examine them one by one to find out what is in each one.

I ll bite the bullet,

Thanks again for all the help guys appreciated.

---

