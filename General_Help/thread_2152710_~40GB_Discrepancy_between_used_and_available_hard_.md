---
title: "~40GB Discrepancy between used and available hard drive space"
date: 2013-06-08
forum: General Help
---

### Post by jjjjeremy on 2013-06-08
Yes, I ran searches. Didn't find anything.

I have a ~200GB partition on my laptop that I share between Windows 7 and Ubuntu 12.04. In order to make space to back up files from another computer I deleted at least 10G of unused movies, files, etc, and that deleted space is not showing up. If I "select all" in the root folder for that partition I get 138.4 GB used of 202, but if I right click on that partition, and go to properties, it shows 175.2 used. The attached photo show the discrepancy between the space listed in "Contents" and the yellow "Used" space. I've emptied the Trash on Ubuntu and Windows multiple times, looked for hidden files, rebooted a few times too.

Any help?

Funnily, Windows shows it as a 188GB partition, and Ubuntu shows it as 202. 

[IMG]https://dl.dropboxusercontent.com/u/11622957/Screenshot%20from%202013-06-08%2013%3A12%3A22.png[/IMG]

---

### Post by deadflowr on 2013-06-08
Feels like the usual gibibyte versus gigabyte thing.
One lists kilobytes as 1000 and the other 1024, I think.
Something like that.

Also possible contents froze.

---

### Post by bluenova on 2013-06-08
138.4 GB is the total size of the files in the directory or in this case the partition as it's a mounted partition.

175.2 GB is the total amount of space used on the partition.

What type of partition is it? I suspect the discrepancy is due to reserved blocks or file allocation table depending on the partition type.

> **deadflowr said:**
> Feels like the usual gibibyte versus gigabyte thing.
One lists kilobytes as 1000 and the other 1024, I think.
Something like that.

This is all Megabytes as depicted by MB. Megabits are expressed as Mb.

---

### Post by jjjjeremy on 2013-06-08
It's an NTFS partition. 1000 vs 1024 isn't going to cause a 40 gig difference on a 200 gig partition, right?

---

### Post by Impavidus on 2013-06-09
> **jjjjeremy said:**
> It's an NTFS partition. 1000 vs 1024 isn't going to cause a 40 gig difference on a 200 gig partition, right?
1.024^3, because we are talking about gigabytes or gibibytes, wich is 1000^3 or 1024^3 bytes. 188*1.024^3=202, so it matches exactly.

Edit: This explains the size difference as reported by Ubuntu or Windows.

---

### Post by localhost8080 on 2013-06-09
I think what the OP is meaning is that he has 40 GB of unaccounted space.

the screenshot shows 138.4 GB of space being used at the top, and in the chart it shows 175.2GB

is this a network drive, or is it a mounted partition?

---

### Post by The Cog on 2013-06-09
The 1024 vs 1000 thing explains the difference between the windows and linux reports of the partition size (188 vs 202). Windows can't count, and thinks a billion is 1073741824. I wonder if MS's accountants use that when they report how many billions profit they made to the tax authorities.

It does not explain the discrepancy between Contents:138GB and Used:175GB. Both reported in the same tool. The figures are derived in different ways. The Used figure is taken from the filesystem itself. The Contents figure is found by summing the sizes of all the files the tool can find. 

One possible cause of the difference might be that there are many small files, where the actual file content is very small but the file has still been allocated a full block or cluster of blocks. In this case, even a 1-byte file makes one or more disk blocks no longer free to be used for storing other files. 

Another possibility is that there are files that the contents scanner was unable to access for some reason. Maybe a corrupt directory entry. Maybe hidden files (I don't know if ntfs can do that). Maybe hidden data in files - I have heard that ntfs can store "alternate" contents for files, and I'm not sure that is handled by linux which doesn't seem to have such a concept. Using windows chkdsk might clean it up a bit.

Either way, I expect that you will not be able to use more than the 27G the filestsyem says is free.

P.S.
As an afterthought, I might be tempted to copy everything off the drive, reformat and copy it back on again, and see what difference that makes.

---

### Post by jjjjeremy on 2013-06-11
I thought of doing the copy thing. Right now I'm also having other issues related to file transfers, so that's a bit iffy for now. My USB transfers consistently slow down from about 25MB/s to ~7-8MB/s over the life of the transfer, regardless of the size of the transfer as long as the transfer is large enough to trigger the transfer status window. Transferring 200GB the other day took about 6 hours even though the initial 25MB estimate said about an hour.

---

### Post by jjjjeremy on 2013-06-11
> **localhost8080 said:**
> I think what the OP is meaning is that he has 40 GB of unaccounted space.

the screenshot shows 138.4 GB of space being used at the top, and in the chart it shows 175.2GB

is this a network drive, or is it a mounted partition?

This is a mounted partition, shared between Windows and Ubuntu. If it helps, I think the drive was at about 175GB, then I deleted a bunch of stuff (maybe 20-30 gigs, which is when I noticed the usage discrepancy. I was trying to make a copy of some of my girlfriend's stuff, didn't have enough space, deleted unnecessary media files, no space, or very little space recovered.

Deleted/unmounted/turned off/reboot in different OS/emptied trash in both OSs over and over again with no avail, in different combinations.

---

### Post by localhost8080 on 2013-06-11
> **jjjjeremy said:**
> Deleted/unmounted/turned off/reboot in different OS/emptied trash in both OSs over and over again with no avail, in different combinations.

damn. there go all my suggestions :|

---

