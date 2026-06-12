---
title: "Archive the / partition for backup, just one question"
date: 2008-01-02
forum: General Help
---

### Post by rootware on 2008-01-02
Greetings everyone and a Happy New Year!

Here's a thing I wanna do: 

I wanna backup the / partition. So I would like to archive the / partition into a file. 

The point is if I archive / , **it would archive the archive itself, so this process it would never end.** 

Here are my partitions:

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51200000    7  HPFS/NTFS
/dev/sda2            6376       19457   105081165   83  Linux

Is there a way to archive the / , **excluding** the file created?

---

### Post by ~LoKe on 2008-01-02
I don't think so...but I believe you could archive everything **except** the /home directory, and save the archive in the home directory.  That way it's not archiving the archive.  Then you could archive the /home directory separately.

---

### Post by p_quarles on 2008-01-02
I think you might have better luck using the partimage backup application -- available in the repositories.

---

### Post by jken146 on 2008-01-02
You could do this in Windows or from a Live CD.  Partimage is a better idea though.

---

### Post by rootware on 2008-01-02
So there's no way to tar with exclusion?

---

### Post by p_quarles on 2008-01-02
> **rootware said:**
> So there's no way to tar with exclusion?
Sure there is, and it's right there in the man page, along with the commands to preserve permissions and symlinks -- i.e., the stuff that will make the archive actually useful when you restore it. 

But, since you asked here, I'm guessing that you would find a utility (partimage) that was specifically designed for your purpose a bit more convenient. Give it a shot.

---

### Post by ~LoKe on 2008-01-02
> **p_quarles said:**
> Sure there is, and it's right there in the man page, along with the commands to preserve permissions and symlinks -- i.e., the stuff that will make the archive actually useful when you restore it. 

But, since you asked here, I'm guessing that you would find a utility (partimage) that was specifically designed for your purpose a bit more convenient. Give it a shot.

You beat me again.  But the good news is from every post you correct me with, I learn something new!

---

### Post by rootware on 2008-01-02
> **p_quarles said:**
> Sure there is, and it's right there in the man page, along with the commands to preserve permissions and symlinks -- i.e., the stuff that will make the archive actually useful when you restore it. 

But, since you asked here, I'm guessing that you would find a utility (partimage) that was specifically designed for your purpose a bit more convenient. Give it a shot.

OK, I've tried PartImage and I have to umount the / partition... guess I must do that with PartImage CD.

I have another question please: if I tar the / with exclusion, will that restore the mbr too?

---

### Post by p_quarles on 2008-01-02
> **rootware said:**
> I have another question please: if I tar the / with exclusion, will that restore the mbr too?
I don't believe so. I'm not that knowledgeable about low-level/hardware stuff like booting, but I believe the mbr is distinct from any filesystem on the hard disk. Tar or partimage will, however, keep your GRUB/LILO configuration files.

---

### Post by Casual Fan on 2008-01-02
[http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207)

---

