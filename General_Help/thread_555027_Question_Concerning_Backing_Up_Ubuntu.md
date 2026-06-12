---
title: "Question Concerning Backing Up Ubuntu"
date: 2007-09-19
forum: General Help
---

### Post by Earthwormzim on 2007-09-19
I've read several other posts about backing up Ubuntu...but, I still have a couple questions:

1)  I see that the two most common apps to choose from to do this are Partimage, and Mondo.  Which one is better (i.e., easier to use)?  According to this post, located
[here]("http://ubuntuforums.org/showpost.php?p=1482147&postcount=5"), apparently this guy reports that he had problems writing to a FAT32 partition with Partimage (plan on using a FAT32 backup disk, being that both Linux and Windows can read and write to them).  Does Mondo have this limitation?  

2) Would it be possible to skip using any programs and just copy all of my folders to a "backup folder" on my backup hdd, and when it comes time to restore them, just reinstall Ubuntu, and simply cut & paste all my old folders from my backup hdd over all of the folders in the new install?  According to another post on backing up Ubuntu...there is a detailed set of instructions on how to do something that sounds very similar using the command prompt ([link]("http://ubuntuforums.org/showthread.php?t=35087")).  But, in this example, he is not actually installing Linux first...instead, from the looks of things, it appears that he is describing how to do this from a live CD, without installing Linux at all (hence the end part about having to install Grub...and I'd like to avoid having to do this...which is why I'm enquiring about doing it in this fashion, being that the install process would include setting up Grub automatically, so I would have to do it myself). 

Would this work?

---

### Post by por100pre1 on 2007-09-19
I just backup my home folder with Grsync to a external hard disk; no weird file types, no compression. To restore the files it's just to drag and drop 'em. After the first backup you can just set it to replace newly changed/accesed files for quick backups. Hope this helps. :)

---

### Post by Earthwormzim on 2007-09-19
But, then the restore wouldn't include programs, would it?  

Edit:  BTW, I just tried Grsync.  Holy crap, this program is awesome!  I have a fairly large mp3 collection, of which I keep two copies (one copy on one hdd, and the other copy on the other hdd)...and for the longest time, whenever I made changes to one, I had to go through the tedious process of making the exact same changes to the other.  Do you know how long I've been looking for a free program on Windows that does this automatically?  And Grsync does exactly this!  AMAZING!!!  +1 for Linux!

---

