---
title: "scrot fills up hard drive"
date: 2015-03-13
forum: General Help
---

### Post by Moofus on 2015-03-13
for my school, we monitor students activity by screenshots, so i set up a crontab with scrot that runs every minute and ouputs to "/home/student/.rar/hour:{minute}" so only the minute field is changeable, and each new one will overwrite a previous one, so there will only be 60 in the folder at any one time. after a couple weeks, messages start showing that there is only megabytes of disk space left.  i look in the folder, and there are still only 60 screenshots in it, however, gparted shows the drive almost full.  what is going on?

---

### Post by Lars Noodén on 2015-03-13
You can try running the Disk Usage Analyzer (baobab) to get a graphical display over what is taking up your space.  Or you could try [du](http://manpages.ubuntu.com/manpages/trusty/en/man1/du.1posix.html) instead if you are logging in remotely.

---

### Post by Moofus on 2015-03-14
would it work just to create a separate small partition for the screenshots?

---

### Post by Lars Noodén on 2015-03-14
It would but only if scrot is the cause of the partition filling.  What did the disk usage say?

---

### Post by Moofus on 2015-03-14
i wasnt able to check, its at school.

---

### Post by Lars Noodén on 2015-03-14
Ok.  Then just log in with SSH from where you are and use [du](http://manpages.ubuntu.com/manpages/trusty/en/man1/du.1posix.html)

```

cd /
find . -maxdepth 1 -type d -exec du -sh "{}" \;

```

Or else check next time you have access.

---

### Post by Moofus on 2015-03-16
yeah ill just check tomorrow

---

### Post by Moofus on 2015-03-17
alright! i just checked disk usage analyzer, and it turns out, it wasn't scrot at all! 
the problem was how i copied the partition over. i just used dd to mirror the 5.7GB partition on my flash drive to the main 75+ GB partition on the hard drive. Apparently, even though gparted showed 75+ GBs almost full, it was still only a 5.7 GB partition. so now i think ill just copy the partition to the hard drive with gparted and then resize it bigger.

but, why would dd do that? i thought it would just overwrite the first 5.7 gigs of data and leave the rest blank and usable.

---

### Post by Holger_Gehrke on 2015-03-18
> **Moofus said:**
> 
but, why would dd do that? i thought it would just overwrite the first 5.7 gigs of data and leave the rest blank and usable.

Because you told it to ...

You probably did something along the lines of
```

dd if=/dev/sdb of=/dev/sda

```
(with "sdb" being the flash drive and sda the hard disk and neither with a number for the partition)
and this copies the whole disk **including the partition table**.

---

### Post by Moofus on 2015-03-18
hmm interesting.
ok so now what do i do? do i close the thread or mark it solved?

---

### Post by Lars Noodén on 2015-03-18
It's up near the top-right of the page under "Thread Tools"

---

### Post by Moofus on 2015-03-18
alright!

---

