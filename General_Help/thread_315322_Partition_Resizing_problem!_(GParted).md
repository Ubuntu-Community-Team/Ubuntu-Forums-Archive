---
title: "Partition Resizing problem! (GParted)"
date: 2006-12-09
forum: General Help
---

### Post by raveneffct on 2006-12-09
Ok! I have a problem, I was suggested to use GParted for resizing my partitions (Makings windows smaller and Linux bigger)...well. I made windows smaller first...the free space I created then became unallocated space...but now it wont let me add that to the linux partition! Please help, thanks. All I can do with the unallocated space is make a new partition with it, but I don't want to do that..nor can I do that because I already have 4 partitions.

---

### Post by taurus on 2006-12-09
You need to do that from the LiveCD since you can't resize or change partition size for Ubuntu while you are using it!!!

---

### Post by raveneffct on 2006-12-09
> **taurus said:**
> You need to do that from the LiveCD since you can't resize or change partition size for Ubuntu while you are using it!!!

Thats what I did in the first place...I did all this from the LiveCD.

---

### Post by taurus on 2006-12-09
Is the unallocated space right before the Linux partition that you want to add to?

---

### Post by raveneffct on 2006-12-09
> **taurus said:**
> Is the unallocated space right before the Linux partition that you want to add to?

Yes. :(

---

### Post by raveneffct on 2006-12-09
Is that bad?

Can someone help, I would reaaally appreciate it, thanks!

---

### Post by raveneffct on 2006-12-09
Sorry for posting so much, but I really want to fix this problem. If you have any idea how I should go about doing this, please let me know. Thanks in advance.

---

### Post by SmiLey497 on 2006-12-09
free bump for answer

---

### Post by drphilngood on 2006-12-09
Exactly which ¨LiveCD¨ are you using?

---

### Post by raveneffct on 2006-12-09
> **drphilngood said:**
> Exactly which ¨LiveCD¨ are you using?

GParted Live Cd.

---

### Post by raveneffct on 2006-12-09
Someone ... anyone?:(  I really need help with this.

---

### Post by Fittersman on 2006-12-09
gparted never worked for me and never will probably, check out my specs if they match yours or if you want to try something else use the hoary install cd to change partition size.

gparted always just breaks my partitions (makes them unknown or something) so when i need to change their size i have to use the hoary one.

bad thing is that im not sure if you can do that without completely reinstalling... 

food for thought :D

---

### Post by raveneffct on 2006-12-09
> **Fittersman said:**
> gparted never worked for me and never will probably, check out my specs if they match yours or if you want to try something else use the hoary install cd to change partition size.

gparted always just breaks my partitions (makes them unknown or something) so when i need to change their size i have to use the hoary one.

bad thing is that im not sure if you can do that without completely reinstalling... 

food for thought :D

I don't see why making a partition bigger should be a big deal, it should be just as easy as making a partition smaller! argh..

And my system is very close to yours. And there is no possible way that I am going to reinstall Ubuntu..it took me nearly 8 hours to get working in the first place.

---

### Post by Fittersman on 2006-12-09
yeah its a big pain in the a** for me and maybe for you too (haha) if you have got a few hours give it a shot :D

---

### Post by louieb on 2006-12-09
You may be out of luck. I've killed windows with GParted too.
To use space on a hard drive it must be in a partition, unallocated space is just that. If its not in a partition the space cannot be used.
Another limit is that the space allocated to any partition including an extended partition must be contiguous.  
If I understand right you want to reduce the XP partition  and add that space to your Linux partition. 
A  safer route is to use something like Norton ghost or PartImage and copy your existing partitions somewhere. Repartition the drive and copy the image back. But thats is kind of a pain too.
Thinking about it, a second hard drive may be your best answer. Its certainly the safest. 
The truth is reallocating hard drive space is not that hard but there sure are a lot of things that can go wrong. Yours is one case where if you can't back it up there is a good chance you can kiss it goodbye. 

Some other stuff about partitions.[LIST]
[*]There is a limit of  4 primary partitions.
[*] If you need more that 4 partitions only 1,2,or 3 of them can be primary and one must be an extended partition (you can have only one extended partition).
[*] Once you create an extended partition it can be subdivided into as many logical partitions as needed. There is a limit it think 14 or so for sata drives and 50 or so for ide drives.[/LIST]To give us a better picture of what you a working with please in Linux open a terminal window and post the output of ```
sudo fdisk -l
```

---

### Post by raveneffct on 2006-12-09
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        4799    38491740    7  HPFS/NTFS
/dev/sda3            9057        9725     5373742+  db  CP/M / CTOS / ...
/dev/sda4            7838        9056     9791617+   5  Extended
/dev/sda5   *        7838        9002     9357831   83  Linux
/dev/sda6            9003        9056      433723+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Linux needed to go in an extended partition because for some reason Windows takes up 3.

---

### Post by taurus on 2006-12-09
Okay, that could be your problem here.  You maked your NTFS smaller which is a primary partition and you want to give that space to your Linux which is in logical partition!!!

---

### Post by raveneffct on 2006-12-09
> **taurus said:**
> Okay, that could be your problem here.  You maked your NTFS smaller which is a primary partition and you want to give that space to your Linux which is in logical partition!!!

So how do I fix it?

---

### Post by bulldog on 2006-12-09
Well that's a nice thing for you to puzzle out this evening.

Some other ideas to read for you :D 

[http://ubuntuforums.org/showthread.php?t=315403](http://ubuntuforums.org/showthread.php?t=315403)

---

### Post by raveneffct on 2006-12-09
> **bulldog said:**
> Well that's a nice thing for you to puzzle out this evening.

Some other ideas to read for you :D 

[http://ubuntuforums.org/showthread.php?t=315403](http://ubuntuforums.org/showthread.php?t=315403)


"IF the free space in front of the Ubuntu install is large enough to hold the Ubuntu install. Why not create a partition out of it and use PartImage to copy your Ubuntu install to it. if that works then it just a matter of changing menu.lst to reflect the change in partition location. After that is done then maybe GParted can resize the new partition."

Ok, if I do that..wont the original Linux partition leave unallocated space as well once its deleted?

Actually don't even think I can make that unallocated space a partition cause I already have 4. Perhaps I can copy the linux partition, delete it..then make the unallocated space the partition and then put the copy of linux there?

And if you can't think of a way to solve this why leaving both Linux and Windows intact, would there be a way to solve it if I completely remove either windows or linux?

---

### Post by louieb on 2006-12-09
```

/dev/sda1             0001        0007    00056196   de  Dell Utility
/dev/sda2   *        0008        4799    38491740    7  HPFS/NTFS
 ---------- free space -----------------    
/dev/sda4             7838        9056    09791617+   5  Extended
/dev/sda5   *        7838        9002    09357831   83  Linux
/dev/sda6            9003        9056    00433723+  82  Linux swap / Solaris
/dev/sda3            9057        9725    05373742+  db  CP/M / CTOS / ...

```I just rearranged the fdisk output in the order they are on disk. It looks like you have about 24 gig of unallocated space between sda2 and sda4. The problem is the location of the free space. The only partition I know you can add it to is sda2. And you need it added to sda4.
BTW what is sda3(5 gig)  CP/M is the name of an operating system that predates DOS. 

Why don't you see if GParted or something can move sda4 and see if it also moves the logical partitions it holds(sda5&6). IF so then you got it made. 
You delete sda6 resize sda5 then add sda6 back.

If if you can't move the staring point of the partitions then you are going to have to delete sda4,5,6. Then add them back. sda4 extended 5&6 logical.
But at least it shouldn't kill windows. I say shouldn't but I killed windows doing something similar before.
Do you feel LUCKY!

---

### Post by bulldog on 2006-12-09
You need to get the free space **behind** the partition you want to enlarge.
Than you can add it to the partition before it.

Some things to consider when you're partitioning.
first primary  windows
second primary windows data
extended partition
first logical /  [root]
second logical /home
third logical swap

This way you can resize your windows from the data partition and your / from your /home.

---

### Post by raveneffct on 2006-12-09
> **louieb said:**
> ```

/dev/sda1            0001        0007    00056196   de  Dell Utility
/dev/sda2   *        0008        4799    38491740    7  HPFS/NTFS
 ---------- free space -----------------    
/dev/sda4            7838        9056    09791617+   5  Extended
/dev/sda5   *        7838        9002    09357831   83  Linux
/dev/sda6            9003        9056    00433723+  82  Linux swap / Solaris
/dev/sda3            9057        9725    05373742+  db  CP/M / CTOS / ...

```
I just rearranged the fdisk output in the order they are on disk. It looks like you have about 24 gig of unallocated space between sda2 and sda4. The problem is the location of the free space. The only partition I know you can add it two is sda2. And you need it added to sda4.
BTW what is sda3 CP/M is the name of an operating system that predates DOS. 

Why don't you see if GParted or something can move sda4 and see if it also moves the logical partitions it holds(sda5&6). IF so then you got it made. 
You delete sda6 resize sda5 then add sda6 back.

If if you can't move the staring point of the partitions then you are going to have to delete sda4,5,6. Then add them back. sda4 extended 5&6 logical.
But at least it shouldn't kill windows. I say shouldn't but I killed windows doing something similar before.
Do you feel LUCKY!

How do I add sd6 back after I delete it, do I have to copy it first?

I hope this works..

Also...can I delete sda3?

---

### Post by bulldog on 2006-12-09
You can delete all the partitions,but the names sda1,sda2 and so on is something that gparted will set.

---

### Post by raveneffct on 2006-12-09
No I mean deleting sd3 but still keeping windows in tact.

---

### Post by bulldog on 2006-12-09
No problem I think,your windows is on sda2 as long as you don't touch this one and the partition before it no harm done.

---

### Post by hsalgado on 2007-01-26
Have you changed the partition type from NTFS of windows to ext3 of Linux?????:confused:

---

### Post by tvor on 2007-04-07
Have similar problem. Need to add the unallocated space to /hda6 as in pics bellow. What is the easiest option to do that (or  perhaps to move the unallocated space under /hda6 ?

Also can I safely steel more space from Window partitions (NTFS) and/or do I have to de-fragment ?)
(running GParted live CD 0.3.4.5)

[IMG]http://tvor.bloguje.cz//img/mmm.png[/IMG]

---

### Post by laidback on 2007-04-07
Try deleting the to-be-reused area first, then select it, reformat etc.

---

