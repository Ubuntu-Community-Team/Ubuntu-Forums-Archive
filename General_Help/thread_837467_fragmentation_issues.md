---
title: "fragmentation issues"
date: 2008-06-22
forum: General Help
---

### Post by dexter.deepak on 2008-06-22
i needed to know the mechanism by which linux avoids fragmentation...
i couldnt find a proper reason, but stumbled across this page :
 
[http://aplawrence.com/Bofcusm/834.html](http://aplawrence.com/Bofcusm/834.html)

and this was a shocking discovery for me.
please have a look at it and give some comments....and yes, if possible please link me to a page which gives the solution to my original problem.
thank you.

---

### Post by windoze87 on 2008-06-22
I believe that Linux file systems (ext2, ext3) have little fragmentation issues , seeing as they are grouped into blocks of data, which are in turn inside a superblock... the difference between ext file systems and Windows file systems (fat32, ntfs) is that where ext writes to a block, ntfs file systems write themselves to the first available empty space, whether it's in the first, middle, or the last sector of a disk, or anywhere in between. Also, when you delete something while using ntfs, it's not really "deleted" per se, it's just made available to the first bit of data that is told to write there. 

So to make this easier to understand, you have a free space on your NTFS hard drive that's X bytes long in sector J, and you have more free space that's Y bytes long in sector O, but there is data that's already been written to in sectors K,L,M,and N. So because of the way that NTFS was made, a program you might install will write itself to the first available space (which in our example is in sector J) and then will go on from there (to sector O), thus causing fragmentation.

Ext file systems make an attempt to reduce fragmentation greatly by preallocation... what that means is when you format a hard drive using an ext file system, it writes in superblocks, which are in turn composed of blocks. These blocks are written so that when a file is written within the block, the preallocation that your ext format performed caused more free space to be left within that block, so while you have a program that's C bytes long, there's still D bytes left within that block. When something is erased out of an ext block, there is more free space available there than if you had used ntfs. Fragmentation isn't eliminated, just reduced greatly. I've used Linux for about a year now and installed/uninstalled programs religiously, and never really seen a performance issue, so as long as you're using ext, you shouldn't have a problem. I think the tool fsck takes care of fragmentation problems among checking other things having to do with your filesystem, it runs itself every 20 boots or so unless you do it yourself.

My bad, fsck just checks the integrity of the filesystem (it looks for bad sectors), it doesn't actually defragment. I think defragfs is what you're looking for, but you can only use it through the command line, i don't think there's any GUI defrag tool for Linux yet. Hope this helps

---

### Post by cariboo on 2008-06-22
Here is a link to the ext3 file system, it also explains about defragmentation. 

[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

MS has been trying to design a file system that doesn't fragment for years, but WinFS has never made it  in to any of their OS's. Now that Hans Reiser is in jail, we might suggest to any of the microsofties that lurk here, RieserFS might be up for sale.:)

Jim

---

