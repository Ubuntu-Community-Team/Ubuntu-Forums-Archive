---
title: "Extending LEFT HAND Partition."
date: 2007-04-06
forum: General Help
---

### Post by Tufty on 2007-04-06
Not sure how to explain this! I have 4 partitions on my HDA.
The first is /dev hda1 NTFS windows 
Second is /dev/hda2 main ext3 for Ubuntu
Third is /dev/hda4 /home for my Linux files
Fourth is /dev/hda3 (/dev/hda5) Linux swap.

All has been fine until two days ago I needed more room in my Windows partition /dev/hda1

I've now spent those two days running various partitioning programs including under Linux GParted & under Windows Partition Magic Pro Version 8 but no matter what I do or how I try to do it I cannot find a way of moving some of the 70 gigabytes of free space I currently have into the windows partition.

Partition magic comes closest to being able to do this. One of it's wizards creates a list of 5 or 6 complicated partitioning instructions which fails after the first or second one.

I have loads of spare space at the right hand side of the graphic between hda4 and the linux swap which is at the right end of the graphic.
I seem to be able to stretch any of the linux partitions ONE WAY ONLY to the right.
Nothing allows me to actually MOVE any partition into the free space area so I can then extend the windows partition.

I hope this makes sense to someone! I'm so frustrated!!!!

I can do on-line MSN or yahoo chat if there is anyone out there willing to talk it over with me.

I can't believe there isn't a way to simply extend my windows partition without having to backup everything, wipe, re-format and re-partition the disk.
The space is there, how do I move the partitions?

Any help gratefully received.

Dave.

---

### Post by Tufty on 2007-04-06
Any takers on this one? 
It's driving me mad! I'm not going to be able to use the windows partition soon unless I can find a way of extending it.
:confused:

---

### Post by oerd on 2007-04-06
are you trying to shrink the windows partition and assing the free space to linux or the inverse? I can't gather it from your post. Whichever it is, the following thread will  give you some insight on how to shrink the windows partition and assing the resulting free space to a linux partition.

