---
title: "Is Gparted stuck or just taking a long time?"
date: 2016-04-10
forum: General Help
---

### Post by Evil Wayz on 2016-04-10
After receiving SMART warnings from my primary drive, I decided to clone it.  Since I was replacing it anyways, I bought a much larger drive.  So when I cloned the drive using "dd"  it created an exact copy of my 40 gb drive on the new drive. The new drive is 2 tb.  So I attempted to resize the drive and add a swap partition.

I set this up and hit enter, and it starts thru to the check, and then the progress bar stops.  I have hit cancel and the log shows it has fixed some inodes.  Am I just being impatient, or should I forget about expanding it and just create a secondary partition with the rest of the space.

Also, how do I tell Ubuntu where the new swap partition is?

Using 14.04.4, Cinnamon 2.8, with the 4.3 kernel.

---

### Post by yancek on 2016-04-10
Did you try to resize using the GParted bootable CD/flash drive or the Ubuntu DVD/flash drive.  You can't do it from an installed system.

It's hard to say if you are  being impatient since you give no information on how long you waited.

---

### Post by Evil Wayz on 2016-04-10
I'm using Linux Mint from a flash key.  As of this post it's been an hour.

---

### Post by Evil Wayz on 2016-04-11
So I cancelled the operation, and then cut and pasted each command to terminal and executed, and it work.  Apparently my computer didn't like hte graphical interface.

---

