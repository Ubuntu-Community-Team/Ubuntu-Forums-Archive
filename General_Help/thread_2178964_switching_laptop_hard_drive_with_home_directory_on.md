---
title: "switching laptop hard drive with /home directory on it"
date: 2013-10-05
forum: General Help
---

### Post by taopublic on 2013-10-05
Hi I have Ubuntu 12.04 installed on my laptop. The / is mounted on one ssd drive but swap and /home on a regular hard drive. Recently the regular hard drive died and I need to replace it. How do I make the switch w/o having to re-install the system? I've already backup all my data. Thanks!

---

### Post by oldfred on 2013-10-05
You should be able to create a new swap & /home on your new drive. Then in fstab replace the UUIDs of old partitions with the new one's.
You may be able to even boot SSD. It will work without swap especially if you have a fair amount of RAM. And it may make a new default /home in SSD, just do not confuse that with the /home you want on hard drive. 

I have a slightly different configuration as I keep /home on my SSD, but have all data including some of the normally hidden folders like Firefox & Thunderbird profiles in my data partitions on my hard drive. Then my /home on SSD is like the default with only the hidden user configuration files (which I do also backup). I then link all folders in my data partition to my /home so it looks and acts like a standard /home with data.

---

