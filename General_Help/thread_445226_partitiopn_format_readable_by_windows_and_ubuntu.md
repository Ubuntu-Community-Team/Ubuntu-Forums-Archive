---
title: "partitiopn format readable by windows and ubuntu"
date: 2007-05-15
forum: General Help
---

### Post by hessiess on 2007-05-15
hi

i use ubuntu manly at school but windows at home becose i cannot get the internet working in ubuntu. what partition format can i use to save all my stuff on so that it can be red in windows and ubuntu?

---

### Post by taurus on 2007-05-15
Fat32.  However, Windows can read ext3 with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by mikewhatever on 2007-05-15
Is fs-driver a better option then ntfs-3g?

---

### Post by merlinus on 2007-05-15
They both work well, but are for different operating systems.

ntfs-3g allow you to read NTFS-formatted drives from Linux.

fs-driver allows windows to read ext3-formatted drives.

-merlin

---

### Post by taurus on 2007-05-15
> **mikewhatever said:**
> Is fs-driver a better option then ntfs-3g?

Yes, it is.

---

### Post by merlinus on 2007-05-15
> **taurus said:**
> Yes, it is.

Why?  ntfs-3g actually works better, for me.

Thanks.

-merlin

---

### Post by taurus on 2007-05-15
> **merlinus said:**
> Why?  ntfs-3g actually works better, for me.

Thanks.

-merlin

If you think ntfs-3g works better go you, then go for it.  There's nothing wrong if you decide to use ntfs-3g.

---

### Post by hessiess on 2007-05-16
is it posable to make windows right to ext3 or ubuntu right to ntfs?  or should i just make a fat32 partition. are there any sise limits on fat32? it would need to be 20 to 30 gb

---

### Post by taurus on 2007-05-16
Fat32 cannot handle a file larger than 4GB.

---

### Post by hessiess on 2007-05-16
that should be fine, i never make anything that big

---

