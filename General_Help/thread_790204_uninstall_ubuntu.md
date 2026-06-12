---
title: "uninstall ubuntu"
date: 2008-05-11
forum: General Help
---

### Post by spudratic on 2008-05-11
Is there a proper way to uninstall ubuntu.I would like to get my hard drive back to a pre  ubuntu state.Grub is the real question for me will it still be there after I delete hardy from the hard drive.

I'm looking for any info tips thanks.

---

### Post by wpshooter on 2008-05-11
Are you wanting to get EVERYTHING off of your computer hard drive or just Ubuntu ?

---

### Post by HunterThomson on 2008-05-11
So, you didn't install ubuntu from with in window$ right?
Yes when you installed Ubuntu grub did over write the MBR (Master Boot Record) for window$. There is a comand line augment you can make in win before you reformat the Ubuntu partitions back to NTFS that will fix it. If i remember correctly you need the win cd to do it. OR you can download the SuperGrub LiveCd and install it after you just expand the win NTFS partition to the whole drive in the partitioner on the ubuntu live cd effectively deleting Ubuntu. I am prity sure you can just set the super grub boot loader to just auto load win so you don't have to select it or it just defaults to do that anyway.

you have to use this if you don't have the Win CD
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by housam on 2008-05-11
You can simply reformat ubuntu partitions ( grub will be deleted )then fix the MBR using windows CD to get it working again.

---

### Post by spudratic on 2008-05-11
thanks people that answers my question.

---

