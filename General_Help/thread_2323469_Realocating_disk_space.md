---
title: "Realocating disk space"
date: 2016-05-05
forum: General Help
---

### Post by clonezonedude on 2016-05-05
Hello there

Well, it seems I messed up when installing ubuntu a couple of years ago, and now I'm paying for it dearly

I was using my ubuntu laptop normally, when I started to get notifications that I am out of HD space, when my machine came with nearly 1TB

I realized I have allocated my space badly, and my ubuntu partition is only 24gb while the rest is wasted

I was wondering. Is there a way I could reallocate the space on my ubuntu partition without having to reinstall the operating system please?

I tried GUI partition majic, but it doesnt do nada

Can somebody **Please** help me?

Thanks in advance :)

PS: How do I install the newest ubuntu version plz? (16.4 I think?)

---

### Post by Bashing-om on 2016-05-05
clonezonedude; Hello.

While RE-partitioning is certainly doable, it is not with out risk .
What 'might' be a better option is to look and see what should be removed . And maybe consider making up a "data" partition to hold large files .
Look and see:
```

df -h
df -i
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes, (The "x" switch limits du to a single file system, in this case the root file system.)

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
-----------------
A fresh install of 16.04 is better addressed in a separate thread . One problem/issue to the thread is protocol .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Impavidus on 2016-05-05
Add to those commands```
sudo parted -l
```to show us your current partitioning.

It may be convenient to create a data or home partition. That should be relatively straightforward.

If you run 14.04 and have set the upgrade manager to inform of LTS releases, it should offer the upgrade somewhere in July.

---

### Post by peter228 on 2016-05-06
So all you want to do is to reallocate space on the hard drive?  That is not hard...  I get myself out of this one now and again ....

1.  Boot the system to a memory stick / live CD

2.  launch gparted

3.  this will show you where the space is to be found

4.  use gparted to resize the partitions.

5.  Done

It is important to boot the system to external media because you cannot resize a partition if it is mounted (in use) and use of the external media will mean that gparted will be able to unmount the partitions for you ....

---

### Post by HermanAB on 2016-05-06
Or, use gparted or fdisk to partition and format the unused space and mount it as /data or whatever you want and start using it.

---

### Post by clonezonedude on 2016-06-28
> **peter228 said:**
> So all you want to do is to reallocate space on the hard drive?  That is not hard...  I get myself out of this one now and again ....

1.  Boot the system to a memory stick / live CD

2.  launch gparted

3.  this will show you where the space is to be found

4.  use gparted to resize the partitions.

5.  Done

It is important to boot the system to external media because you cannot resize a partition if it is mounted (in use) and use of the external media will mean that gparted will be able to unmount the partitions for you ....

Will this affect the main partition where I have my os mounted? (I'm afraid of losing everything, even with backup)

Sorry I took forever to answer... I got absorbed by work and a couple of cons ^^;

Thanks so far for all the help, everyone :)

---

### Post by clonezonedude on 2016-06-28
> **HermanAB said:**
> Or, use gparted or fdisk to partition and format the unused space and mount it as /data or whatever you want and start using it.

Will this allow me to expand my main (os) partition?

---

### Post by Impavidus on 2016-06-28
There are basically two things you can do. You can make your root partition (with all software and all documents) bigger, or you can create a new partition for all your documents and keep the software (the OS) in the current partition. That last approach has certain advantages, like making it easier to reinstall without wiping your data. The second approach is safer too, in the sense that it's less likely that some unforeseen problem destroys your entire system. I don't think the OS needs all 24 GB.

In post #2 and #3 were some requests for diagnostic data. Could you post the output? Keep in mind that the **sudo du** command may take a long time to run.

---

