---
title: "Windows shared partition"
date: 2006-11-17
forum: General Help
---

### Post by Loyid on 2006-11-17
Hi all,

I just joined Ubuntu and I need help on the following issue:

I partitioned my hard disk with the installer of Ubuntu 6.10. 
I set the windows partition at 15GB, a swap partition 1GB, a 10GB partition for Ubuntu and the remaining partition is meant to be shared among the 2 OS (windows XP and Ubuntu). All partitions are fat32 and primary partitions.

I can access all the partitions from Ubuntu but Windows is not able to see them. The only partition that shows up in windows is the 15GB partition containing Windows itself. All the other partitions are not even listed.

How can I do in order to see at least the shared partition in Windows? No problem at reformatting if necessary

Many Thanks:)

---

### Post by taurus on 2006-11-17
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Swab on 2006-11-17
> **Loyid said:**
> Hi all,

I just joined Ubuntu and I need help on the following issue:

I partitioned my hard disk with the installer of Ubuntu 6.10. 
I set the windows partition at 15GB, a swap partition 1GB, a 10GB partition for Ubuntu and the remaining partition is meant to be shared among the 2 OS (windows XP and Ubuntu). All partitions are fat32 and primary partitions.

I can access all the partitions from Ubuntu but Windows is not able to see them. The only partition that shows up in windows is the 15GB partition containing Windows itself. All the other partitions are not even listed.

How can I do in order to see at least the shared partition in Windows? No problem at reformatting if necessary

Many Thanks:)

I may be wrong, but I think Windows will only entertain 3 primary partitions.  Perhaps 4 primary partitions has confused Windows?

Edit: Actually I think I am wrong :)

---

### Post by taurus on 2006-11-17
4 primaries, 1 extended with many logicals...

---

### Post by Loyid on 2006-11-17
Thanks for the replies but if I am not wrong Win deals with up to 4 primary partitions.

 
Isn't the info contained in [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
for the case in which you have made the partitions in win and want to mount them in Linux? I have the opposite problem. I created the partitions with Ubuntu installer and want to see them in Win. 

Thanks.:-k

---

### Post by Swab on 2006-11-17
One question, why did you make then all fat32?  Sorry I can't actually help but I just wonder why you are installing Linux onto a fat32 partition.

---

### Post by Loyid on 2006-11-17
my HD is goes only at 4200rpm, with a fat32 is slightly faster.

---

### Post by taurus on 2006-11-17
You CANNOT install Ubuntu on a fat32 filesystem since bad things will happen to your Ubuntu...

---

### Post by Loyid on 2006-11-17
Would you be so kind to explain me why?

Thanks

---

### Post by taurus on 2006-11-17
Because of permissions.  You can't set permissions with fat32 and Linux is all about permissions.  There must be some articles about it on the web but I am too lazy to do any search right now so I guess if you want to learn more, you just have to try google then.

---

### Post by greeklegend on 2006-11-17
Does the ubuntu installer even LET you install it to Fat32?

---

### Post by Loyid on 2006-11-17
YEs it did. So can I reformatr it again and change the partition onto a ntfs? how can I do it? with the ubuntu installer?

---

### Post by taurus on 2006-11-17
> **Loyid said:**
> YEs it did. So can I reformatr it again and change the partition onto a ntfs? how can I do it? with the ubuntu installer?
You CANNOT install Ubuntu on NTFS, either.  If you want to install Ubuntu, make it as ext3...

---

