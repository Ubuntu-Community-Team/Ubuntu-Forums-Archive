---
title: "Merge partitions"
date: 2006-10-23
forum: General Help
---

### Post by Carwood on 2006-10-23
My HD is partitioned like shown here:
[http://img140.imageshack.us/img140/6773/screenshotgpartedyj4.png](http://img140.imageshack.us/img140/6773/screenshotgpartedyj4.png)
How can I merge the unallocated space with sda3?

---

### Post by CatKiller on 2006-10-23
Move your sda3 partition to the left, and then resize it to the right. You'll probably need the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"), since I don't think the version on the Ubuntu cd can move ext3 partitions.

---

### Post by Kateikyoushi on 2006-10-23
As far as I know you can't move the beginning of an ext3 filesystem.
So could create a new ext3 in the free space, copy the files there and then resize this new partition because the end can be moved, extended.

---

### Post by CatKiller on 2006-10-23
> **Kateikyoushi said:**
> As far as I know you can't move the beginning of an ext3 filesystem.

From the [GParted news page]("http://gparted.sourceforge.net/news.php"):

> **04 September 2006 : GParted 0.3**

It took a bit longer than expected, but finally we decided to release GParted-0.3.
This release includes one of the most exiting features since the first release;
**We finally have full move support!!** Although it should be considered a bit experimental, our tests worked out perfectly and we didn't see any errors so far.

---

### Post by Kateikyoushi on 2006-10-23
Good to know, seems I am not up to date.

---

### Post by JMO707 on 2006-10-23
Hi there. Sorry about using your thread :p

I want to format /dev/hda1 & /dev/hda8, then merge them with my Ubuntu partition /dev/hda7

Screen:

[[IMG]http://show.imagehosting.us/show/1696462/0/nouser_1696/T1_-1_1696462.png[/IMG]](http://www.imagehosting.us/index.php?action=show&ident=1696462)

My fear is that the /dev/hda1 is a logical partition, and the rest not. Even if I dont know what that means, it puts me in a doubt =s

---

### Post by CatKiller on 2006-10-23
> My fear is that the /dev/hda1 is a logical partition, and the rest not. Even if I dont know what that means, it puts me in a doubt =s

Actually hda1 is the only one that **isn't** a logical drive - it's a Primary partition. The others are logical drives in an Extended partition.

> **JMO707 said:**
> I want to format /dev/hda1 & /dev/hda8, then merge them with my Ubuntu partition /dev/hda7

You might not, you know. You can probably get rid of the hda8 partition with no problems and extend your hda7 into the space, but if you get rid of hda1, the number of hda2, the Extended partition, will probably change. Which may make everything else inaccessible.

Have you considered just mounting that partition into your filesystem and deleting everything that's on it?

---

### Post by Carwood on 2006-10-23
Thanks for your responses.
It worked for me with the gparted live cd. Thanks!

---

### Post by TiredBird on 2006-10-23
You got lucky. 

I have used GParted several times and I have crashed twice, wiping out my partition tables in the process. Once it was recoverable, the other time not.

Yes, the moves supposedly work but they're still iffy. In particular, I don't trust them to move or resize logical partitions, primary yes, but logical no. That's where they seem to have the most problems.

I liked the suggestion that was made to put a partition into the empty space, then transfer the data from your live partition to it, then wipe out the current partition and resize the new one to take up the whole disk. That way, you are not letting the partitioner move your data and I don't trust it to do that yet.

Yes, it is wonderful that they finally have full move but in their own words it's still experimental. BE CAREFUL.

---

### Post by JMO707 on 2006-10-24
I solve that issue reinstalling CatKiller. Now, I would want to add that free space to the /dev/hda5 partition. Is there any way of do that without using a newer version of gparted?

[[IMG]http://show.imagehosting.us/show/1698711/0/nouser_1698/T1_-1_1698711.png[/IMG]](http://www.imagehosting.us/index.php?action=show&ident=1698711)

---

### Post by TiredBird on 2006-10-24
What you are trying to do is almost exactly what I was trying to do on the two occasions that I crashed. Your hda5 is a logical partition and in order to use the empty space below it you have to move the data in hda5. That is a recipe for disaster in my opinion.

I'm looking at your partition layout to see if there might me a safer way to go about it.

Let me look for a few minutes then I'll get back to you.

---

### Post by TiredBird on 2006-10-24
I had it all written up, step by step, but I timed out and lost it. Don't understand why the forum keeps timing me out. Guess it's because I'm too long winded.

Anyway, the jist of it was to use the new [GParted Live CD ]("http://gparted.sourceforge.net/") but NOT in a transaction that has it moving data you have in partitions. Use it to expand partitions toward the high end or shink them from the high end, remove them, etc. but never to move data.

Here it is in a nutshell. 

Delete the swap partition. Move the low end of hda2 up to match the low end  of hda5. Then expand hda1 to fill the empty space. Move as much data as possible from hda5 to hda1 (using normal Linux commands), then shrink hda5 from the right. Add a partition above hda5 and move the rest of the data from hda5 into it. 

Then wipe out hda5. Expand hda1 to fill the empty space. Copy the rest of the data from the new high end partition into hda1. 

Delete the high end partition. Put a swap partition in the high end. Then expand hda1 to take up the rest of the space.

At all times, use GParted for one step at a time. Apply each step after putting it in. Do not wait and batch the steps. Periodically, boot into the Linux system and verify that you have what you think you have. DON'T TRUST the partitioner.

That's it roughly.

---

### Post by CatKiller on 2006-10-24
> **JMO707 said:**
> I solve that issue reinstalling CatKiller. Now, I would want to add that free space to the /dev/hda5 partition. Is there any way of do that without using a newer version of gparted?

Not as I understand it, directly anyway. I've never been burned by GParted as TiredBird has, but the versions I've used weren't very old, and I haven't done that many operations with them.

TiredBird's method is sound if you don't want to move the start of the partition. Lengthy, but sound. Personally, if I didn't want to move partitions directly, I'd borrow a spare drive from a friend, copy the data to it using tar, then repartition my drive as I liked, and then copy the data back.

---

### Post by TiredBird on 2006-10-24
Catkiller's idea of borrowing a drive from a friend, copying the data over, etc., is a good one, particularly if you have a friend that has a large external USB drive. To me that is preferable to moving the partitions.

My experiences with GParted are all within the last couple of months. My version of the Live CD is 3.1-1. I don't think it gets any more recent than that. Both of my problems involved moving or extending the low end of a logical partition to a lower point. I won't try it again until I'm satisfied they have fixed the problem. My bug report is on file there and as far as I know they haven't fixed it although I have had some communication with them on it.

---

### Post by TiredBird on 2006-10-24
I just looked up the bug report I filed. It was on 9/29 and the product was GParted 0.3.1. Since that time, several other bugs have been reported regarding resizing or moving partitions. I wouldn't take the chance with data that was important to me.

---

### Post by JMO707 on 2006-10-24
Ok, I was just burning the LiveCD to try, but its not that urgent. Im going to find something =)

---

