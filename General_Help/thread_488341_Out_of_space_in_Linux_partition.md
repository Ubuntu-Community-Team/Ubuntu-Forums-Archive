---
title: "Out of space in Linux partition"
date: 2007-06-30
forum: General Help
---

### Post by icemarle on 2007-06-30
Bah, I wasn't careful enough. I installed Xubuntu because I wanted to save on space... I had enough space for the installation itself. After using Xubuntu for some time, I downloaded some programs until it finally cracked. I'm stark out of space and I lost the ability to log-in. So I retreated back to Win XP. I used Ext2 IFS to access my Linux partitions through Windows. So now... I need to know what files are safe to delete. I don't really want to experiment with stuff and end up ruining everything.

---

### Post by Tea4all on 2007-06-30
Easier way, Just start up xubuntu, and try to log in "failsafe XFCE" under options,session.  If this does not work try to log in "failsafe terminal.  remove extra files!

---

### Post by icemarle on 2007-06-30
It boils down to the same thing. I still need to remove some files... I just want to know which are safe to delete...

---

### Post by God Of Atheism on 2007-06-30
I had the same think on Ubuntu and my solution to get it running again was to resize the partition using a gparted bootdisc.

Still, I don't understand why there would have to be any available free space on the / partition at login time.

Also I don't have an answer as to what is safe. In general any optional programs are safe to delete, as well as all documentation, but you probably have most programs for a reason and documentation is practical to have. I assume you use a separate /home partition, that one tend to get filled.

Emptying the wastebasket might also help.

---

### Post by icemarle on 2007-07-01
I don't have any trash. If i had, I obviously would've deleted them already. I guess I ought to resize my partition... as much as I don't want to XD I really need to get a bigger hard drive... :(

---

### Post by CrispyFried on 2007-07-01
/var/cache/apt/archives/ has copies of downloaded install files, you can delete them or copy them elsewhere.

---

### Post by confused57 on 2007-07-01
Don't know if this will help or not:
[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by icemarle on 2007-07-02
Thanks :) Those help a lot ^^

---

