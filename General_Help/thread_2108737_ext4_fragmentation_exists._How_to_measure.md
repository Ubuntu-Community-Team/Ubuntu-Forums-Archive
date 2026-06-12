---
title: "ext4 fragmentation exists. How to measure"
date: 2013-01-25
forum: General Help
---

### Post by esbrinartot on 2013-01-25
Hi. I just want to find out how important is the fragmentation with ext4.

1st time that I used linux I thought that fragmentation didn't exist.

Then I discovered that yes and you can extract the value with next command:

sudo fsck.ext4 -vpf /dev/sda2

292258 inodes used (15.75%)
271 non-contiguous files (0.1%)
517 non-contiguous directories (0.2%)
# de nodos-i con bloques ind/dind/tind: 0/0/0
Extent depth histogram: 245522/114
4768499 blocks used (64.33%)
0 bad blocks
2 large files

203517 regular files
29254 directories
59 character device files
26 block device files
2 fifos
948 links
59355 symbolic links (46489 fast symbolic links)
36 sockets
--------
293197 files


And now I've read that this command is doesn't give you the real value of fragmentation as windows do.

I think this command only gives you the % of non.contiguous files. And it's because we can have milions of small files without fragmentation an a thousand of big archives with a lot of fragmentation.

The article also says that windows gives you the real value of fragmentation.

**So how could i get a value in linux that I could compare to windows?**

When you assign the blocks in a hard disk... Which is the difference with NTFS and ext4? It think to avoid fragmentation the algorithm that assign the information to the blocks is what cause the fragmentation. **So anyone know the difference of the algorithm used by ntfs and ext4?**

I beginning to believe that the fragmentation in linux is the same as in Windows.

---

### Post by tgalati4 on 2013-01-25
In Windows you worried about it because it would cause your system to run very slowly.  When you went through a defragmentation and optimization, then Windows ran faster.

I have not noticed the same performance degradation in linux.  And I have had desktops running continuously for the past 6 years.  It would be interesting to run fragmentation statistics on those drives to see how bad they are.

You would probably get a performance boost by upgrading to a newer distro with better tuned ext parameters than worry about fragmentation.

---

### Post by Slim Odds on 2013-01-25
Block devices, like hard drives, will always store files in blocks (i.e., pieces). Therefore, over time, there will always be some sort of fragmentation. Every file system has this issue.

It just depends on the techniques used by the file system as to how much this affects performance.

---

### Post by esbrinartot on 2013-01-25
I agree with your opinions. But I would like to know to measure the real fragmentaation in Linux. According to some opinion the fragmentation obtained with the first method is no real. Low % doesn't mean that your system has no fragmentation because you have a huge archive that cause a lot of fragmentation.

I also would like to know the reason why ext4 is more efficient than ntfs.

For example I've read that most of the archives in the Linux system needs super user privileges to move them. So this is guess that this is good in order to avoid the fragmentation. 

Also would like to know why ext4 is more efficient than ntfs. Is the algorithm to assign blocks more efficient? Which are roughly the difference between both algorithms?

---

### Post by esbrinartot on 2013-01-27
Due to I was so interested in the fragmentation and I didn't obtain any answer I look up information and wrote a very good post. Although is in Spanish I let you the link. Maybe you can use google translator to understand the text.

[http://geekland.hol.es/la-fragmentacion-en-linux-existe/]("http://geekland.hol.es/la-fragmentacion-en-linux-existe/")

---

