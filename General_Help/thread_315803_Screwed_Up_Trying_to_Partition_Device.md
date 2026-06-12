---
title: "Screwed Up Trying to Partition Device"
date: 2006-12-09
forum: General Help
---

### Post by preyer on 2006-12-09
I was trying to repartition my hard drive such that I could have a separate /home partition. my original root partition was stuck somewhere in the middle of the space I wanted to use for the new /home drive.
I copied the old root directory to a new place and that worked properly. Then I had two copies of my data, then I decided to delete the partition where the old data was saved, seems that this screwed up copied data and now it is formatted in linux-swap and i have lost all the data. 

Is there any way to get it back, I am using the live cd I'm scared or resetting the computer because I really want this data back.

If anyone has any possible ideas on how the get the data back I'll be indebted to you.

Thanks

P.S. - Yes I'm an idiot for not backing up the data before playing around with partitioning.

---

### Post by lemonsCC on 2006-12-09
The issue may be that your fstab doesnt know where / is....update your fstab accordingly....see this page:
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by preyer on 2006-12-09
Thanks for your help,
I managed to solve the problem using gpart, I had deleted the main Linux partition and it found it, but couldn't find my windows parition. That isn't a major problem, I was thinking of reinstalling windows again.

What this really made me realize is the importance of backing up.

---

