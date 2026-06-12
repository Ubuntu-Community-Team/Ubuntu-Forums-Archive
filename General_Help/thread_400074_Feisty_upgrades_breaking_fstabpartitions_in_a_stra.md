---
title: "Feisty upgrades breaking fstab/partitions in a strange way?"
date: 2007-04-03
forum: General Help
---

### Post by Tybee on 2007-04-03
During the recent updates in Feisty, I'm noticing a strange issue involving one of my partitions. I have three major partitions (excluding the swap): Windows (NTFS), Storage (NTFS), and Ubuntu.

My Storage partition, for the record, is 250 gigabytes with 100 gigs free.

During one update a while back, Storage suddenly vanished from the Places menu and my desktop along with Windows. Lo and behold, it's there in my /media/ directory. I open it up, and there's absolutely nothing in there and it says there's only 35 gigs free. Scared to death I reboot to Windows and the partition is perfectly fine. Well, more recently, another update seemed to fix the problem. "Storage" and "Windows" is back again on my desktop and in Places. I'm happy. Two days later, another update does something strange. This update says I need to perform a partial upgrade. No problem. It runs, I reboot, and now Storage is gone. Windows is still there. Storage is listed under the Computer icon, but it's black. When I open it, I'm presented with a security box telling me that drive is restricted to administrators. I put in my password and there's all my data.

Now, here's more strangeness. My music is on Storage. I open my music player and it can't find any of the music at all. I wonder what's going on. After a little poking, I notice something. Under the /media/ folder, there is Storage and "Storage_". "Storage" has nothing in it, and claims is only 35 gigs free. Much like my problem when this first started. "Storage_" has everything in it and shows up correctly. I modified my FSTAB and commented out the Storage drive, just to experiment. I reboot, and nothing was affected. I still have "Storage" and "Storage_"

Simple question: how do I fix this? How do I make everything right again so that I no longer have that mysterious phantom partition with 35 gigs and my Storage drive shows up properly on my desktop and doesn't prompt me for an administrator login box when I want to open it?

---

