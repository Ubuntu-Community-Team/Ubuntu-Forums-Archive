---
title: "Copying a Hard Disk to another Hard Disk"
date: 2006-11-21
forum: General Help
---

### Post by Joshua on 2006-11-21
Can anyone tell me if there is a good way to copy exactly all the data from an old hard disk (windows) to a new hard disk using the Ubuntu Live CD?  Similar to using Ghost?

---

### Post by mbeierl on 2006-11-21
Define exactly, please?  If the disks are exactly the same size, you can use the "dd" command from the terminal to create an exact copy of each and every block of data.

I'm just not sure that is what you mean by exact...

---

### Post by mcduck on 2006-11-21
check out the 'dd' command.. It does raw copying from disk/partition to other. 'man dd' should tell you more, so it no matter what the file system is.

---

### Post by Ramses de Norre on 2006-11-21
Or partimage, if you like a GUI.

---

### Post by Joshua on 2006-11-21
The disks are not the same size.  Sorry for the confusion.  I meant that I want to be able to make the new disk look pretty much the same (just with extra space) so that, when I make the new disk the "master" and take the old one out, it will boot and look just like my old computer (just with extra space).

---

### Post by Ramses de Norre on 2006-11-21
Partimage will do that too, I think. It's in the repo's.

---

### Post by aysiu on 2006-11-21
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) explains the process with screenshots.

---

### Post by Joshua on 2006-11-21
Thanks, that looks perfect.

---

### Post by artinla on 2006-11-28
Hey Joshua,

I like ddrescue.  It is pretty quick, and can do multiple partitions in the same process. 

I/E:  sudo ddrescue /dev/hda /dev/hdb 

would copy the entire contents including the MBR over to hdb from hda.  It also works on SCSI or SATA drives.

It is better than dd because it reports progress and error counts as it goes.

Install it with "sudo apt-get install ddrescue"

Hope it helps.

Art

---

