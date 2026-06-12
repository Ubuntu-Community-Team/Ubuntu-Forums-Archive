---
title: "Error 17 when I try to boot-up ubuntu"
date: 2007-09-15
forum: General Help
---

### Post by febqwerty on 2007-09-15
every time i try to boot-up my system i get this:
[http://s225.photobucket.com/albums/dd273/sinogap/?action=view&current=SNV32151.jpg](http://s225.photobucket.com/albums/dd273/sinogap/?action=view&current=SNV32151.jpg)
[http://s225.photobucket.com/albums/dd273/sinogap/?action=view&current=SNV32152.jpg](http://s225.photobucket.com/albums/dd273/sinogap/?action=view&current=SNV32152.jpg)

---

### Post by Sef on 2007-09-15
Error 17 is > 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

What is the partition formatted as (NTFS, ext 3, other)

---

### Post by febqwerty on 2007-09-15
Ntfs

---

### Post by Sef on 2007-09-15
> Ntfs

For GNU/Linux, you should go with ext3, the default format.   GNU/Linux can't be run on NTFS.

In other words, you need to reformat and reinstall.

---

### Post by febqwerty on 2007-09-15
> **Sef said:**
> For GNU/Linux, you should go with ext3, the default format.   GNU/Linux can't be run on NTFS.

In other words, you need to reformat and reinstall.


but it used to run on ntfs o well how do i reformat to ext3? and btw the error says file not found is there anything i can do without reformating?

---

### Post by Mahon on 2007-09-15
I have kind of the same problem on my laptop. I'm running XP and Ubuntu 7.04. The XP is running on ntfs, but the Ubuntu is running on swap/ext3 on a seperate disk. I can't run kernel 2.6.20-16-generic, 2.6.17-10-386 or 2.6.17-10-generic. I can run kernel 2.6.17-12-generic, but it takes a long time to boot. Sometimes it runs kernel 2.6.20-16-generic, and it boots a lot faster, but this only happens once in a while, when i let the boot screen time out. How can this be fixed?

---

### Post by febqwerty on 2007-09-16
> **febqwerty said:**
> but it used to run on ntfs o well how do i reformat to ext3? and btw the error says file not found is there anything i can do without reformating?

Can anyone please help me

---

### Post by Sef on 2007-09-16
> but it used to run on ntfs o well how do i reformat to ext3?

You would have to reinstall Ubuntu.   The default file system is ext3.

---

### Post by febqwerty on 2007-09-17
> **Sef said:**
> You would have to reinstall Ubuntu.   The default file system is ext3.
can you please tell me how i change to ext3?

---

