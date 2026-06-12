---
title: "Pleas help! I'm desperate.  I've lost ALL my files."
date: 2006-11-13
forum: General Help
---

### Post by Justinl1qgu on 2006-11-13
Last night Ubuntu crashed for the firts time since I've had it.  Strange.  I had to reboot 3 times then evreything seemed normal.  I installed crossover office, but it didn't work, so I worked on a spreadsheet from my home forlder for a while and went to bed.  This morning I turned my computer on and my home folder is wiped clean!  There is nothing in it at all.  I can't even log in without using failsafe terminal mode.  

This is a panic for me.  I have my whole life in that folder and no backup.  

Right now I just want to recover my files.  I'll worry about fixing the system later.

If anyone knows what to do please give me a hand.

Thanks,
Justin

---

### Post by taurus on 2006-11-13
Boot into recovery mode and paste the output of these three commands here!

```

df -h
ls -la /home
du /home

```

---

### Post by wieman01 on 2006-11-13
Don't want to hijack the thread but perhaps you have to make use of the pipe so that you can copy the output to another computer that is connected to the Internet:
> df -h >> file1.txt
ls -la /home >> file2.txt
du /home >> file3.txt
You may also have to mount an external device (e.g. USB stick or HD). Sorry for meddling...

---

### Post by Justinl1qgu on 2006-11-13
Thanks for the fast responses.  I have solved the problem.  Crossover wiped out my fstab.  I restored an earlier version and rebooted.  Ubuntu kindly offered to scan the hard drives.  I don't know what it found but it fixed it.  I'm back up and running.

---

### Post by NorthCoast on 2006-11-13
now do a backup....

---

### Post by megamania on 2006-11-13
> **NorthCoast said:**
> now do a backup....
That's what I was going to say... you have ALL your life on a hard disk and don't have a backup?
I was like you until 5 years ago - backed up to cd every now and then. When my friend lost all of his data, I went out and bought a second hard disk with a removable tray.
Since then, whenever I upgrade my hard-disk, I always buy two of them and backup regularly.

If you think 70-100 euros is too much for a second hard disk, just ask yourself "how much would I be willing to pay to have my data recovered?"...

---

### Post by wieman01 on 2006-11-13
"rsync" is a reliable command-line tool for backup. Check this out (using it myself):

[http://www.ubuntuforums.org/showthread.php?t=187894]("http://www.ubuntuforums.org/showthread.php?t=187894")

Wiki: 

[http://www.linuxwiki.de/rsync]("http://www.linuxwiki.de/rsync")

---

### Post by jms1989 on 2006-11-13
> **megamania said:**
> That's what I was going to say... you have ALL your life on a hard disk and don't have a backup?
I was like you until 5 years ago - backed up to cd every now and then. When my friend lost all of his data, I went out and bought a second hard disk with a removable tray.
Since then, whenever I upgrade my hard-disk, I always buy two of them and backup regularly.

If you think 70-100 euros is too much for a second hard disk, just ask yourself "how much would I be willing to pay to have my data recovered?"...

I use an external bootable backup program, off a CD, to backup my Linux. It's called "True Image 9.0". I backup my computer when I get ready to perform a upgrade to vital files or install a suspicious app. I back it up to a external HDD 160GB (FAT-32) from a 40GB HDD. I'm sure you can Google the app to purchase and download it, it maby $40 USD, and you just burn it to a CD, restart, boot to CD, and there you go. It's originly for windows but it works just fine for me.

---

### Post by wieman01 on 2006-11-13
> **jms1989 said:**
> I use an external bootable backup program, off a CD, to backup my Linux. It's called "True Image 9.0". I backup my computer when I get ready to perform a upgrade to vital files or install a suspicious app. I back it up to a external HDD 160GB (FAT-32) from a 40GB HDD. I'm sure you can Google the app to purchase and download it, it maby $40 USD, and you just burn it to a CD, restart, boot to CD, and there you go. It's originly for windows but it works just fine for me.
You may also use Partimage & RescueCD if you don't want to spend 40$. There is another guide for full system backup:

[http://www.ubuntuforums.org/showthread.php?t=287522]("http://www.ubuntuforums.org/showthread.php?t=287522")

---

### Post by megamania on 2006-11-14
> **jms1989 said:**
> I use an external bootable backup program, off a CD, to backup my Linux. It's called "True Image 9.0". I backup my computer when I get ready to perform a upgrade to vital files or install a suspicious app. 
I know True Image, but since I backup regularly I prefer to use rsync. This way I create a mirror of my home partition in seconds, because it only touches the files that were added/modified/deleted on the source.

By the way, I have an old True Image backup of my Windows partition, which I don't use anymore. I'd just need to extract a few files, but the cd that I have (I downloaded it from the official website 7/8 months ago) doesn't like my Linux partitions (ext3), so I have nowhere to extract to, because I have no Windows installed. In other words, I can see the files but can't save them.

Is the version you are using capable of _writing_ files to linux partitions?

---

