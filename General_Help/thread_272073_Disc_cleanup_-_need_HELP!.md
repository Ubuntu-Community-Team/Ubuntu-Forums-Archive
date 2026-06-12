---
title: "Disc cleanup - need HELP!"
date: 2006-10-05
forum: General Help
---

### Post by zugu on 2006-10-05
My filesystem is mounted on a root partition, and the /home directory is located separately, on another partition. I also have a swap partition.

I store everything important in /home. All the big files go there, along with all the multimedia, games - everything that is not part of the OS.

However, I have disc space issues on the root partition. The Ubuntu fresh installation had around 2.5 GB in size. Now is almost 5 GB, filling in the whole partition (which is, by the way, of 5 GB). I admit that I installed various things using apt-get, but I still have around 700 MB free.

However, if I use some filesharing clients on the /home partition (the clients run under Wine), I get messages telling me that I'm runnong out of space on the root partition. How is this possible? The client itself is located in the /home directory, and the download location is set on the /home partition too. What has this to do with the root partition? Why is the root partition filling up with stuff? It should't be involved at all. And after I finish the download, the free space is back, it's just incrementally less.

Could the /temp dir does this to me? Is it used as a buffer for every incoming file? Is it a sort of cache? If yes, how do I disable it?


Please help me, otherwise I will be forced to format the root prtition and reinstall Ubuntu.

---

### Post by kidders on 2006-10-05
Hi there,

Almost everything you do involves your "root" partition in some manner ... after all, the entire operating system is there. If you're running short on space, there are a few things you can check:

[LIST]
[*]Is your /tmp filling up with crap?
[*]Have you put anything large in /root that you don't need any more?
[*]Do you have the source code for more than one kernel installed?
[*]Is your /var/log drowning in archived system logs?
[/LIST]

To save more space, you could maybe delete your package cache.

> Could the /temp dir does this to me? Is it used as a buffer for every incoming file? Is it a sort of cache? If yes, how do I disable it?
Naturally, disabling the use of temporary file storage would completely cripple your system.

Imho, 5GB is *waaaaaay* too small for a functional desktop Ubuntu install. If I were in your situation, I would use **du** to identify the parts of my system that were becoming bloated and, assuming I couldn't thin them out, I'd consider moving things to other partitions. For instance, say I had a massive MySQL database or maybe a huge big website. I would create a new partition and move my /var into it, with the added bonus of being able to choose a filesystem specifically suited to what I wanted to store there.

For the sake of example:

```

cfdisk /dev/sda                  [ ... make a new partition, say, /dev/sda7 ]
mkreiserfs /dev/sda7
mkdir /mnt/newvar
mount /dev/sda7 !$
cp -dpR /var/* !$
umount !$ && rm -R !$
mv /var /oldvar && mkdir /var
chmod 755 /var

```

Then, you could add a new line for /var to your /etc/fstab, reboot, and (assuming nothing went pear-shaped) you'd be all set to **rm -Rf /oldvar**

I hope this is of some help.

---

### Post by zugu on 2006-10-09
Thank you for the advice. However, considering that a full Ubuntu install has around 2.5 GB, how is 5 GB insufficient? Don't get me wrong, I know Vista will need at least 10 GB to function properly, but c'mon! Why is so much space needed? I just don't get it. There is no swap file on the root partition, it is located in a separate partition. The basic system is using 2.5 GB and I just add multimedia support and a handful of small packages. Everything else is in /home, and /home is mounted on other partition.

Yet Ubuntu craves for more and more discspace. I do not find this normal.

And why do we need the /temp dir when we have the swap partition?

Cheers.

---

### Post by dcstar on 2006-10-09
> **zugu said:**
> 
......
And why do we need the /temp dir when we have the swap partition?

Cheers.

Swap is for the system to manage active processes, /temp is for whatever various bits of software you run.

---

### Post by kidders on 2006-10-09
> **zugu said:**
> Thank you for the advice. However, considering that a full Ubuntu install has around 2.5 GB, how is 5 GB insufficient? Don't get me wrong, I know Vista will need at least 10 GB to function properly, but c'mon! Why is so much space needed? I just don't get it. There is no swap file on the root partition, it is located in a separate partition. The basic system is using 2.5 GB and I just add multimedia support and a handful of small packages. Everything else is in /home, and /home is mounted on other partition.

Yet Ubuntu craves for more and more discspace. I do not find this normal.

And why do we need the /temp dir when we have the swap partition?

Cheers.

Hi again,

Most people like to give their operating system a little breathing room. It is nice, for instance, not to have to delete thumbnail caches, temporary internet files, etc., just to scrape together enough disk space to burn a DVD. Over time, people's OSs naturally tend to bloat a little, as they install more and more applications, perform system upgrades, and so on.

These days, now that disk space is so cheap, people have grown to like the idea of being able to consult system logs from 3 months ago, or enjoy the performance boost they get from using filesystem caches, without having to worry about how much room they take up. Windows for instance, requires that the amount of free disk space never fall below 15% to function effectively. In addition, the ability to undelete files depends on the presumtion that the disk blocks they used to occupy won't have been reclaimed by your system by the time you try to recover them.

With regard to your other question, all operating systems use both virtual RAM and temporary filestorage. As dcstar noted, they are entirely different things.

I hope that helps.

---

