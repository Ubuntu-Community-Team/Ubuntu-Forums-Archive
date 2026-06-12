---
title: "How do I resize a partition?"
date: 2007-01-12
forum: General Help
---

### Post by wersdaluv on 2007-01-12
I want to create a new partition by resizing my present partiotions but the resizing option is not available and I don't know why. What can I do?

I also have that "extended" file system and "linux-swap" file system but I don't know what they are. Do you know what those are?

After installing Ubuntu, I am still unsure if my old partitions still exist or they are really deleted. By the screenshot I attached, can you say if my old partitions are still there or not?

Also, is it completely safe for me to use gparted under KDE?

Edit: I just uploaded the screenshot I forgot to upload

---

### Post by mvaniersel on 2007-01-12
> **wersdaluv said:**
> I want to create a new partition by resizing my present partiotions but the resizing option is not available and I don't know why. What can I do?

I also have that "extended" file system and "linux-swap" file system but I don't know what they are. Do you know what those are?

After installing Ubuntu, I am still unsure if my old partitions still exist or they are really deleted. By the screenshot I attached, can you say if my old partitions are still there or not?

Also, is it completely safe for me to use gparted under KDE?


The resizing option can be not available for NTFS partitions if you haven't installed ntfsprogs. sudo apt-get install ntfsprogs will solve this problem (or use the live CD, see below)

ext3 is the standard filesystem used by linux, and the default for ubuntu partitions. linux-swap is a special filesystem used for swap space (to use as extra memory when your system runs out of physical memory). linux systems are usually configured with a small partition (250-1000 Mb) dedicated for swap space.

Yes, gparted can be used under KDE. But I advice you to run gparted from the live CD, because gparted doesn't work on mounted partitions.

---

### Post by wersdaluv on 2007-01-12
> **mvaniersel said:**
> The resizing option can be not available for NTFS partitions if you haven't installed ntfsprogs. sudo apt-get install ntfsprogs will solve this problem (or use the live CD, see below)

extended (ext3) is the standard filesystem used by linux, and the default for ubuntu partitions. linux-swap is a special filesystem used for swap space (to use as extra memory when your system runs out of physical memory). linux systems are usually configured with a small partition (250-1000 Mb) dedicated for swap space.

Yes, gparted can be used under KDE. But I advice you to run gparted from the live CD, because gparted doesn't work on mounted partitions.

Thank you very much! I'll try to do what you said.

---

### Post by mvaniersel on 2007-01-12
Oh, now that I see your screenshot:

An extended partition here is a partition to allow more than 4 partitions, I believe it is mainly a windows compatibility thing. Basically you can have only 4 logical partitions, but an extended partition can again be subdivided into an unlimited number of partitions, so that way you can get around the limit of 4.

---

### Post by wersdaluv on 2007-01-12
So does that mean that my old windows partition that I thought was deleted still exists?

---

### Post by ajgreeny on 2007-01-12
It's worth getting a copy of the live CD of gparted which is more recent than the version in ubuntu.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
It can do many things that ubuntu's version can't and is very useful to have around at all times anyway.

---

### Post by wersdaluv on 2007-01-12
Thanks. :) 

I'm currently downloading it.

---

### Post by bodhi.zazen on 2007-01-12
> **wersdaluv said:**
> So does that mean that my old windows partition that I thought was deleted still exists?

On the screen shot you have no windows partition.

You have a large primary partition hda1

and a small extended partition, hda2, which contains a logical partition, hda5

as mvaniersel said, you can not resize a mounted partition, in this case hda1.

The solution is to boot to a live CD, either the Ubuntu live Cd or the Gparted live Cd.

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by wersdaluv on 2007-01-13
How do I burn the GParted live CD on Kubuntu?

---

### Post by bodhi.zazen on 2007-01-13
k3b

---

### Post by wersdaluv on 2007-01-13
Is it really better to use the GParted Live CD than the Ubuntu live CD for editing partitions? It's because I'm having a hard time with the GParted Live CD. There was a point when the monitor displayed nothing.

---

### Post by mahiyar on 2007-01-13
You can also use the knoppix 6.01 live cd to carry out the same operations.

---

### Post by mvaniersel on 2007-01-13
> It's worth getting a copy of the live CD of gparted which is more recent than the version in ubuntu.

ajgreeny: is that actually worth the trouble? I've used gparted on the edgy (i.e. current) live CD a couple of times in the last past week, and it did the job very well. 

I mean, can you be specific about features in the latest gparted live CD that are important?

---

### Post by bigken on 2007-01-13
> **wersdaluv said:**
> Is it really better to use the GParted Live CD than the Ubuntu live CD for editing partitions? It's because I'm having a hard time with the GParted Live CD. There was a point when the monitor displayed nothing.

yes it is when you run the gparted liveCD there are no partions mounted so you  can prefrom the tasks required ;)

---

### Post by wersdaluv on 2007-01-13
> **bigken said:**
> yes it is when you run the gparted liveCD there are no partions mounted so you  can prefrom the tasks required ;)

So what do I do? There's nothing displayed on my monitor

---

### Post by wersdaluv on 2007-01-13
> **mvaniersel said:**
> ajgreeny: is that actually worth the trouble? I've used gparted on the edgy (i.e. current) live CD a couple of times in the last past week, and it did the job very well. 

I mean, can you be specific about features in the latest gparted live CD that are important?

So you mean, you are completely satisfied with Ubuntu Edgy Live CD's GParted?

---

### Post by bigken on 2007-01-13
how did you burn the iso

---

### Post by wersdaluv on 2007-01-13
> **bigken said:**
> how did you burn the iso

I used K3b and it went well

---

### Post by bigken on 2007-01-13
did select make disc from iso ?

---

### Post by wersdaluv on 2007-01-13
Yes.

Actually, I believe that the CD was burnt properly because when I booted it, it worked. It's just that, there was an instance when, after a step, the screen turned black and nothing appeared.

---

### Post by bigken on 2007-01-13
I would try another disc :-k

---

### Post by ajgreeny on 2007-01-13
> **wersdaluv said:**
> Is it really better to use the GParted Live CD than the Ubuntu live CD for editing partitions? It's because I'm having a hard time with the GParted Live CD. There was a point when the monitor displayed nothing.
I think it just has some operations that were not on the dapper live CD version of gparted, such as move partitions.  Anyway it is such a good and small CD that boots in seconds compared to the ubuntu live CD that is is worth having around.

---

### Post by wersdaluv on 2007-01-14
I had problems with the GParted live CD so I used the Ubuntu Edgy live cd instead and it went well!

---

### Post by bodhi.zazen on 2007-01-14
Hate it when that happens :p

Glad all is well, thanks for the update 8)

---

### Post by mvaniersel on 2007-01-15
> **wersdaluv said:**
> So you mean, you are completely satisfied with Ubuntu Edgy Live CD's GParted?

Yep, worked fine for me (on several occasions)

> **bigken said:**
> yes it is when you run the gparted liveCD there are no partions mounted so you  can prefrom the tasks required ;)

Idem dito for the edgy live CD :)

---

### Post by wersdaluv on 2007-01-16
Thanks guys! It worked! :)

---

