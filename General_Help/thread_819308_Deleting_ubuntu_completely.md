---
title: "Deleting ubuntu completely"
date: 2008-06-05
forum: General Help
---

### Post by Zophixan on 2008-06-05
Hiya, for warrenty purposes, I need to delete ubuntu completely. What I did was, I booted into a live disc, and deleted all the partitions. I then tried to reinstall windows xp - but it can't detect any hard disks at all! I then tried to format the free space into ntfs using a live disc. Still didn't work. Confused I let it boot up without a disc in, and it says "grub error" or something to that effect, which i find baffling, since I deleted all the partitions, surely theres nothing left? Anyway, how would I go about deleting grub completely, and also making my ntfs disk detectable?

---

### Post by rraj.be on 2008-06-05
Are you using 

```
two hard disk's.
```

---

### Post by Zophixan on 2008-06-05
haha nope :-p Its definately only one physical hard disk, with everything deleted, and formated to NTFS.

---

### Post by wpshooter on 2008-06-05
> **Zophixan said:**
> Hiya, for warrenty purposes, I need to delete ubuntu completely. What I did was, I booted into a live disc, and deleted all the partitions. I then tried to reinstall windows xp - but it can't detect any hard disks at all! I then tried to format the free space into ntfs using a live disc. Still didn't work. Confused I let it boot up without a disc in, and it says "grub error" or something to that effect, which i find baffling, since I deleted all the partitions, surely theres nothing left? Anyway, how would I go about deleting grub completely, and also making my ntfs disk detectable?

IF you have NOTHING on the hard drive that you need to keep you can WIPE it cleaning using [www.killdisk.com](www.killdisk.com).

Good luck.

---

### Post by rraj.be on 2008-06-05
boot to live cd and use some check what its showing for the following

and post its output.

```
sudo fdisk -l
```

Also check in system monitor what its showing for your file system report.

---

### Post by doorman on 2008-06-05
[FONT=Verdana]do you have sata disks? if so, maybe you need a win xp installer with sata drivers built in, because not all win xp versions have that. Try the win xp sp2 one[/FONT]

---

### Post by Pjotr123 on 2008-06-05
You'll need to remove Grub from the Master Boot Record. Here's how:
[http://ubuntutip.googlepages.com/grub](http://ubuntutip.googlepages.com/grub)
(number 2 )

Greeting, Pjotr.

---

### Post by rraj.be on 2008-06-05
Yup.

If you want your HD to be clean use some wiping utilities.

it will clear completely including EACH bit [including MBR]

---

### Post by bodhi.zazen on 2008-06-05
Step-by-step instructions : [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Zophixan on 2008-06-05
Hey guys thanks for the replies, I think its the sata problem as one person suggested. Now I'm having problems finding drivers which work! Can anyone provide help on that? I have a hp dv8263ea, i tried the manufactor site, but it doesn't seem to work once slipped streamed!

---

### Post by rraj.be on 2008-06-05
What is the result of wiping the whole drive.

I think that will solve.

Just try that [just a 10 minuets job] before trying o other's

---

