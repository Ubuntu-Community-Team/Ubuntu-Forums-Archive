---
title: "How to Copy files from one hard drive to another and skip bad files"
date: 2008-06-27
forum: General Help
---

### Post by jcdlinux on 2008-06-27
Hi,

I have been using Ubuntu for a while, but I am still new at it. The thing is I have a Hard Drive laying around which has some files I wanted to back up on a DVD (the HDD has Windows XP, and occasionally clicks) I hooked it up and started Ubuntu to transfer those files from the bad drive to a folder on Ubuntu. When transferring Ubuntu freezes for a while and stops the transfer, when I tried the transfer to another Drive containing Windows XP I get a CRC error (cycling redundancy Check Error) under windows so I cant get the files out of the drive. 
I would like to know if there is any software that I can use in Ubuntu to skip those files that are bad and continue copying without aborting the transfer. I really don't mind losing some of files, but would like to get back the majority of them. Any simple to use solutions will be very grateful.

Thanks in advance for any help

---

### Post by unutbu on 2008-06-27
Have you tried 

```
sudo /sbin/dosfsck /dev/sda?
```

where /dev/sda? is replaced with the device name for your WinXP drive. There is also a way to run fsck from within WinXP. I think you boot the WinXP CD, select recovery mode and then type ```
/chkdsk drive /r
```
See [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

> 
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also **marks any bad sectors** and it recovers readable information.

You can use the following options:
/p : Does an exhaustive check of the drive and corrects any errors.
/r : Locates bad sectors and recovers readable information. 
Note If you specify the /r option, the /p option is implied.



Then perhaps try making a backup of the drive with clonezilla ([http://www.clonezilla.org/](http://www.clonezilla.org/)).

If that does not work (and it very well may not),
then the only other thing I can think of is to copy-by-bisection. That is, select roughly half the files on the WinXP drive and see if you can copy just half. If it succeeds, try to copy the other half. If a particular half-copy fails, then bisect it into two pieces and try to copy each piece separately. Repeat ad nauseum.

---

### Post by jcdlinux on 2008-06-27
Hello,
Well ive tried the method of copying half of the files but it fails when it encounters a corrupt file, I would like to know if there is something thet can skip the bad file and continue copying the rest, something like Ycopy for Windows but for ubuntu (I tried ycopy in windows xp but it freezes).
Like i said I am new at usind ubuntu and I realy don't understand these command codes, could you explain how to copy using the code?
Thanks

---

### Post by Rick Myers on 2008-06-27
As a former data recovery tech I suggest, you stop what you are doing if you want to keep your files.

You need another drive the same size or larger to image/clone the bad drive to. Use dd to copy the disk sector for sector to another drive. Then mount clone drive to copy the files off.

You'll find some data recovery information on my site [http://www.microswamp.com](http://www.microswamp.com) under Tech Notes/Data Recovery.

---

### Post by unutbu on 2008-06-27
Have you booted from the Windows CD and run the chkdsk
command? If not, I'd do that first, because the documentation says that it can identify and mark badblocks. It that succeeds, then you can copy by any method (such as nautilus).

---

### Post by jcdlinux on 2008-06-27
> **Rick Myers said:**
> As a former data recovery tech I suggest, you stop what you are doing if you want to keep your files.

You need another drive the same size or larger to image/clone the bad drive to. Use dd to copy the disk sector for sector to another drive. Then mount clone drive to copy the files off.

You'll find some data recovery information on my site [http://www.microswamp.com](http://www.microswamp.com) under Tech Notes/Data Recovery.

Should I fist clone the drive using something like colnezilla, and by using dd...what is it, how does it work? Could someone give me the steps for doing so, I am not really an experienced Ubuntu user. And I am very confused at this point :confused: 
Appreciate the help so far

---

### Post by unutbu on 2008-06-27
I've never used clonezilla, so I'm sorry I can't give you precise instructions. However, if you download and burn a clonezilla liveCD, from [http://www.clonezilla.org/download/sourceforge/](http://www.clonezilla.org/download/sourceforge/)

I think its use should be pretty straight-forward. 

While Rick Myers's advice to clone the drive first is technically correct, what are you going to do after you clone the drive? You'll probably run /chkdsk. If that doesn't work, then what? So what good will having a clone of your drive do? If you don't have a plan for that, then you might as well run /chkdsk first.

If it is very important to you that you extract as much data as possible, then I would urge you to clone the drive first. But since you wrote
> 
I really don't mind losing some of files, but would like to get back the majority of them.
it seems to me /chkdsk is the answer.

---

### Post by jcdlinux on 2008-06-27
Thanks for the help, I will see what chkdsk can tell me. Also, going back to my original question can anyone suggest a Ycopy alternative for Ubuntu or something like jfilerecovery, but that can copy complete folders and not one file at a time? I want to have a plan be if all suggestions fail.
Thank you guys for helping me out, if anyone can add any other suggestions I will be very greateful.
once again, Thanks!

---

### Post by unutbu on 2008-06-27
I don't know how this command will behave when it reaches a bad file, but it would under normal circumstances copy all directories recursively:

Suppose you have the windows drive mounted at /media/disk. Then

```

cd /media/disk
mkdir ~/rescue
find . -print0 | cpio --null --sparse -pvd ~/rescue

```
This hopefully will copy all good files on the WinXP drive to a subdirectory of your home directory called rescue.

---

### Post by Rick Myers on 2008-06-29
> While Rick Myers's advice to clone the drive first is technically correct, what are you going to do after you clone the drive? You'll probably run /chkdsk. If that doesn't work, then what? So what good will having a clone of your drive do? If you don't have a plan for that, then you might as well run /chkdsk first.

The objective to cloning the drive first is 2 fold. 1) If the drive has physical damage causing the bad blocks, running chkdsk on a physically sound cloned copy will allow chkdsk to do it's thing without the added complication of dealing with physical defects. 2) Cloning the drive is generally a read once routine over the media. Where using a disk repair utility will force retries over physically bad areas of a drive. Hence, cloning first will reduce the potential for increasing damage to the original media during recovery.

Really running a disk/filesystem repair util is a bad idea. I suggest running a data extraction util before running a disk/filesystem repair util. Something like R-Studio (sorry I don't know of an equiv. Linux util) which rebuilds the file system in memory or cache on a different disk. Then permits file/directory recovery based on the rebuilt file system. If results are poor after using an extraction util, then use a disk/filesystem repair util.

---

### Post by unutbu on 2008-06-29
I'm not familiar with R-Studio, nor any Linux equivalent.

Is R-Studio's method of rebuilding the filesystem superior to clonezilla + /chkdsk ?

---

### Post by Rick Myers on 2008-06-29
I've been out of the data recovery business for a year or so. Hadn't heard about clonezilla 'til this thread. I'll be tryin' it out. 

R-Studio doesn't do the cloning part. They have a cloning tool you could buy, however. 

With respect to quality of r-studio filesystem rebuild compared to chkdsk. Chkdsk is a pretty basic tool. It's not a fair comparison. R-Studio can do things chkdsk could never dream of.

---

### Post by xzyguest on 2010-01-03
I'm gonna borrow this thread for a (stupid) question. I feel a little ashamed asking this and please don't laugh, but how do I copy/paste files from a dvd to a hard drive? :oops:
I backed up my stuff when I left windows but now after selecting the files and hitting ctrl+c and then going to the drive and hitting ctrl+v...it just won't do it. I've also right clicked and the "paste" is blank.

---

### Post by r0g on 2010-09-04
And I'm going to re-hijack it to get things back on track!

There's still no answer to this question as far as I can see. I've ended up here 2 years later with the same request as the op. I'd never dreamed it would be so hard to find an error tolerant copier for linux - I can barely believe "ignore read errors" isn't an option for 'cp' or 'rsync'!

To people questioning the need for such a utility please consider...

a) There are several for that other operating system (including the cutting edge XCOPY utility!) and...

b) Some people (me for example) would like to be able to set a copy going and know that every readable file has been copied by the time it finishes i.e. A program that simply skips files that it can't read within a pretty brief timeframe, half a second of so. 

In my case I am working from a ddrescued image and I'd like to see how bad the damage is. If most of the data I want can be copied quickly or there are very few errors I can skip the fscking around and, as I don't entirely trust linux's write support for the disk format I'm using it spares me from having to sit around scratching my **** whilst a 250Gb image file backs up on my already busy system.

c) There are other uses too... On a badly failing had drive one might want to do a quick surgical copy of a few key files or folders as it may not survive the full imaging procedure.

