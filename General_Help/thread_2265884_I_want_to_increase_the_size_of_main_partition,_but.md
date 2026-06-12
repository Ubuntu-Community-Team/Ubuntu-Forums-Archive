---
title: "I want to increase the size of main partition, but swap partition is in the middle.."
date: 2015-02-18
forum: General Help
---

### Post by carlos7 on 2015-02-18
Hello all!

I attach here how my partition system looks like. As you can see, I have a 500 GB unallocated space, then the swap partition, and then, the root partition (yes, I did it wrong from the beginning, I know...But I just wanted to give Ubuntu a try...). Now, I would like to put the swap partition at the beginning of the unallocated one, and then combine the rest, so that the main partition is bigger, but I have no idea how to do it using Gparted (or at least, I can't move/resize). Could anyone help me? Thanks!!

---

### Post by SuperFreak on 2015-02-18
Partitions have to be unmounted in order to make changes. Perhaps someone will confirm this but I don't think unallocated space can be added from the left side to a partition on the right in GParted.


You might want to use the Live DVD/USB to make any changes

---

### Post by carlos7 on 2015-02-18
Mmm I see. I also tried formatting is as ext4 first, but it didn't work. I cannot move/resize the swap partition :(

---

### Post by SuperFreak on 2015-02-18
right click on swap partition and choose Swapoff
I suspect the only way you are going to get what you want is a reinstall of Ubuntu preceded by a Live disk creation of the partitions you want

---

### Post by carlos7 on 2015-02-18
Ok, I will try that! Thanks!

---

### Post by carlos7 on 2015-02-18
Well, this is how I made it!

- First, I Swapedoff, and I was able to move it to the left!
- Then, I rebooted praying that there were no problems (no problems at all!)
- Then, I decided to keep the original root partition as a system one, and the 500GB as the /home directory. I followed this instructions: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Everything was smooth and worked perfectly fine!

---

### Post by SuperFreak on 2015-02-18
Great. You can mark this thread SOLVED

---

