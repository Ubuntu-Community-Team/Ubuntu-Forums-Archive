---
title: "NTFS, FAT32 partition questions"
date: 2005-07-30
forum: General Help
---

### Post by Zotova on 2005-07-30
My apologizes if this is in the wrong section or if the question has been asked too many times before.

On my laptop I currently have Windows XP and ubuntu, the laptop came with one hard drive but was split into two ntfs partitions (both around 18 gb each).

When I first wanted to test Linux a couple of months back I created a 3 gb partition as I presumed I would play with Linux, get bored and then delete it. However after trying out suse and mandriva and not being impressed I came to ubuntu, which I have decided to keep.

On further exploration I managed to mount both ntfs partitions in ubuntu, but unfortunately there is no way to write to these partitions outside of xp.

So my question is, if I were to create (or convert one of the ntfs partitions) a fat32 partition would it be possible that both xp and ubuntu could read and write to this partition? For example allowing previous xp pictures, word documents etc not only to be read in ubuntu but also edited and saved. Then when I boot into xp would it be possible for this fat32 partition to be read and written too by xp? If you like a partition which could sit between the two operating systems.

Also, currently my D:/ in xp has a few windows programs on it (mainly games) and the rest of the drive contents is mainly pictures and the odd document. Would it be possible to convert that partition to fat32 without loosing the data? I have installed Gparted in ubuntu but when I went to convert the ntfs partition to fat32 it warned me that all data would be lost within this partition. Would there be a relatively safe way around this using another partition manager? (Preferably free and preferably in ubuntu).

Would I also be correct in thinking, if there is a way to convert the ntfs drive to fat32 without loosing the data the games currently on that partition would still be playable? As the windows registry would still be saved on the C:/ partition? (Which is where all the windows directories are stored.) .

Thanks for any replies.  :)

---

### Post by super on 2005-07-30
i can only answer the first part of your question with certainty.

> if i were to create (or convert one of the ntfs partitions) a fat32 partition would it be possible that both xp and ubuntu could read and write to this partition? 
yes, if you convert one of the partitions into a fat32 filesystem, then both linux and windows will be able to read/write the drive.

as to the second question:
> Would it be possible to convert that partition to fat32 without loosing the data? 
i don't think it's possible, but i`m not 100% sure.

---

### Post by Zotova on 2005-07-30
Thanks for the reply.
 
So for example, if I converted the partition which is currently called D:/ in xp to fat32 would it automatically still show in xp? As my current linux partition does not seem to show under xp.

---

### Post by kosmic on 2005-07-30
1 - To show your windows partitions in linux you have to mount them first (FAT, NTFS)

2 - Yes if you convert one partition to FAT both linux and windows can write and read to them.

3 - There is a small program Called CAPTIVE (it uses windows drivers) to let linux write and read NTFS Partitions, you can try but be carefull with that because the program is still experimental.

---