To be honest I'm surprised not to find linux leading the way with a file level utility akin to GNU's excellent dd_rescue i.e. one that works with a log file and skips and re-queues troublesome files and folders.

I could write the easy/dumb version in an afternoon but I feel sure there must already be an app or a canonical way of using the common linux tools to skip read errors whilst copying, no?

Yours Hopefully,

Roger Heathcote

---

### Post by dcstar on 2010-09-04
> **r0g said:**
> And I'm going to re-hijack it to get things back on track!

There's still no answer to this question as far as I can see. I've ended up here 2 years later with the same request as the op. I'd never dreamed it would be so hard to find an error tolerant copier for linux - I can barely believe "ignore read errors" isn't an option for 'cp' or 'rsync'!

To people questioning the need for such a utility please consider...

a) There are several for that other operating system (including the cutting edge XCOPY utility!) and...

b) Some people (me for example) would like to be able to set a copy going and know that every readable file has been copied by the time it finishes i.e. A program that simply skips files that it can't read within a pretty brief timeframe, half a second of so. 

In my case I am working from a ddrescued image and I'd like to see how bad the damage is. If most of the data I want can be copied quickly or there are very few errors I can skip the fscking around and, as I don't entirely trust linux's write support for the disk format I'm using it spares me from having to sit around scratching my **** whilst a 250Gb image file backs up on my already busy system.

c) There are other uses too... On a badly failing had drive one might want to do a quick surgical copy of a few key files or folders as it may not survive the full imaging procedure.

To be honest I'm surprised not to find linux leading the way with a file level utility akin to GNU's excellent dd_rescue i.e. one that works with a log file and skips and re-queues troublesome files and folders.

I could write the easy/dumb version in an afternoon but I feel sure there must already be an app or a canonical way of using the common linux tools to skip read errors whilst copying, no?

Yours Hopefully,

Roger Heathcote

I suppose rdd-copy exists for a reason:

[http://www.digipedia.pl/man/doc/view/rdd-copy.1/](http://www.digipedia.pl/man/doc/view/rdd-copy.1/)

Install the rdd package and try it.

---

### Post by r0g on 2010-09-04
That's great thanks, I'll check it out, although I got frustrated and wrote my own before I got your message! 

It's not a thing of beauty so I won't pollute the forums with it but if anyone wants it (about 40 lines of python code, all core modules) shoot me an email to ubuntu-forum-stuff at technicalbloke.com

Thanks again dcstar :)

Roger.

---

