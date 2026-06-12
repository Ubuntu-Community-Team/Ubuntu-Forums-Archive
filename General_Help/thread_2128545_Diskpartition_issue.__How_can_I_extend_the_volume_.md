---
title: "Disk/partition issue.  How can I extend the volume where Linux is?"
date: 2013-03-23
forum: General Help
---

### Post by pretty_whistle on 2013-03-23
Here's a screenshot of the problem:

[IMG]http://i49.tinypic.com/2gw6vki.png[/IMG]

See all that free space?  I want to extend the volume where Linux is sitting so that the free space is part of it but there are 2 partitions in the way, one is "extended" and the other is "swap".  What is the easiest way to do this??

Just an FYI on how it got this way:
I made a disk image of everthing on an older laptop who HDD is 160GB in size.  I restored that image to this bigger HDD (500GB in size) so for some reason it has made that extra space "unallocated".

---

### Post by oldfred on 2013-03-23
Maybe 4 choices?
You can probably expand extended partition to include all the unallocated, then move swap all the way to the end of the drive inside the extended and then shrink extended? That then moves unallocated before extended.

You can just delete swap (& extended) and recreate at end of drive. You will have to manually edit fstab with new UUID of swap. You probably can still boot but it will complain about a partition not found as the old UUID is no more.

You can create a new partition and move /home into it.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


You can just create a new partition in the unallocated. I would first expand extended partition so new partition is inside the extended. That gives a bit more flexiblity in the future as you can only have one extended which can hold many logicals.
With the new partition you mount it as /mnt/data and can link all the folders inside it back into /home so it looks like it is part of your install. A bit more advanced as you have to edit fstab to add partition and set ownership & permissions to use it.

---

### Post by pretty_whistle on 2013-03-23
[IMG]http://i49.tinypic.com/29ksyhj.png[/IMG]

Now here's what it looks like.  I used Clonezilla and told it to ignore the partitions on the image I restored.

My question now is:
It shows there are 2 partitions of 5.9GB each, one labeled "Extended" and the other labeled "Unknown".  There is no "swap".  So, is it ok to not have "swap" or should I make the "Unknown" one swap??  Is swap really necessary?

---

### Post by pretty_whistle on 2013-03-23
Oh, my bad.  The "Unknown" labeled partition is already swap it just doesnt have a name so it labeled it "Unknown".  Haha.

---

### Post by pretty_whistle on 2013-03-23
So, using Clonezilla as I did worked.  And I didnt even have to do anything else.  Cool.

I'll mark thread as solved then.

:D

---

### Post by Slim Odds on 2013-03-23
Just an FYI. If you're system really does use swap, it's best to have that partition at the beginning of the disk instead of the end.

If you machine does use swap much, then it really doesn't make much difference.

---

### Post by pretty_whistle on 2013-03-23
I have, or may have, a new problem.  Take a look at this message its giving me:

[IMG]http://i48.tinypic.com/2ep7w9s.png[/IMG]

What does that mean?

---

### Post by oldfred on 2013-03-23
If you have a new 4K drive or SSD, then partition alignment is important. Normally gparted now aligns on correct boundries. Not sure how you created new partition.
If you have an older drive it really does not matter.

If you have encrypted /home then partition tools do not see swap.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you have lots of RAM you probably can live without swap. I have 4GB of RAM and almost never use swap. But it is better to have at least some swap.

---

### Post by pretty_whistle on 2013-03-23
> **oldfred said:**
> If you have a new 4K drive or SSD, then partition alignment is important. Normally gparted now aligns on correct boundries. Not sure how you created new partition.
If you have an older drive it really does not matter.

If you have encrypted /home then partition tools do not see swap.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you have lots of RAM you probably can live without swap. I have 4GB of RAM and almost never use swap. But it is better to have at least some swap.

I too have 4 GB of ram.  I wonder if I can just delete it.....

Anyone know?

---

### Post by pretty_whistle on 2013-03-23
Can anyone tell me what that warning message means in post 7 above?  It's the one that says the partition is misaligned.
???????

---

### Post by Slim Odds on 2013-03-23
> **pretty_whistle said:**
> Can anyone tell me what that warning message means in post 7 above?  It's the one that says the partition is misaligned.
???????
It means that your partition does not start in the right place. You can probably fix this with gparted.

---

