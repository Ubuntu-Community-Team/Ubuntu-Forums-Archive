---
title: "Is there a special way I have to set up target hard drive to use Clonezilla?"
date: 2019-07-16
forum: General Help
---

### Post by dora5 on 2019-07-16
I used Clonezilla five years ago to do exactly what I am doing now, and never had a problem.  Suddenly I can't get it to work, and from the discussions, neither can anyone else.  There are complaints about it everywhere.

Maybe there is something simple I am doing wrong that noone has thought of.  I tried enough different methods!

First I used an ordinary SATA hard drive in a USB enclosure, which uses USB3.   The USB3 plug definitely works properly.  I've used it to boot Ubuntu Live and to back up files.   I formatted the drive, formatted it as Ubuntu Disk's idea of general use, created a partition, and formatted it as FAT.   When I created the partition, I named the volume SystemBack.   The name displays as SystemBac.

I got to selecting the drive to put my backup image on, and where the name of the partition should have been I got <abort> exit directory browsing.

I tried with a different hard drive.  Same thing.

Most people have reported this problem with USB, but I also tried it with a SATA connection.

I took the hard drive out of the USB enclosure, and connected it to a SATA connector on the motherboard, and did the whole thing all over again, following the same procedure, name, exactly.

Same error.

It said that if there were spaces in the name it would not display. There are no spaces in the name, and I applied the same name five times. I didn't put in a space by mistake.  

However, Clonezilla seemed to want to keep going.  It seemed to see the partition, just called it -.   It clearly saw it.  It went ahead and let me select the partitions to back up, and created a backup image.   Took a long time, went through it's stuff.  Seemed to conclude normally.

Then I took out my system drive and put in a new drive, and tried to restore it.   It got to the point where it needed to see teh partition, and saw teh image and consistently referred to it by name.   I selected the drive to restore it to.

Then it crashed saying "no input found".   ????!!!!    Obviously there was input, it told me the input's name!

I imagine it's failing to see something important.

The only other clue is that references to the drive describe it as "dirty" among other things, and that was true of both drives. They aren't both dirty.  Whatever dirty means. Both drives were wiped by me where I work, so there is nothing on them, dirty or otherwise, and it's highly unlikely they'd have the same dirt on them to start with.

It's not my hard drives, and it's not my hardware.   

Was I supposed to create a partition?

How was I supposed to format it?

How was I supposed to format the drive?

The instructions do say FAT for general use, NTFS for Windows, and I'm backing up an Ubuntu system.   

Are there rules you've not told anybody about about how to name the volume besides not to use spaces?   Maximum number of characters?  No spaces? Clonezilla requires Chinese encoding?

I'm not doing ANYTHING in command line inside of Clonezilla.   I only want to know if something obvious like formatting method or volume name is causing only some people to run into this issue.   The errors I got and described are the error information I'm going to have.  I don't have the skill level, and I don't have the time.   Mind, I know the people at Ubuntu didn't cause this problem, but you really need to change your expectations about how much time people should be expected to spend solving a problem.   Expecting people to spend more time to get Clonezilla to work than it would take to set up their entire system all over again is plain stupid.   Fixing their programming is Clonezilla's job.    


Thanks!

Dora Smith

---

### Post by dora5 on 2019-07-17
Answer was stupid but on Clonezillas part, not mine.  Watched 10 you tube videos before someone dropped the missing detail.  And noone on any forum ever thought of it.  

Instructions say that for instance if you intend to back up onto sde1 than sde1 appears in the choice screen and you pick it.   It does not.   You have two options.  If you pick the option that seems to say abort it's not here, it picks / and lets ypu go on.  In reality my images were created last trial but something else went wrong on restore.

The other option is,  you were supposed to have put actual directories on the partition, and you're supposed to pick one!   It's completely not intuitive and not in any readable version of the instructions.

It gets more confusing on restoring.  I picked the directory where I knew it was and it told me to either go bsck up a level or abort because its not there.   I picked abort and no to trying again and it picked / and went on.

The real reason it probably crashe is I didn't use diskpart which was used to do the backup, evidently thst causes a no input error.  I got farther second time but I was supposed to put partitions on the drive,  and it doesnt tell you THAT nowhere, either!   Always before partitions just copied with everything else!

