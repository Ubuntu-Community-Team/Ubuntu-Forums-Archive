---
title: "How can I shrink my Windows partition?"
date: 2007-06-27
forum: General Help
---

### Post by speaker219 on 2007-06-27
I installed Ubuntu and still kept Windows intact with a fairly large partition.
Is there any way I can shrink the Windows partition to get more space for my Ubuntu partition? Any help would be appreciated, thanks.:p

---

### Post by LaRoza on 2007-06-27
Several ways, I recommend using GParted Live, see my sig.

It is very easy to use.

Just shrink it, and resize the other partition. But Back up any essential data, just in case.

---

### Post by bigken on 2007-06-27
and defrag windows a  couple of times 1st

---

### Post by r76 on 2007-06-27
I'd second that, it's a great tool, especially on the LiveCD.  Defragment your windows partition first.

---

### Post by Canis familiaris on 2007-06-27
Use GParted in Ubuntu Live CD and shrink your Win Partition.

---

### Post by speaker219 on 2007-06-27
Thanks for all the input! I'm reconsidering and i'm starting to think I might as well take the big jump and have my computer with solely Ubuntu on it. (aka dumping windows :P)

---

### Post by Canis familiaris on 2007-06-27
> **speaker219 said:**
> Thanks for all the input! I'm reconsidering and i'm starting to think I might as well take the big jump and have my computer with solely Ubuntu on it. (aka dumping windows :P)
Sure! :p

However I suggest if you do that use Dapper. Feisty has some particularly annoying problems.

---

### Post by stchman on 2007-06-27
> **speaker219 said:**
> I installed Ubuntu and still kept Windows intact with a fairly large partition.
Is there any way I can shrink the Windows partition to get more space for my Ubuntu partition? Any help would be appreciated, thanks.:p

First thing to do is to run a chkdsk /f and then a defrag.


Once that is done boot up the Ubuntu Live CD and fire up Gnome Partition Editor.  I would go to System--->Preferences--->Removable devices and uncheck the automount feature.

You can then select the Windows NTFS partition (typically hda1) and then select resize.  You can then drag the slider to the left and then click apply.  This will shrink the Windows partiton.

After that you can make a new partition from what is now unallocated.

Fairly simple.

---

### Post by speaker219 on 2007-06-27
> **Anurag_panda said:**
> Sure! :p

However I suggest if you do that use Dapper. Feisty has some particularly annoying problems.
I haven't had any problems in Feisty and i've tried Dapper - major problems. it might be laptop-specific, but i'm sticking to feisty ...

---

### Post by vexorian on 2007-06-27
You can do it safely using windows' own tools to partition the disk. Control Panel¬Administration tools¬disks

---

### Post by stchman on 2007-06-27
> **vexorian said:**
> You can do it safely using windows' own tools to partition the disk. Control Panel¬Administration tools¬disks

Windows XP does not have that ability.  Windows Vista does have the shrink and expand in its disc manager.

---

### Post by Canis familiaris on 2007-06-27
> **speaker219 said:**
> I haven't had any problems in Feisty and i've tried Dapper - major problems. it might be laptop-specific, but i'm sticking to feisty ...
Sorry for going out of topic here, but have you ever tried running a VCD in Feisty? If you did successfully, tell me how you did it?

---

### Post by vexorian on 2007-06-27
> **stchman said:**
> Windows XP does not have that ability.  Windows Vista does have the shrink and expand in its disc manager.
As a person that shrinked his HD to install Ubuntu using windows I must disagree? Unless my memory is failing horribly in that case sorry.

> Sorry for going out of topic here, but have you ever tried running a VCD in Feisty?

Rather off-topic but you just try to open it in totem, ubuntu might tell you that you need restricted codecs then you download and install them.

But I just use VLC media player (available on repos) and it has not given me a single problem, although I am not a multimedia oriented user I must say

---

### Post by Canis familiaris on 2007-06-27
> **vexorian said:**
> 
Rather off-topic but you just try to open it in totem, ubuntu might tell you that you need restricted codecs then you download and install them.

But I just use VLC media player (available on repos) and it has not given me a single problem, although I am not a multimedia oriented user I must say
You were able to mount the VCDs? How? It never automounts in mine?

---

### Post by stchman on 2007-06-28
> **vexorian said:**
> As a person that shrinked his HD to install Ubuntu using windows I must disagree? Unless my memory is failing horribly in that case sorry.



Rather off-topic but you just try to open it in totem, ubuntu might tell you that you need restricted codecs then you download and install them.

But I just use VLC media player (available on repos) and it has not given me a single problem, although I am not a multimedia oriented user I must say

I said Vista disc manager has the ability to shrink existing NTFS partitions.  XP can create and delete partitons, not modify them.

---

### Post by vexorian on 2007-06-28
hmm I am not ready yet to call Vista "windows" but either way perhaps I just used it to delete one partition and move the rest to another, pretty odd I do think I used it to resize a partition, sorry.

---

### Post by stchman on 2007-06-28
> **vexorian said:**
> hmm I am not ready yet to call Vista "windows" but either way perhaps I just used it to delete one partition and move the rest to another, pretty odd I do think I used it to resize a partition, sorry.

If there is a way to resize partitions using XP disc manager please let me know.  My girlfriend bought a laptop with Vista and it has "Shrink" and "Expand" in it's disc manager.  It is one of the few things I do like about Vista.

---

### Post by betes on 2007-11-08
> **stchman said:**
> First thing to do is to run a chkdsk /f and then a defrag.


Once that is done boot up the Ubuntu Live CD and fire up Gnome Partition Editor.  I would go to System--->Preferences--->Removable devices and uncheck the automount feature.

You can then select the Windows NTFS partition (typically hda1) and then select resize.  You can then drag the slider to the left and then click apply.  This will shrink the Windows partiton.

After that you can make a new partition from what is now unallocated.

Fairly simple.

I have the same question as the OP.  I understand these instructions, but I have another question.  How does the new partition that is created from the unallocated space get used by Ubuntu?  Is there a way to increase the size of the ubuntu partition (without reinstalling) or is it just as functional to have another partition with linux file system?

---

### Post by betes on 2007-11-10
> **betes said:**
> I have the same question as the OP.  I understand these instructions, but I have another question.  How does the new partition that is created from the unallocated space get used by Ubuntu?  Is there a way to increase the size of the ubuntu partition (without reinstalling) or is it just as functional to have another partition with linux file system?

So the solution to this questions is on many other threads, but I thought I'd answer my own question here in case some one with this question stumbles onto this thread first (as I did).  Gparted does allow you to move the starting point of a partition forward into unallocated space.  I just defraged the windows partition, booted to the live cd, opened Gparted, resized the windows partition (shrinking it) and expanded the linux ext3 partition into the newly created space.  It took gparted a long time to move the linux partition over (almost 2 hours), but everything worked fine and now I have a much bigger linux partition.

Again, theres more detailed info about this elsewhere with more clear instructions from folks who know a lot more than me, but just wanted to leave this here for whoever might find it.

---

