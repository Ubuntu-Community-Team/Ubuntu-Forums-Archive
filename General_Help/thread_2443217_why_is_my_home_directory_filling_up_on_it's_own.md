---
title: "why is my /home directory filling up on it's own?"
date: 2020-05-12
forum: General Help
---

### Post by 777funk on 2020-05-12
I had 100GB and it was full so I expanded the partition to 450GB and within a week it was full. I am pretty sure I didn't put this additional amount of data on the drive. 

Any ideas on what could be happening?

---

### Post by 777funk on 2020-05-12
Ok I think it has to do with LuckyBackup. Maybe the snapshots are being stored to the drive that it's reading from...

---

### Post by CelticWarrior on 2020-05-13
> **777funk said:**
> Ok I think it has to do with LuckyBackup. Maybe the snapshots are being stored to the drive that it's reading from...

If so that's not a backup.

---

### Post by dino99 on 2020-05-13
I'm sure you are able to find those huge files by glancing at /home and its subdirs  ;)

---

### Post by monkeybrain20122 on 2020-05-13
You can use the disk usage analyzer (already installed by default) to scan your home directory, it will tells you the size of the subdirectories, what are in them and when they were last modified.

---

### Post by ActionParsnip on 2020-05-13
What is the output of:

```

cd $HOME
du -sch .[!.]* * |sort -h

```

What is the output please?

---

### Post by HermanAB on 2020-05-13
Note that if you have a problem with collections of data containing duplicated files - government forms, pictures, etc - you can recover the space with a program called *hardlink*, without having to delete anything.

---

