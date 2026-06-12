---
title: "[SOLVED] hard drive full"
date: 2008-02-24
forum: General Help
---

### Post by midgemiles on 2008-02-24
I have a 120 gig hard drive on which I have Ubuntu and 4.8gig of data, mainly evolution mail files.
The system monitor says the directory "/ " type ext3 has total 108 gig, with 7.5gig free, and 2.0gig available.  I don't understand how Ubuntu can be taking up so much space. The Garbage bin is empty.
The Disk Usage Analyser tool reports there is a total of 8.1 gig used in "/ " and subdirectories.
Is there a hidden block of files that I can't get at?  I have removed all packages not required using Synaptic.
Any ideas?

---

### Post by dcstar on 2008-02-24
> **midgemiles said:**
> I have a 120 gig hard drive on which I have Ubuntu and 4.8gig of data, mainly evolution mail files.
The system monitor says the directory "/ " type ext3 has total 108 gig, with 7.5gig free, and 2.0gig available.  I don't understand how Ubuntu can be taking up so much space. The Garbage bin is empty.
The Disk Usage Analyser tool reports there is a total of 8.1 gig used in "/ " and subdirectories.
Is there a hidden block of files that I can't get at?  I have removed all packages not required using Synaptic.
Any ideas?

Tools run at user level will only report on files that they have read access to, run them with **sudo** and see what is reported.

You should also run a fsck on the partition (using the Live CD).

---

### Post by pebo on 2008-02-24
```
sudo find / -type f -size +100000k
```will list any files over 100MB. Possible culprits are log files in /var/log and hidden .trash files in /root.
HTH

---

### Post by r4ik on 2008-02-24
> **pebo said:**
> ```
sudo find / -type f -size +100000K
```will list any files over 100MB. Possible culprits are log files in /var/log and hidden .trash files in /root.
HTH

Think it is k not  K

---

### Post by midgemiles on 2008-02-24
Thankyou all for your tips.  From these I have discovered that the problem is due to backup files from the "simple backup" programme, which I have set to create backups by logarithmic method.  It is supposed to erase all but one file per month and one per year as time progresses, but I seem to have one backup for every day computer was turned on since October 2007, leading to 95 gig of files!
I will now have to investigate why simple backup hasn't culled the older files...  All these files had owner = root, so I changed owner to my user name and then deleted most of them.
cheers!

---

