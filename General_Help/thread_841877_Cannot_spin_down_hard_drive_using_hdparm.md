---
title: "Cannot spin down hard drive using hdparm"
date: 2008-06-26
forum: General Help
---

### Post by antechinus on 2008-06-26
This does not work for my machine:

```
sudo hdparm -S 120 /dev/sda1
```

I get the following reply:
```
/dev/sda1:
 setting standby to 120 (10 minutes)
```

But the hard drive is still whirrring away after 10 minutes and beyond.

What could the possible problems be, so I may diagnose?

---

### Post by ryanhaigh on 2008-06-26
This will only work if no data on the drive is accessed for the full 10 minutes. You could try using the -y option to spin down the drive immediately just to test if it works. Other than that you might want to look at adding the noatime to you fstab options for the filesystems associated with the disk you want to spin down.

---

### Post by sdennie on 2008-06-26
You will have to do something to drastically reduce your disk accesses.  Otherwise Ubuntu writes the disk about every 5 seconds and you'll never get into standby mode.  See this guide: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

---

