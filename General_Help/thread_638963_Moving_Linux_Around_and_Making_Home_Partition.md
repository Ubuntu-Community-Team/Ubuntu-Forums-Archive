---
title: "Moving Linux Around and Making Home Partition"
date: 2007-12-12
forum: General Help
---

### Post by lvleph on 2007-12-12
Currently I have 4 partitions.

Windows NTFS 15G | Media NTFS 65G | Linux ext3 13G | swap < 1G 
(not sure where the rest of my 100G is)

What I want to do is repartition it to look like this.

Linux ext3 10G | Home ext3? 78G?  | Test Linux ext3 5G | swap 1-1.5G (I have 1G Ram, but video shared)

What are the problems that will arise in the process of doing this, or what should I be aware of? I want to use my current Ubuntu, so how will that work moving from the back of the drive to the front? I will have to figure out the home partition still, but there are plenty of threads on that. What about the size of the swap and the Test Linux?

---

### Post by lvleph on 2007-12-12
Well, no one seems to be ready to answer my questions so I will post a few things I have found.

[Backup Ubuntu](http://www.uluga.ubuntuforums.org/showthread.php?t=35087&highlight=restore+ubuntu+from+backup)
[Restore Grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

So my question about moving Ubuntu has been answered.

---

### Post by atlfalcons866 on 2007-12-12
try this web page

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by lvleph on 2007-12-12
Well, I started the process. I was restoring the backup I made. When it got to a file cdrom and said that the date was in the future and then quit. Now I am stuck with a system that cannot boot. Also, the GRUB instructions didn't quite cover everything, but it informed me enough to be able to get it to boot to the correct directory using the edit function. I don't know much about using GRUB in command line. Right now I am using my wife's computer to see if I can correct the cdrom file issue.

---

