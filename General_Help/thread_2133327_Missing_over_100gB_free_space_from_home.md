---
title: "Missing over 100gB free space from /home"
date: 2013-04-07
forum: General Help
---

### Post by RideTheSpiral on 2013-04-07
Ever since I started using ubuntu a few years ago, I've had my /home partition on it's own hard drive. Lately though I've had no free space even though I've deleted stuff I didn't need and emptied the trash. df -h shows this: /dev/sdb1       459G  459G     0 100% /home.. When I right click on home in nautilus and hit properties, it only adds up to 325gb of used space.

Please help :(

---

### Post by nerdtron on 2013-04-08
Can you give some more details on the layout of your partitions? I mean, how big is the entire hard drive and how much is allocated to your root partition and home partition.

You can try this command to determine the folders with the highest usage in your system.
```

du -m / | sort -n -r | head -n 10
```

It's a three part command. The first part is telling the computer to display the disk usage of the "/" or root directory, you can change it to a specific directory that you want (/home if you want it to scan the /home directory). The second part is sorting the output of the command numerically in reverse order so that the highest ones are listed first. The third part shows only the top 10 highest disk usage directories, you can change it to 20 or something that you would like.

It would take a bit of time to scan your root directory (or your /home if that what you inputted) if you have a big drive and a lot of files so be patient.

---

### Post by kurtguenther on 2013-04-08
I have the same problem.  I'm using Ubuntu 12.10 and a 300GB drive.  Things filled up unusually fast. 

245192  /home/kurtg
41575   /home/kurtg/VirtualBox VMs
22539   /home/kurtg/Documents
10374   /home/kurtg/Pega

I get the same results with Disk Usage Analyzer: 

/home/kurtg   100%   257.1 GB
Virtualbox        17%   43.6 GB
Documents        9.1%  23.6 GB
Pega                 4.2%  10.9 Gb

Things drop away to megabyte region after that.   Maybe 2 GB of space there. 

My only thought is that it might be the encrypted home directory.   ?? 

--Kurt

---

### Post by kurtguenther on 2013-04-08
I looked at my /home/kurtg/.Private and it's 257GB, so that's my problem.   Is there a way to compact the home directory, so I can get some of this space back for the system?   It looks like this is a common problem on Macs, but I can't find a solution for ubuntu.

---

### Post by RideTheSpiral on 2013-04-08
I figured it out by using /forcefsck and rebooting. Not sure why over 100gB of free space wasn't available but it is now :)
I have /home on a separate 500gB hard drive. Root is on an SSD. Not that it really matters now.

---

