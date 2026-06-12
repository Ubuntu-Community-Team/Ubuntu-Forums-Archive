---
title: "dd command stops after 1.1 GB"
date: 2007-02-28
forum: General Help
---

### Post by kirsche on 2007-02-28
Hello,

I'm trying to create an ISO from a data dvd on a feisty box.
The dvd is readable and accessible.

I ran:
kirsche@bulmers:/data$ dd if=/dev/scd0 of=dvd_1.iso
2097151+0 records in
2097151+0 records out
1073741312 bytes (1.1 GB) copied, 370.089 seconds, 2.9 MB/s
kirsche@bulmers:/data$ 

The dd only copies 1.1 GB of the 4.4 GB DVD image...
The target filesystem is ext3.
Specifying bs and count didn't change the result either

Did anyone saw this behaviour too?
Thanks

---

### Post by LotsOfPhil on 2007-02-28
Hmm. Is the DVD all "one track" ?

---

### Post by kirsche on 2007-02-28
Don't know...
I used a fedora box now to do the copy - works there without a problem

---

### Post by Praill on 2007-02-28
Why dont you use some better image creating software like k3b?

---

### Post by digen on 2007-02-28
Could you check the /var/log/messages just after that command exits to prompt ?

> #sudo tail -f /var/log/messages

---

