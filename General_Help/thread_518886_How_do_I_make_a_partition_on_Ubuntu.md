---
title: "How do I make a partition on Ubuntu"
date: 2007-08-06
forum: General Help
---

### Post by kris2pe on 2007-08-06
I plan to make a separate  my ubuntu partition into 2 parts! 
Coz I will reformat the first partition & back up my files on the other!
how do I do this? Hopefully its done in gui okey!

---

### Post by tors on 2007-08-06
apt-get install gparted

and you can find information about it here:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by tszanon on 2007-08-06
> **kris2pe said:**
> I plan to make a separate  my ubuntu partition into 2 parts! 
Coz I will reformat the first partition & back up my files on the other!
how do I do this? Hopefully its done in gui okey!
If you don't need whatever there is in your partition, you can use the Live-CD and gparted to delete the current partition and create the new ones. If you need some files, then I think you still can use the Live-CD to resize the current partition to create enough space for a second partition (also using gparted).

If you have ever used Partition Magic, you'll see that gparted has a similar interface.

---

### Post by kris2pe on 2007-08-06
> **tszanon said:**
> If you don't need whatever there is in your partition, you can use the Live-CD and gparted to delete the current partition and create the new ones. If you need some files, then I think you still can use the Live-CD to resize the current partition to create enough space for a second partition (also using gparted).

If you have ever used Partition Magic, you'll see that gparted has a similar interface.

I only use Partition Magic to separate my partition on windows. But I'm sure how to configure it w/ a linux partition coz in windows I can just adjust it easier coz its partition format is NTSF. While in Linux I don't know who to go about it! 
Is there a tutorial out there? 

I already tried dling gparted. But I have no idea how to access it!

---

### Post by tszanon on 2007-08-06
> **kris2pe said:**
> I only use Partition Magic to separate my partition on windows. But I'm sure how to configure it w/ a linux partition coz in windows I can just adjust it easier coz its partition format is NTSF. While in Linux I don't know who to go about it! 
Is there a tutorial out there? 

I already tried dling gparted. But I have no idea how to access it!
To access gparted, you can type ALT + F2 and then type ```
gksu gparted
```in the box that will appear.
The partition type you should use is EXT3. It's fast, reliable and the default partition type in Ubuntu.

Besides the information above, everything will be just like in Part. Magic: select the desired partition, resize it, create a new one in the empty space and apply all changes.
Suggestions:
1. backup your files before doing anything that can destroy them.
2. you said you will use this new partition for backup. I don't recommend it, because if the drive fails, everything will be lost (the files and the backups). Consider using an other drive or cds/dvds.

---

### Post by kris2pe on 2007-08-08
Ok now the problem is I can't resize the hd! 
HELP!

---

### Post by dr.koljan on 2007-08-08
> **kris2pe said:**
> Ok now the problem is I can't resize the hd! 
HELP!

Why you can't? What is the problem? Have you tried to unmount the drive which you are resizing? (Right-click on its icon on your desktop, then 'unmount')

---

### Post by kris2pe on 2007-08-08
Um becoz I can't coz I'm using ubuntu!!!

---

### Post by dr.koljan on 2007-08-08
So why don't you load into your Ubuntu CD?

---

### Post by logos34 on 2007-08-08
the partition you are resizing cannot be mounted--you need to work from the ubuntu live CD or get Gparted live CD

---

### Post by tszanon on 2007-08-08
Yes, the partitions you need to modify must be unmounted. So, as the process involves partitions that you can't unmount (because they're needed by the running system), you must use the live-cd to modify them.

---

### Post by kris2pe on 2007-08-09
Ok I tried using my live cd! But the problem is that it doesn't do it!
I tried resizing it! And it refuses to do it! I don't know why!
It just doesn't want  me to do it! And the details aren't shown to me!

---

