---
title: "Working with mdadm, how?"
date: 2015-09-05
forum: General Help
---

### Post by katana-9988 on 2015-09-05
Hello. I am using ubuntu 15.04 installed on 128 SSD. I have now 4TB X 2 I want to run them under software RAID 1 and mount under /mnt/rd01 (for example). I did my homework and I got the steps in how to do it. 

But I am wondering how I will be notified if one of the disk have failed in RAID? will it show a me a notification in the desktop? or lets say sent an email to me?

Thanks.

---

### Post by TheFu on 2015-09-05
I get emails, but I have an MTA configured with forwarding to an email address I actually watch/use.  Local email isn't very useful - especially when sent to root.

I'd rethink using /mnt/ too. There is an [official linux directory hierarchy]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/") which explains what existing directories are for. The /mnt is for temporary use only.  Why not mount to /rd01?

 >  This directory is provided so that the system administrator may temporarily
  mount a filesystem as needed. 

---

### Post by katana-9988 on 2015-09-05
So without an email. Will the system can notify me?

---

### Post by TheFu on 2015-09-05
> **katana-9988 said:**
> So without an email. Will the system can notify me?

You can always watch the log files using any of the normal alarming tools. That is what a professional would do.

Saying this for any lurkers - you already know it.

RAID at home is fine, if you want to learn. Not many other real-world uses for RAID at home.  Be certain you still have perfect *know-you-can-restore* backups. Backups are 1000x more important than RAID.  RAID is for 1 thing - HA - nothing else.  It is a hassle and there are things that RAID doesn't solve, but there are 1000 things that backups solve.

---

