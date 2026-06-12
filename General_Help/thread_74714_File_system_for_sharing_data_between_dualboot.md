---
title: "File system for sharing data between dualboot"
date: 2005-10-12
forum: General Help
---

### Post by mariux on 2005-10-12
Hi, i have a laptop for schoolwork and i have installed both (k)ubuntu and windows xp on it. The thing is that i need to run windows from time to time and since i need to have all my precious hd-space available all the time, having the partition formated to ntfs causes me to "not be able to use ubuntu as much" since i need to have write access to all my hdspace.

So the question is, is there a fs i can use that is:
* Writable from both ubuntu and windows (at atleast 5mB/s (tried that wine ntfs writer about a year ago and it did only 400kB/s))
* Supports files larger than 4gb (dvdimages) (this one rules out fat32 as it doesnt support files larger than 4gb ?!?)

Well, thats about it :) Anyone?

---

### Post by matthew on 2005-10-12
I was going to recommend fat32 until I saw the filesize requirement...off the top of my head I really don't know of one, but you might be able to use this wiki page to help you in your searching. Good luck!!

[http://en.wikipedia.org/wiki/List_of_file_systems](http://en.wikipedia.org/wiki/List_of_file_systems)

---

### Post by Pettman on 2005-10-12
There is ext2/ext3 read write support for windows. I have got i working, but I do hardly use is since I only got 2 small ext3 partitions for Linux. [Here]("http://sourceforge.net/projects/ext2fsd") is the project info page on sourceforge.net and [here]("http://ext2fsd.sourceforge.net/") is the projekts homepage.

EDTI: Have no idea about how fast/slow read/write is, but ext2 and ext3 can handle large files.

---

### Post by mariux on 2005-10-13
I think i will just make it a fat32 and have another small ntfs partition for those large files. Thanks for the help anyways :)

---

