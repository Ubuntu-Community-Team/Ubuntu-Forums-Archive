---
title: "Defrag NTFS Partition"
date: 2007-04-11
forum: General Help
---

### Post by mand0 on 2007-04-11
Forum goers:

I've got two hard drives as of right now.  One, where Ubuntu is installed, is ext3 and the other, where I keep all my files, is NTFS.  I am aware that Linux is not as prone to defragmentation so I don't need to worry about that.  However, my NTFS hard drive will eventually need to be defragmented and I only have Ubuntu installed.  Is there a way to defrag a NTFS partition while in Ubuntu?

---

### Post by mand0 on 2007-04-12
This is the closest thing I've been able to find and it's still in development:

[http://wiki.linux-ntfs.org/doku.php?id=ntfsdefrag](http://wiki.linux-ntfs.org/doku.php?id=ntfsdefrag)

---

### Post by dfreer on 2007-04-12
[http://forum.ntfs-3g.org/viewtopic.php?t=468](http://forum.ntfs-3g.org/viewtopic.php?t=468)

Seems like it still needs to be defragged. You may be able to find a windows defragger that works with Wine, but I dunno if I would trust it with my important data. If you have another computer with windows, you may try mounting the NTFS partition through the network and see if windows or a defrag program can reach it.

Although this isn't a solution, you might want to consider converting the NTFS partition since you are running Ubuntu anyways. There's really no advantages to running NTFS in a pure linux enviroment.

EDIT: Seems I read the post wrong, sorry. AFAIK there isn't any NTFS defragging software for linux, and considering that NTFS3g just recently became *stable* (Feb. 21, 2007) I'm not that surprised. Still, consider switching ntfs with reiserfs/xfs/whichever linux filesystem you prefer.

---

### Post by mac.ryan on 2007-04-12
> **dfreer said:**
> []("http://forum.ntfs-3g.org/viewtopic.php?t=468")You may be able to find a windows defragger that works with Wine, but I dunno if I would trust it with my important data.

AFAIK, all the defraggers works with the windows APIs (due to the 'industrial secret' around NTFS), therefore I am not sure whether any of them would eventually work with wine...

Should you be wishing to run a defrag on your ntfs partition from windows, I would recommend [jkdefrag]("http://www.kessels.com/JkDefrag/").

---

