---
title: "How do i change the permissions of an entire drive??!!"
date: 2007-06-21
forum: General Help
---

### Post by Zavie A. on 2007-06-21
My current PC has two drives which until recently only used windows. I then installed Ubuntu onto my main C drive and it now won't allow me to change the properties, add or delete anything in my storage drive (drive D) As i do not have the permissions to do so. 

so...

**[COLOR="Red"]HOW DO I CHANGE THE PERMISSIONS OF MY STORAGE DRIVE?[/COLOR]**

p.s. Can i get the "for dummies" version? im only 15. lol

---

### Post by keiffee30 on 2007-06-21
Now this is a 1st for me, im answering a problem. 

I wouldn't like to tell you about the 1st problem incase i gave you the wrong way, but there are loads of books about Linux. 
The best place to start would  be PC World, they have got some books about linux that might just help you along. Also have a look at the webs too there you will find loads of information about linux. 

Hope this helps and good luck

---

### Post by NeoLithium on 2007-06-21
Well, is your storage drive still formatted with NTFS or FAT, or is it a Linux filesystem type?  As well, can you post the output of this command from terminal, and let us know which drive it is:  ```
cat /etc/fstab
```

---

### Post by Zavie A. on 2007-06-21
Deffinetly NTFS

---

### Post by NeoLithium on 2007-06-21
No problemo then. There's an easy walkthrough here that will take you step by step for NTFS read/write support :)

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Hope this helps :)

---

### Post by jfinkels on 2007-06-21
> **Zavie A. said:**
> Deffinetly NTFS

You need to install the NTFS-3G driver to enable read/write access to NTFS partitions from Ubuntu. See here for more info:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Zavie A. on 2007-06-21
ive got the volume mounted...but it still wont allow me to delete or add files to it...so im stuck again :( lol

---

### Post by cookies on 2007-06-21
> **Zavie A. said:**
> ive got the volume mounted...but it still wont allow me to delete or add files to it...so im stuck again :( lol

Unmount it, install NTFS-3G, and then use NTFS-3G to enable read/write support to it.

---

### Post by russo.mic on 2007-06-22
It's probably important to make sure you understand this:

The problem isn't permessions as such, it's more that linux by default can't write to NTFS partitons.  it can read, but no write.  I know it says permessions issues, but that's misleading.  

be careful when writing large files especially to the NTFS partiton.  It has been known to overwrite important data.  

Russo

---

