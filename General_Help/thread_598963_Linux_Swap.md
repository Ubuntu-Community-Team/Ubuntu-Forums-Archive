---
title: "Linux Swap?"
date: 2007-10-31
forum: General Help
---

### Post by jolt459 on 2007-10-31
Hi,

I would like to create another Partition for my Music, Pictures and Videos that can be accesible from both my Linux partition and my Windows partition. There is one problem though, apparently GParted won't allow more than five partitions. And I have five.

Two of them I have no idea what they are. They are the "Linux Swap" and the "extended" and they are both locked, I can't edit them. I'm just wondering a way to get around this so I can create another partition, if anybody could help me, that would be wonderful :)

And another question I have, what Hard drive format works for both Linux and Windows. What I mean by this is which one can be accessed from both my Windows Partition and my Linux Partition? (Like FAT32, NTFS, etc)

Thanks a bunch, and btw I really like you're quick responses and helpful community!

---

### Post by louieb on 2007-10-31
With seeing your partition table can't give specifies. But swap is similar to a virtual memory file in windows. Partition layout has rules. Here a simple explanation of partition types and links to other information.  [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")
As for a shared data partition format it with a file system native to the operating system you use the most. ntfs or ext3. There are programs you can install in the other to allow it to read and write to the data partion too.

---

### Post by ofb on 2007-10-31
Can't touch extended and swap. Think of the extended as a partition that contains other partition that you use - it's not taking up space of it's own. Swap is used by your system for memory intensive processes - when there's too much to 'think' about for the available RAM, things get set down momentarily on the harddrive in Swap.
[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

---

### Post by ofb on 2007-10-31
Incidentally, while old FAT32 is a popular format for partitions that either OS can use, keep in mind that it cannot handle as many characters in file names as ext3.

So sometime you may get 'permission denied' errors when you try to copy over files with names that include characters like '>' and ':'.

---

