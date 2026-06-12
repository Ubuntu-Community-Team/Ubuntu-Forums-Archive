---
title: "Partioning + Organization with Ubuntu / Windows"
date: 2008-05-29
forum: General Help
---

### Post by deadimp on 2008-05-29
I recently made the full switch to Ubuntu from Windows about two months ago.

I have a few questions regarding how / if I should partition my drives:

I have two hard drives - a 300GB SATA for my OS's and their installed programs, and a 500GB SATA for my own data (development, school, random files).
The 300GB has three partitions in this order: 1 ntfs (WinXP), 1 ext3 (Ubuntu), 1 swap
The 500GB has one partiton: 1 ntfs
I've probably used under 50GB's total, so temporarily moving / copying stuff shouldn't be a problem.

Should I go ahead and reformat the 500GB to ext3?
I ask this because I feel like I should be using ext3 to make sure that I can manage permissions and all that myself.
To do this, I'll end up copying everything to the 300GB, and then reformat the 500GB, and copy back. I was thinking about partitioning the 500GB and moving stuff around with that, but it could potentially take more time to reorganize.

Should I reorganize the placement of my partitions?
I know it seems like kind of a moot point, but both the Windows and Ubuntu partitions have the same size. I might need to resize the Ubuntu partition, and I'm guessing that shrinking / moving the smaller partition (with Windows) and just resizing the larger one (Ubuntu) will be faster than the other way around.


Also, I don't really use Windows that much, but I need it since I'm going to start an internship with a company that does development on Windows.

---

### Post by deadimp on 2008-06-02
4 Days...
*bump*

---

### Post by jualin on 2008-06-02
The only problem with reformatting the 500GB to ext3 is that you are not going to be able to use it from Windows since Windows doesnt "know" that it exists, so I wouldn't do that if you want to access the files from that partition from Windows. Now about the resizing the Windows and the Ubuntu partition, do you feel that you are running out of space. If you do then go ahead and resize your partitions, however if feel that everything is working fine I would not risk resizing your partition since sometimes resizing might make the system not boot up. Hope this helps!

---

### Post by deadimp on 2008-06-03
I'm not even near running out of space on either partitions, so I guess I won't bother with the risk.

As for Windows recognizing ext3, it's not of great importance since I hardly boot into it. However, I know of several drivers for Windows for the ext2 file system - which works since ext3 since ext3 is derrived from ext2. I used Ext2 IFS [ [http://www.fs-driver.org/](http://www.fs-driver.org/) ] which seemed to work pretty well a while back, especially since I could specify drive letters. I was able to browse through my root Ubuntu file system.
I just googled 'ext2 fs' and also found a SFNet project [ [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd) ], but it seems a little young so I'll probably end up going with the freeware driver.

---

### Post by forestpixie on 2008-06-03
They seem ok as it is if you ask me - I probably wouldn't bother and would probably leave the ntfs as it is and access it from buntu. But if you do, I would move files away and delete and reformat rather than resizing partitions with data on - I know that it cantake a long time to do.

I assume you've read the ext2ifs and permissions stuff, it could cause problems - but I have never needed to do it so that's not first hand.

I've seen resizing go for over a day - so I would shy away from any great amounts of file movement during resize operations.

---

