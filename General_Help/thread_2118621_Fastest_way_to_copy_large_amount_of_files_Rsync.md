---
title: "Fastest way to copy large amount of files? Rsync?"
date: 2013-02-21
forum: General Help
---

### Post by MrsUser on 2013-02-21
I'd like to copy a folder with all subfolders/files in it from partition sdc1 to partition sdb1. File permissions do not have to be kept as I copy from an NTFS drive. Nautilus will do the job, of course. But I wonder if there is a faster method to copy a large amount of data, assumably via command line? If possible, it should also give feedback about the progress. I had a look at rsync which seems to be a good choice. However, I wonder what's the _fastest_ way.

---

### Post by papibe on 2013-02-21
Hi MrsUser.

You can use 'cp' or 'rsync'. I don't think there's much performance difference between them (when rsync is used for coping). If I have to guess, I'd say cp is faster.

A copy using 'cp':
```
cp -ivpr source/ destination/
```
**However**, for a large  directory tree, I would always prefer rsync because in case of any error, recovering with rsync would be a breeze (you just run it again).

A typical'rsync' command would be:
```
rsync -av source/ destination/
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by JiuJitsu500 on 2013-02-21
The fastest way is not really limited by software, as nautilus is only an overlay of the command you'd use in a terminal anyway. GUI apps are all just that, running commands and scripts while you see yourself doing something else graphically.

The fastest way would prbably be though nautilus so you can at least see what's going on and progress, but a simple "mv /pathtofile/tocopy/ormove /pathto/destination" will also do the trick, but in the background that's the command nautilus uses when you say "move to folder."

live media might be faster since both the copied/moved file and destination are mounts and not the OS though... and flash will always be much faster than a rotational disk. Hardware is what limits this in the end, software can only be tuned to use the best efficiency of the hardware. a 6.0GB/s SSD will never be able to transfer at 6GB/s (relative speed) if the controller is maxed at Gen 2 3GB/s (relative speed)...

technology is awesome.

Oh, besides though, fastest means more room for error. Naultilus or a "mv" or "cp" command will be just fine and leave very little room for error as long as the system stays on. Faster than what they choose to move at may lead to serious corruption.

rsync is something I don't use, but it wouldn't be any better or faster than what nautilus can do.

---

### Post by markbl on 2013-02-21
> **papibe said:**
> 
A typical'rsync' command would be:
```
rsync -av source/ destination/
```

Actually I would instead say a typical rsync command would be:
```

rsync -av --delete source/ destination/

```
I.e. often/normally you are intending a duplicated copy of the source dir so you also want files that were deleted in the source dir to be deleted in the destination dir. Unless it is a one off copy, rsync is better than cp because it only copies the changes and works the same over a network.

Note when I type the above rsync command manually I always add a "-n" the first go to check what it will do before it does anything.

---

### Post by MrsUser on 2013-02-21
I'll give rsync a try:
```
rsync -av --progress '/path to/the source folder' '/path to/the destination folder'
```The -n option is also very useful, by the way. Nice to see what will be copied before actually copying.

```
rsync -n -av --progress '/path to/the source folder' '/path to/the destination folder'
```And as you can see I put the path as a string by using " **'** ". I just tried it without and it didn't work, because some directory names have blanks. Then I put it as string and now it works.

Thanks a lot to you all! :popcorn:

-----------

EDIT:

> **papibe said:**
> **However**, for a large  directory tree, I  would always prefer rsync because in case of any error, recovering with  rsync would be a breeze (you just run it again).


Just out of curiosity -- how does rsync keep track of already copied files? And do I not have to use the -P option then?

---

### Post by dcstar on 2013-02-21
> **MrsUser said:**
> I'd like to copy a folder with all subfolders/files in it from partition sdc1 to partition sdb1.** File permissions do not have to be kept as I copy from an NTFS drive**. Nautilus will do the job, of course. But I wonder if there is a faster method to copy a large amount of data, assumably via command line? If possible, it should also give feedback about the progress. I had a look at rsync which seems to be a good choice. However, I wonder what's the _fastest_ way.

Copying anything to/from NTFS in Linux is compromised because it is a non-Linux filesystem. People continually report that NTFS file IO is way slower than native Linux IO.

---

### Post by papibe on 2013-02-21
> **MrsUser said:**
> how does rsync keep track of already copied files?
It only does it on the fly while it's being run. The basic algorithm is based in filename, size, and modification date (although it can be tweak a bit).

> **MrsUser said:**
> And do I not have to use the -P option then?
Option -P implies two options --partial and --progress.

'progress' works wonders when you are transferring big files. If you are transferring lots of medium to small files, I would recommend using only the verbose option (-v).

'partial' is always useful. It doesn't add too much value if you are transferring small to medium size files. Its true value applies when transferring big files and/or when transferring over a network.

Does that help?
Regards.

---

### Post by CharlesA on 2013-02-21
> **papibe said:**
> It only does it on the fly while it's being run. The basic algorithm is based in filename, size, and modification date (although it can be tweak a bit).

Indeed. You can also tell rsync to do it by checksum:
```
 -c, --checksum              skip based on checksum, not mod-time & size
```

But it can be considerably slower due to having to calculator the checksum of the source and destination files.

I've always run rsync like this:

```
rsync -ai --delete /path/to/source /path/to/destination
```

I don't have quotes around anything and it seems to handle spaces just fine.

---

### Post by MrsUser on 2013-02-22
> **CharlesA said:**
> 
I've always run rsync like this:
```
rsync -ai --delete /path/to/source /path/to/destination
```I don't have quotes around anything and it seems to handle spaces just fine.
What's the -i parameter for?

---

### Post by schragge on 2013-02-22
From *man rsync*
> -i, --itemize-changes
           output a change-summary for all updates

---

### Post by thermion on 2013-02-22
rsync is a bit slower than cp, but it has several advantages and is in general more secure.
I like to run rsync this way:

[I]rsync -avx --progress --compress-level=0 --exclude=.*

[/I]The exclude part saves you much trouble if you have to deal with MacOS metadata on your volumes.

---

### Post by CharlesA on 2013-02-22
> **MrsUser said:**
> What's the -i parameter for?

> **schragge said:**
> From *man rsync*

What they said ^.

It makes the output look like this:

```
charles@Thor:~$ rsync -ai --dry-run scripts/* /tmp/
>f+++++++++ bdupdate.sh
>f+++++++++ bitscan.sh
>f+++++++++ check.sh
>f+++++++++ daily.sh
>f+++++++++ dvds.sh
>f+++++++++ full.sh
>f+++++++++ monthly.sh
>f+++++++++ notify.sh
>f+++++++++ offsite.sh
>f+++++++++ smart.sh
```

> **thermion said:**
> rsync is a bit slower than cp, but it has several advantages and is in general more secure.
I like to run rsync this way:

[I]rsync -avx --progress --compress-level=0 --exclude=.*

[/I]The exclude part saves you much trouble if you have to deal with MacOS metadata on your volumes.

Looks like --progress shows a little less info than -i, but shows the total bytes sent and received, which is kinda cool.

---