What a pack of idiots wrote this version.

---

### Post by mastablasta on 2019-07-17
what is the current file format you are using on the drives?

---

### Post by dora5 on 2019-07-17
Was fat now ntfs

---

### Post by mastablasta on 2019-07-17
NTFS should be Ok and then backup to .iso or whatever image file they use? the Ubuntu or any other linux filesystem is contained wihtin image anyway. 

[https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)

fat will not be good, because it has a size limit as well as some other limits. volume name shouldn't matter. in dos it was 12 characters. having it short might help. 

if you are having issue with current version there should be older ones also available. as i understand their images use debian testing, so ... well sometimes things are not working so well in there. :-)

---

### Post by GhX6GZMB on 2019-07-17
You don't mention how big your drives are, but did you notice this limitation:

[LIST]
[*]The destination partition must be equal or larger than the source one.
[/LIST]

---

### Post by dora5 on 2019-07-17
Yes, I did notice that the destination drives have to be atleast as large - but I also explained what the problem was, and that wasn't it.

I am fairly good at Ubuntu and don't need a picture book.   You don't point me to a picture book for Clonezilla, but, do you think they'd communicate what we're actually supposed to do if they used pictures?   Honest, I doubt it would help.  The creators of Clonezilla are quite simply idiots who can't think in a straight line.   

I didn't actually end up able to restore my files, specifically because, according to Clonezilla, now, it can only restore partitions backed up on sd5 and sd6, on destination drives named sd5 and sd6.   

That's enough for me, the creators of Clonezilla have completely lost their minds.

Even supposing sa5 and sa6 would have worked, I don't have control over what numbers the system gives my partitions, and there is no way I could ever reproduce the way the installation software set up the partitions on my system drive!   Somehow it created a partition 2 that got split into partitions 5 and 6, and that isn't anything I did, I straightforwardly created my partitions.   

Researching if I actually am forced to use this stupid piece of sh..., I learned no, I can simply use gparted to copy my partitions.  All of them.  And I don't need to fiddle with partitioning and formatting some esoteric way to get it to work.   

I checked with my boss to see if that is true, explaining that I can't get Clonezilla to work, and he said Clonezilla "can be confusing".  I said, I think Clonezilla was deliberately designed to be confusing, because it repeatedly tells people to do things that are completely different from what they actually have to do!   He agreed with both parts of that.   

He said Clonezilla isn't confusing once you learn it, but my psychic powers clearly aren't up to the task.   I'm sure that somebody SHOWED him how to use it, as there is no other possible way anyone would ever figure out how to use it.  

If Ubuntu people don't want to hear that Clonezilla was created by idiots who can't think in a straight line, you really need to drop this software from your repository.

---

### Post by uRock on 2019-07-17
> **dora5 said:**
> ......Snip....

Even supposing sa5 and sa6 would have worked, I don't have control over what numbers the system gives my partitions, and there is no way I could ever reproduce the way the installation software set up the partitions on my system drive!   Somehow it created a partition 2 that got split into partitions 5 and 6, and that isn't anything I did, I straightforwardly created my partitions.  

....snip....

This can be done by creating smaller partitions on the new drive, then deleting them. I've never used Clonezilla, so can't say much for their software.

I prefer using Gparted or DD to move files when replacing a drive.

---

### Post by mastablasta on 2019-07-18
> **dora5 said:**
> 
If Ubuntu people don't want to hear that Clonezilla was created by idiots who can't think in a straight line, you really need to drop this software from your repository.

i always thought clonezilla is to be used as a separate distro. so you boot into live session and have all drives unmounted , so you can manipulate them.

agree with the ridiculous interface. also you make one mistake and have to go back form beginning (no next, back buttons). that is why i was so hopeful about redo backup, but unfortunately, they stopped developing it. it was quite perfect, just needed some update (kernel and apps), and maybe a disk to disk clone feature added. but that't was it. wish someone would pick up the development and do it properly. i am sure people would be willing to test it. Ubuntu would also benefit from a good backup/rescue disk.

---

