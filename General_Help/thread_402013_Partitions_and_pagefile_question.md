---
title: "Partitions and pagefile question"
date: 2007-04-05
forum: General Help
---

### Post by gummo on 2007-04-05
Hello,

first off, this question is a question about windows, not Ubuntu really, this is the only forum i frequent that has alot of techy people who know a bit about computers, so i figured i'de just ask here.

I currently have the following drives setup:

80G 7200RPM 8MB cache (MASTER)

1st partition: 10G Windows XP PRO SP2
2nd partition: 24G Ubuntu Edgy Eft 6.10
3th partition: 1G Swap
4th partition: 44G Storage (ntfs)

120G 7200RPM 2MB cache (SLAVE)

1st partition: 40G Games (ntfs)
2nd partition: 40G Storage (ntfs)
3th partition: 40G Storage (ext3)

Now, my question is concerning the first partitions on each drive. I currently only use windows for gaming and ubuntu for everything else. Ubuntu is running just fine on my machine but games are starting to become a bit heavy. I decided to start tweaking my windows a bit and came to the following problem:

Several tweakguides advice to (if u have 2 equally fast drives) place the pagefile on the first partition of ur non-windows drive. The thought behind this being that, that way 2 drives are reading/writing instead of 1 drive doing all the work. Seems logical enough.

What i was wondering: wich actually uses the pagefile most during gaming? Are it the game files that are being written to the pagefile? (hence making it better to leave the pagefile on the windows partition?) Ive looked on quite some forums but nothing really clarified it :(

**So, in short: for gaming purposes, where should i place the pagefile for best performance with my current drive setup? (see couple lines up).**

---

### Post by dannyboy79 on 2007-04-05
it has nothing to do with games versus word processing. it is plainly better to have the paging file on a seperate partition at a minimum (better for different hard drive all together) because this way when ANY program is taking all the ram, then the paging file is used (hard drive space is used as ram) and if this is on a seperate drive that isn't being accessed by anything else than obviously it would perform better since that's the only thing that making that drive spin. here is a microsoft article: 
[http://support.microsoft.com/kb/314482/](http://support.microsoft.com/kb/314482/)
and also here:
[http://support.microsoft.com/kb/555223](http://support.microsoft.com/kb/555223)

I have a machine with 2gb of ram. I made the size on "C" between 126-252 MB, and something like 3072 MB to 6000-MB on "E." Not only do I now have some breathing room on "C," but it seems to me that Photoshop and various operations (like database compression) are now perceptibly faster.

---

### Post by gummo on 2007-04-05
Thanx dannyboy79

I think ill just reformat my first partition on my slave into 2 4g and 36g partitions, using the 4g as pagefile and the remaining 36G for games. I dont really care too much about the dumprep thing so ill just stick to the 1 pagefile. Guess that should be pretty much optimal then, windows at the start of 1 drive and the pagefile at the start of the other, both in their own partitions.

Off to format :P

---

### Post by dannyboy79 on 2007-04-05
no, you don't need to recreate an entire partition just for the pagefile.sys, all you have to do is move the file to your second hard drive's first partition and that's all. at least that's what I gathered from that. also, i would take microsofts help to heart, if they say that something bad could happen by not having a paging file along with windows than I would make a paging file on the same drive as windows. it's your system obviously so you do what you want.

---

