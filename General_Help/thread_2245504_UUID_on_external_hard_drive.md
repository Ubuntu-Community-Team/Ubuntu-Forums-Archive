---
title: "UUID on external hard drive"
date: 2014-09-24
forum: General Help
---

### Post by ELMIT on 2014-09-24
I thought a UUID must be unique!

I bought two hard disks:

sudo blkid /dev/sdc1
/dev/sdc1: LABEL="Seagate Expansion Drive" UUID="4E30C12B30C11ABB" TYPE="ntfs" 

sudo blkid /dev/sdb1
/dev/sdb1: LABEL="Seagate Expansion Drive" UUID="4E30C12B30C11ABB" TYPE="ntfs" 

How can I change label and UUID ????

---

### Post by sudodus on 2014-09-24
Label is easy to change with gparted.

I would recommend a windows tool to change UUID, unless they are new, and you can reformat them. In that case reformatting with gparted should create a new UUID.

---

### Post by tgalati4 on 2014-09-24
I would purchase a lottery ticket.  Your luck may be changing!

> tgalati4@Mint14-Extensa ~ $ apropos label
dosfslabel (8)       - set or get MS-DOS filesystem label
e2label (8)          - Change the label on an ext2/ext3/ext4 filesystem
findfs (8)           - find a filesystem by label or UUID
ip-addrlabel (8)     - protocol address label management
mlabel (1)           - make an MSDOS volume label
**ntfslabel (8)        - display/change the label on an ntfs file system**
ppmlabel (1)         - add text to a portable pixmap
swaplabel (8)        - print or change the label or UUID of a swap area

If you are going to keep the drives as NTFS, then common UUID's is the least of your problems.

---

### Post by oldfred on 2014-09-24
If the drives were preformatted, the vendor is not formatting them, but cloning an image. That image then only has the one UUID. 
Every drive then has the same UUID.

---