[http://ubuntuforums.org/showthread.php?t=114142&highlight=shrink+partition](http://ubuntuforums.org/showthread.php?t=114142&highlight=shrink+partition)

The inverse problem is very similar, and ```
man ntfsresize
``` gives a summary of how to proceed.

---

### Post by Tufty on 2007-04-06
The windows partition is full, the Linux partitions have oooodles of space. All that space is over on the right hand side. I can shrink Linux partitions to free up that space. I end up with a massive lump of free space on the **right hand side**, the only thing I am allowed to do with that is extend the linux partitions back into it as they are **in the way** between the windows partition and the free space.
I can't get the free space into a position where I can extend the windows partition into it, or move the windows partition to where the free space is.

In the past two days of trying everything I can, I can find no way at all of actually moving a partition. 

There never seems to be any arrows on the LEFT side of a partition to enable extension in that direction. I can't understand how I can get this free space into the windows partition.

I'll have a look at the link you advise, and report back here...

Thanks.



This probably all reads like complete rubbish!

---

### Post by Tufty on 2007-04-06
Hmmmmm... the advice about DiskDrake doesn't quite tie up.....
in the link you sent, the auther says:

"DiskDrake has always worked flawlessly for me. If you want to use it, here's what you do:

1. Go to the PCLinuxOS download page and download PCLinuxOS

2. Burn the ISO as a disk image

3. Reboot your computer from the CD"
.......................

When I go to the link s/he provides, I get :

 Parent Directory                                       -   
 livecd-TR3.iso                    04-Mar-2007 08:18  690M  
 livecd-TR3.md5sum                 04-Mar-2007 22:04   49  

No mention of DisDrake? is that what TR3.iso is? How do I tell?
If it is, then how do I 'Burn the ISO as a disk image' ?

---

### Post by mac.ryan on 2007-04-06
_I might be totally wrong_, but in my understanding:[LIST]
[*]Partitions have - at their beginning - a table where all the file names, permissions, path, are stored, together with the pointer to their first bit of data on the hard disk.
[*]In this table it is also said what is the area of the HD assigned to that specific partition.[/LIST]For this reason:[LIST]
[*]Extending (or shrinking) to the right is a rather trivial business: you simply have to change the "ending point" of the partition in the above mentioned table. (This - I assume - is why defragging is useful if you want to shrink it, given that defrag will "pile" all the data at the beginning of the partition)
[*]Extending (or shrinking) to the left is a rather complicated business: this operation would include to move the famous table, and possibly having to move part or all of the data bits on the HD. (This is not just a matter of amount of operations to do, but also - and above all - of how to do it in a safe way, for example in case of power failure...)[/LIST]Again, this is my understanding of how things work.... but I have no specific expertise in file systems, so...

---

### Post by Tufty on 2007-04-06
Your observations seem sensible to me... but I'm not sure how they help?
Are we coming closer to saying it's not possible or incredibly complicated to extend the windows partition if it is full and other partitions are between it and the free space?
So can it not be done?

---

### Post by oerd on 2007-04-06
I don't mean to be a fatalist, but from how i see if there was a solution, you had to provide free space in the **left hand side** of the linux partion. In this way you would shrink the ext partition from the left and then extend the ntfs partition. But that said, even that process is not that trivial.

btw, have you had a look at **ntfsprogs** ?

---

### Post by Tufty on 2007-04-06
All partitions (that I've ever seen in Linux & NTFS) seem to fill from left to right....
the empty space is NEVER on the left side of the partition.
But I could happily extend my NTFS partition to the right IF immediately to the right of it were free unallocated space.
I can easily make free unallocated space, but I can't move that space to be immediately to the right of the NTFS partition. Neither can I move the EXT3 partitions **into** (and so use up) the free space to their right. All I can do is EXTEND them, I can't MOVE them. So the free space seems to be ONLY available to the EXT3 partitions it is currently next to or within.

I've not yet read the reference you mentioned, partly because I'm new to this, and it doesn't seem to be clickable, and so I'm not sure just how I get to whatever it is you advise me to read.

---

### Post by mac.ryan on 2007-04-06
> **Tufty said:**
> Are we coming closer to saying it's not possible or incredibly complicated to extend the windows partition if it is full and other partitions are between it and the free space?

IMO probably yes. I can only think to workarounds for the moment:
[LIST=1]
[*]Reinstalling ubuntu in a new partition at the right of your HD, deleting the old one, and extending the NTFS onto that newly freed space.
[*]Creating a second NTFS partition in the space at the right of your HD and mounting that one in windows in some point that makes sense to you (for example you might wish to mount there your "my documents" folder, or part of it...)[/LIST]

---

### Post by Tufty on 2007-04-06
I'm finding this incredibly difficult to believe....
I fully expected someone to come forward & say something like "Ahhh ok this is what you need to do"
What we have is a hard disk with chucks of data and chunks of space.
Are we REALLY saying that no one has written any software that can organise those chunks in any way desired?
Isn't that exactly what Partition Magic & Qparted are supposed to do?

I must be missing something? There are programs that can almost defeat the worlds best chess players, but there isn't software to move blocks of data on a hard disk?

Am I dreaming this?????

---

### Post by eyemeansit on 2007-04-06
Yesterday I downloaded GParted Live CD (gparted version .3.4-5) from [this]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") link. It comes as an ISO file, which I then burned to a CD using K3b, (which automatically knew what to do with an ISO file). This created a boot-disk which runs a stripped down Gentoo Linux with GParted as nearly the only app available, and automatically opened on the desktop.

Anyway, with this GParted Live CD I was able to shrink my Windows Partition (hda1) from 19.7 GB to 12 something, creating unallocated space between it and my Ubuntu partition (hda2). Then I was able to grow the Ubuntu partition LEFT to make use of the unallocated space (a rather time consuming process, I should warn you.) Everything went off without a hitch.

While this is a bit different than the situation you described, it shows that it is possible to "grow left" with GParted. I hope this will help you!

---

### Post by mdurham on 2007-04-06
Just a suggestion.
cp -ax everything from hda2 to a directory on another partition. Remove the hda2 partition. Resize hda1 (Windows) partition. Create a new hda2 partition and cp-ax everything back to hda2.

---

### Post by Tufty on 2007-04-11
Hi...
I sorted this one by doing the following:

1) copied all my user data from /home partition onto the main Ubuntu partition.
2) deleted my /home partition.
3) extended the Ubuntu partition (TO THE RIGHT) to encompass ALL the spare space.
4) booted in wondows & used the partition magic wizard to extend the windows partition. What that did was offer me the available free space, but ask me where I wanted to steal it from, allowing me to take it from my Ubuntu partition. Partition magic then generated a few partitioning commands to move the Ubuntu data to the right, resize the Ubuntu Partition and then extend the windows partition into the created space.
5) re-created my /home partition.
6) copied user data back into /home.

Phew...
This worked perfectly! 
The reason I had to remove the /home partition was it was in the way & partition magic would only allow me to use space from the partition immediately to it's right - the Ubuntu partition.

Thanks for all your thoughts & ideas people.

Dave.

---

