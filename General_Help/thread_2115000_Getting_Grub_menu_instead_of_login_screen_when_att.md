---
title: "Getting Grub menu instead of login screen when attempting to log into Ubuntu."
date: 2013-02-11
forum: General Help
---

### Post by The Wolf on Red Street on 2013-02-11
Hi guys,


I've been hunting through the forums trying to find a solution to my problem, but so far I have been unsuccessful in fixing it.

First of all, I'm running Windows 7 and Ubuntu 12.10 (? I think) on a dual-boot system that apparently uses Wubi.

Recently, my computer has been getting dialog boxes saying there's a system bug and asking whether or not I want to report the problem. When I try to report the problem, an error message pops up (forgive me as I don't remember what exactly it said). 

The other day, the computer froze up - I did a manual shut down, turned it on again, and got to the dual boot menu. I selected Ubuntu, pressed enter, an error message flashed across the screen very briefly and then it sent me to the Grub menu, title as follows:

GNU GRUB VERSION 2.00-7ubuntu11
version 12.10-rev273


I pressed TAB, saw boot, typed in boot command and it said it couldn't find the kernel or something (sorry, not super versed in linux).


I have a lot of work that I've done over the past eleven days or so that is important to me, and I'm afraid of reinstalling Ubuntu and erasing my work. I want to completely eliminate Windows. I just don't know how to do that without screwing my documents over. 

If someone could help me it would be GREATLY appreciated.

---

### Post by bcbc on 2013-02-12
Try this: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

First run, chkdsk. Then try. You might also need to run fsck.

You could try to backup data using this tool (point it at the \ubuntu\disks\root.disk assuming it's still there and mountable): [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)

---

### Post by The Wolf on Red Street on 2013-02-12
> **bcbc said:**
> Try this: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

First run, chkdsk. Then try. You might also need to run fsck.

You could try to backup data using this tool (point it at the \ubuntu\disks\root.disk assuming it's still there and mountable): [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)


How do I run fsck?

I ran chkdsk again. Transferred dirs in found.0000 to disks. Still getting Grub. This stuff is giving me a headache, haha.

---

### Post by bcbc on 2013-02-12
You need to fsck from a live CD/USB. E.g. if you have an Ubuntu USB you should boot from it, mount the NTFS partition containing the root.disk and then fsck the root.disk.

To find out which partition, from grub:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```

That should spit out (HD0,MSDOS3) or something like that. Report back and create a bootable Ubuntu USB/DVD if you don't have one first.

PS there should have only have been one directory in the \found.000 file. Make sure you have an \ubuntu\disks\ directory containing the root.disk and swap.disk (and also an empty directory for boot containing just another empty directory - not important).

---

### Post by The Wolf on Red Street on 2013-02-12
> **bcbc said:**
> Try this: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

First run, chkdsk. Then try. You might also need to run fsck.

You could try to backup data using this tool (point it at the \ubuntu\disks\root.disk assuming it's still there and mountable): [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)


Also, I attempted to look in root.disk using that tool. It didn't appear to do anything, or there just isn't anything in root.disk (it's size is listed as 0KB)

---

### Post by bcbc on 2013-02-12
> **The Wolf on Red Street said:**
> Also, I attempted to look in root.disk using that tool. It didn't appear to do anything, or there just isn't anything in root.disk (it's size is listed as 0KB)

Well... that's not good.

---

### Post by bcbc on 2013-02-12
I don't think there's much you can do when the file size is 0KB - I've never seen anyone recover from that. 

You might be able to extract data using [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") (I'm not sure if it will pick up data from the raw blocks leftover from the root.disk). If the data you lost is extremely important it's worth a try, but be warned that photorec recovers a ton of stuff including things you previously deleted and there are no file names so you have to sift through them manually. It helps to limit the file types it recovers beforehand to specific things e.g. .jpg or .doc. etc. Unfortunately you'll get all sorts of rubbish as well e.g. from browser cache if you're looking for pics.

---

### Post by Mark Phelps on 2013-02-12
In the link, they renamed the found file to root.disk.  Did you try that?

---

### Post by The Wolf on Red Street on 2013-02-12
> **Mark Phelps said:**
> In the link, they renamed the found file to root.disk.  Did you try that?


No. Maybe I'll redo chkdsk and try that. I'm using that recovery program right now.

---

