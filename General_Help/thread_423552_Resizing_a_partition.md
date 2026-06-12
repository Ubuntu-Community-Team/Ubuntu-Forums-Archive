---
title: "Resizing a partition?"
date: 2007-04-26
forum: General Help
---

### Post by Jroller90 on 2007-04-26
I was wondering if i could resize my Ubuntu partition without loosing any files, and how would I go about doing this?

---

### Post by jfinkels on 2007-04-26
> **Jroller90 said:**
> I was wondering if i could resize my Ubuntu partition without loosing any files, and how would I go about doing this?

Boot from the Ubuntu Live CD, and use GParted to resize your partition.

---

### Post by nemesisrobot on 2007-04-26
Use Gparted, couldn't be any easier.

---

### Post by Jroller90 on 2007-04-26
ok, thanks. I decided I'd ask before screwing up something :)

---

### Post by jfinkels on 2007-04-26
> **Jroller90 said:**
> ok, thanks. I decided I'd ask before screwing up something :)

Better this way than the alternative :)

---

### Post by lex on 2007-04-27
> **jfinkels said:**
> Boot from the Ubuntu Live CD, and use GParted to resize your partition.
 
I tring Kubuntu 7.04, I tried to use QTparted from my live cd,  but it wouldn't let me resize my partition. I could format and delete it but not resize it. Any other ideas.
thansk.

---

### Post by jfinkels on 2007-04-29
> **lex said:**
> I tring Kubuntu 7.04, I tried to use QTparted from my live cd,  but it wouldn't let me resize my partition. I could format and delete it but not resize it. Any other ideas.
thansk.

You can only resize partitions formatted with certain filesystems. For example, you may not be able to resize an NTFS filesystem, but you may be able to resize and EXT3 filesystem (which is the default for Ubuntu).

Another reason this might happen is if you have mounted the partition. If you can browse the files of the hard disk partition that you are trying to resize, you canNOT resize it! You must unmount the partition before you can resize it.

---

