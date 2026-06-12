---
title: "[SOLVED] File system filled, won't release space"
date: 2008-05-08
forum: General Help
---

### Post by dbyrne on 2008-05-08
Help ! My /home file system filled up yesterday while I was playing with motion (created many .avi files in the movies directory).

I deleted the files (rm * at the shell prompt), but "df -k" still show 0k free, 100% full. I've since rebooted, which has made no difference.

I'm running 7.10, with the /home filesystem mounted on a RAID-1 device (/dev/md2), which is constructed on a pair of 300Gb Seagate Barracudas.

Any ideas how I can kick the system to recognise the free space ?

---

### Post by briandu on 2008-05-08
If I am not mistaken - all your deletes are in fact placed into the Wastebasket and NOT actually deleted. 

check your wastebasket and empty then the space will be reclaimed.

Oddly, you have to enable the "deleted" function in Hardy otherwise it all lands up in the Wastebasket.

Seems obvious I know but........

---

### Post by dbyrne on 2008-05-08
Is that the case for server edition ?

I've never come across the concept of a wastebasket in a raw unix system, other than where there's a file explorer/desktop in play. Can't imagine how that would work with a "rm *" from the command-line, how would you go about doing a command-line "empty wastebasket" ?

I'm running Gutsy, is there an equivalent of the "enabling the 'deleted' function" you mention in 7.10 edition ?

---

### Post by HermanAB on 2008-05-08
My guess is that you are using Ext3.  To fix that, you need to run fsck.  To do that on the / partition, you need to boot off a CD, for other partitions, you need to be in single user mode.

Cheers,

Herman

---

### Post by dbyrne on 2008-05-08
That's right, I'm running ext3 over RAID. Would you expect that to cause space not to be freed up when I delete files, or could you point me to some documentation on this ? I'd like to understand it a bit more as there are probably other features of ext3 that I don't realise.

I did think an fsck might sort it out, am currently trying to find out how to request an fsck at next reboot rather than doing another 20 reboots :) I can't really unmount the filesystem either to do a manual fsck, as the server is headless so if I go to single user there's no console to run the fsck from.

Thanks for your help.

---

### Post by dbyrne on 2008-05-08
More info:

I used "tunefs -c 2 -C 3 /dev/md2" to force an e2fsck on next reboot, and then rebooted. The /var/log/fsck/checkfs file confirms that the e2fsck ran successfully:

```

Log of fsck -C -R -A -a
Thu May  8 21:41:39 2008

fsck 1.40.2 (12-Jul-2007)
/dev/md2 has been mounted 3 times without being checked, check forced.
/dev/md2: 273096/29982720 files (3.8% non-contiguous), 59119896/59934464 blocks

Thu May  8 21:56:19 2008
----------------

```

However "df -k" still shows 0k available, 100% used (although there is a difference between Used and Available :confused:)

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md2             235974416 232560964         0 100% /home


```

---

### Post by dbyrne on 2008-05-09
More info:

I thought that given that the "Used" amount is reported as less than the "1-K blocks", there might actually be free space available and the "Available" figure might be reported wrongly.

However any attempt to use disk space results in failure:

```
$ ls -l x.dat
-rwxrwxrwx 1 dmb root 2995 2007-12-17 23:07 x.dat
$ cp y.jpg x.jpg
cp: writing `x.jpg': No space left on device
$ vi test.txt
E297: Write error in swap file

```

edit: more info, having deleted some more files the available space suddenly sprung above 0 bytes, and percentage used below 100% !

However "df -k" shows a discrepancy between 1K-blocks in total and (used + available) of 9Gb: I'd expect these to add up ?

$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md2             235974416 207952048  18432856  92% /home

Also for /home, "du -sk" reports 266,666,766, which is higher than the total vailable space reported by "df -k". I don't understand why this is, any ideas ?

---

### Post by dbyrne on 2008-05-09
OK, this is a very one-sided conversation, but in the hope that this might help someone in the same circumstances here's my guess at what happened :):

1. File system was gradually filling up anyway, with backups, shares etc.
2. It got to over 100%, then while I was messing around with motion, I filled up the rest of the extra 2.5Gb of *reserved blocks* !! I didn't realise that there's an automatic allocation of extra space when an ext3 filesystem is created, in retrospect it's the same as any other unix fs.
3. I deleted < 2.5Gb of avi files, but these came out of the reserved blocks, so "df -k" still showed 100%, and 0 blocks free (apart from the ones that I could have filled that were reserved)
4. Once I'd deleted over 2.5Gb worth, the free space registered on the output of "df" again.

I'm not absolutely sure if that's how Ubuntu behaves, but it makes sense.

I've now used "tune2fs -m 1 /dev/md2" to reduce the reserved blocks to 1% of the available space instead of the default 5%, which gives me an immediate 40Gb extra. Only user files are written to this fs, no root/system/logs so that should be fine. I might even set it to 0% ...

Now off to find out if there's any benefit to cutting the same percentage to zero for the swap partition.

edit: Can't do it, not allowed for swap. Question answered :lolflag:

---

### Post by fjgaude on 2008-05-09
My years of experience with ext2 and ext3 is that it is best to never use more than about 90% of the space leaving 10% free. If huge files are been stored, like movies of 5GB, then it might be best to consider what the free space size amounts to. All this is considering file fragmentation.

Google these filesystem types to understand how files are allocated to appreciate fragmentation.

---

### Post by dbyrne on 2008-05-10
Lots of stuff on the web to suggest that ext2/3 filesystems don't fragment much under normal circumstances, where 'normal' means with a reserve block, most seem to recommend 5% so I've gone back to that.

Thanks for the tip !

---

