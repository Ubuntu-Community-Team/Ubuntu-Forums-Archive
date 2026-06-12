---
title: "[SOLVED] Primary Partition exceeded"
date: 2007-10-10
forum: General Help
---

### Post by jpittack on 2007-10-10
I have four primary partitions.  One ubuntu, one vista, one dell utility, one dell recovery.  I have been told to not remove the dell, because the computer will not boot then.  I have already allocated 4 gigs of space to use for important files like homework and pictures that I want both vista and ubuntu to access.  When using gparted, I get the message that I can not set up a primary partition, I have exceeded my limit. Vista comes up with an error as well.  Is there a such thing as a secondary partition that I could use?

---

### Post by AgentZ86 on 2007-10-10
I think the limit is 4 primary partitions.

You need to divide a partition and setup a logical partition or extended partition.

I had the same problem with multiboot machines. I had 6 or 7 partitions all booting different linux types, and one partition for my windows xp. But only 2 or 3 primary partition and I think I had a logical partition with several extended partitions within the logical partition. Or something like that it's been a while.


Anyhow that was also my problem at first.
I hope this helps that should be the problem I think the limit is 4 primary partions.



> **jpittack said:**
> I have four primary partitions.  One ubuntu, one vista, one dell utility, one dell recovery.  I have been told to not remove the dell, because the computer will not boot then.  I have already allocated 4 gigs of space to use for important files like homework and pictures that I want both vista and ubuntu to access.  When using gparted, I get the message that I can not set up a primary partition, I have exceeded my limit. Vista comes up with an error as well.  Is there a such thing as a secondary partition that I could use?

---

### Post by jpittack on 2007-10-10
I can't find a way to set up a logical parition.  Could you explain how you think you went about fixing this.  All I can find in gparted is new partition, which is for a primary.

---

### Post by dptxp on 2007-10-10
Delete at least the last partition.
Any new partitions you make from now, make logical/extended or whatever,
but not primary.

---

### Post by jpittack on 2007-10-10
I have been told to not delete the last partition, a dell partition.  This is supposed to prevent me from booting my machine.  I believe the guy.  Can I make a partition logical/extended without removing the last partition?

---

### Post by jpittack on 2007-10-10
Here is the order of everything as it appears in gparted.

sda1/  Dell utility
sda2/  vista
unallocated space
sda4/  ubuntu
sda3/  dell restore

---

### Post by AgentZ86 on 2007-10-10
> **jpittack said:**
> I have been told to not delete the last partition, a dell partition.  This is supposed to prevent me from booting my machine.  I believe the guy.  Can I make a partition logical/extended without removing the last partition?

You may be right about that? 

I'll research this again and check my notes

---

### Post by dptxp on 2007-10-10
> **jpittack said:**
> Here is the order of everything as it appears in gparted.

sda1/  Dell utility
sda2/  vista
unallocated space
sda4/  ubuntu
sda3/  dell restore

How much unallocated space after Vista ? You can add it to Ubuntu space, resize partitions again.

---

### Post by AgentZ86 on 2007-10-10
Right, I think he has to resize the Ubuntu partition and make it contain the unallocated space.

Then you can select the create logical or extended partitions from there.

Basically creating a logical or extended prartition within the Ubuntu Primary parition. Just FYI

Also I noticed you have not swap partition, that probably slows things down a bit ?

No matter, anyhow I think that should do it

---

### Post by jpittack on 2007-10-10
I'm not following how to do this.  When I right click on ubuntu, I do not have the resize/move option.  It is grayed out.

If you can give me step by step, I would appreciate it.  I have always used vista to create my partitions.

I have the 2GB of RAM, which are fast modules.  I thought that because ubuntu is a light OS that I would not exceed the 2GB and thus would never have my system using swap space.  I wouldn't say that anything is slowed down.  Everything is much faster than vista:).  Please tell me if my swap would be utilized at all.  It would be a good idea to set it up now since I am messing with partitions.

---

### Post by AgentZ86 on 2007-10-10
Ok I'll do this on a machine I have running and post the how to,

In the mean time, post what type of space you wish for this partition ???

Please post your partition configuration again with partition sizes.

And what is the new extra partition going to be used for ??? or what file system ?

Please advise I'll boot up and old computer I have in the corner and get this done so I can instruct you further on it.

---

### Post by AgentZ86 on 2007-10-10
Ok I see the problem, sorry about that I had to refresh my memory on this.

The max is 4 primary so you already have the max.

First I'll deal with the partition problem, then the problem of trying to keep your stuff in the same working order it is in now.

But don't proceed until you have read and addressed the working order part first. As I've listed below

The only way to fix this is to delete one partition,

When creating a new partition you must create an extended partition.
And be sure to use the full unallocated space for the extended partition.
Then you will see another unallocated space which is the same size now as the extended partition. 
So now you will make new logical partition whatever size you wish and as many as you wish. There is some limit on logical drives also but I think it's like 10 or 20 or something I can't recall off hand.
And you will select you file type, Fat32,NTFS,ext2,ext3 etc etc.

Then apply changes.

(FYI extended partition is a primary partition also, so you cannot create more then 4 primary or 4 extended partitions for that matter.) 

I don't know which partition you care to use for your new extended and logical partition, but it would seem simpler to me to if you use the Dell utility Partition for that.

**Working order part:**
As far as restoring the system to the same working order, I would suggest 
that before you delete any partition, that you create  a disk image of the partition you plan to delete.
I would do that with the Dell Utility Partition, I don't know if the Dell Utility is a bootable partition or not but I think it's just data that can be backed up to another partition.

I'll get on dell tech support chat and ask them tommorow.

Summery:
Create Disk Image, or Copy Partition/Drive (Dell Utility Partition)
Delete a Primary Partition (Dell Utility Partition)
Create Extended Partition (full unallocated space)
Create Logical Partitions(you select sizes and file type) (for Dell Utility Partition create same file type)
Format and apply,
Copy Disk Image, or Copy Parition to one of the new Logical Partition.

You may have to fool with the grub menu to be sure that the boot location is stated correctly in the grub boot file, I'll post more on that too.

I'll post back exactly how to create/copy the partition in my next post
And perhaps some info on the boot file to get it to give you the 

Anyhow that is the deal thus far.

**Also NOTE:**
When resizing you must select New size in the New size field or the resize button will be grey (inactive)
And you can only resize partitions, not the unallocated space
:guitar:

---

### Post by jpittack on 2007-10-10
dell restore
vista
space
ubuntu
dell utility

FAT32 so vista and ubuntu can read and write.

I want a partition of important files, mabye even my home folder, so that I can break, fix, tweak and massage Ubuntu until I get supercomputer results:).

I will check and see what dell says and try to make a cd backup tonight.  A heads up.  Tomorrow I have a test in calc and will be at school all day studying.  I can take a break every now and then to get this set up but we won't really be able to do something in a fast and orderly manner:(.  If it helps I am in a central time zone.  So my time I am free (yet studying) from 12:30 to around 5 with class at 5:30.

Thanks so much for all of the help.  I have been wanting to do this for so long.  If its not too much trouble, maybe I should set up a swap?

---

### Post by jpittack on 2007-10-10
Great news.  Utility partition is not needed for booting.  It contains the image of the os and dell uses it when I send in my computer for service.  They strong recommend that I do not delete the partition.  Blah! But getting rid of it does not void my warranty.  WOOT!  It seems to contain lots of important sounding files. They are all mainly in .mdm format.  I think as long as I don't destroy my BIOS I am good to go.

I have destroyed my BIOS while attempting to flash it.  The files never seem to respond when I try to update the BIOS.  Then the program stops responding and I just tried to run it again.  System shuts down, never turns on.  Dell gets a call.  I learn a lesson.

Lets continue with our endeavour.  Thanks a billion!

---

### Post by jpittack on 2007-10-11
I forgot to give you the sizes

Dell Restore about 70 mb
Vista about 76gb
space is 4 gb
ubuntu about 27 gb
Dell utility is about 4 gb

back up complete!

---

### Post by vanadium on 2007-10-11
If you are running gparted from within Ubuntu, then it is normal that you cannot do anything with the partition because it is used.

Before I can give more concise suggestions, I need more precise information. Please post the output here of the command

sudo fdisk -l

I can already tell in general that any drive can have only up to four primary partitions. The trick to have more partitions is to have an extended partition, that in turn can hold several logical partitions.

---

### Post by AgentZ86 on 2007-10-11
> **jpittack said:**
> I forgot to give you the sizes

Dell Restore about 70 mb
Vista about 76gb
space is 4 gb
ubuntu about 27 gb
Dell utility is about 4 gb

back up complete!

Ok, so Gparted will work no problem.

The easiest thing would be to make a disk image of that 4GB partition the Dell Utility partition, either with hard drive copy utility or possibly the copy feature in Gparted, I'll confirm and post instruction on this today sometime.

Then as described below, delete the Dell utility partition, and create extended partition.
Then you could I guess resize the larger Vista partition to a bit smaller size if you want to utilize more space for you new extended partition.Or resize one of the other partition.
Or I guess leave it alone as you will end up with a 8GB extended partition if thats enough space, however you need a logical partition of at least 4GB in order to restore the Dell Utility Data, So that leave you only 4GB for your extra partition you want to create. Anyhow Just FYI if you have not considered that.
You will now have more unallocated space, then resize the new extended partition to make it larger if desired,
Then create logical partitions as desired and described in my last post.

This would probably be simpler if you had another old 5GB or 6GB drive laying around to save the partiion or drive copy files to. But I think we can span some CD's or DVD's or something for that also I'll post back on that also.

I'll post back again once I confirm how to make/copy the disk partition for you.

And this should do it, also I'll play with resizing the existing partitions to confirms that this won't create any problems with the OS and post back today sometime.

Anyhow I think your on the right track now.
:)

---

### Post by jpittack on 2007-10-11
I am using a laptop that I can hook up to an external hard drive.  Sadly, I think it is NTFS format.  I can get all of the files from the utility partition because it doesn't use more than 70mb of space of that 4 gb.

---

### Post by AgentZ86 on 2007-10-11
> **jpittack said:**
> I am using a laptop that I can hook up to an external hard drive.  Sadly, I think it is NTFS format.  I can get all of the files from the utility partition because it doesn't use more than 70mb of space of that 4 gb.


I would copy the 4Gig Partition to the External Hard Drive or to a CD, or even to a Zip drive since it's only 70MB of stuff.

But before you do that, let me research a bit to understand the copy partition commands on Gparted to be sure you don't overwrite the existing partition.

NTFS format should make no difference since your 4GB utility partition is probably NTFS also.

I'll have to research the copy partition topic a bit, but I'll post that back in a few.

WDdiag will work great for this also, I'll post a link to the correct file.

Also do you  have a floppy drive in your laptop ???

---

### Post by AgentZ86 on 2007-10-11
Ok, here is what I've found.

The condition that exists is that you have 4 primary partition, and unallocated space outside of those partitions.

Using Gparted at least, I cannot seem to combine the unallocated space after deleting a primary parition.

Basically what I've done was to hook up my extra drive and create a similar partition on the external drive which is similar to the one I want to copy from the other main drive.

Then copied the partition in question, then changed devices and pasted the partition into the extra drive partition I just created, I then deleted the primary partition.

That went ok, but the unallocated space did not combine, I now have 2 unallocated spaces.

Which means you basically have to delete all partitions, except the Vista Partition.

Then all the unallocated space will be reclaimed completely.
But before doing that you will have to create additional partitions on your external hard drive similar or matching the main drive partitions.

Then 
Copy the main partitions and paste to the external partitions you created
Do this one at a time, then delete all the partition except Vista.

Then re-create the partition exactly like they were, with the exception of the 4th partition, that one has to be an extended partition,using whatever unallocated space that is left, and then logical partitions of your desired size.

I've not figured out any other way to reclaim the unallocated space outside of the 4 partition Using the Gparted methods.
Once that 4th partition was created any unallocated space seems to be untouchable unless you delete all the partitions except one, then re-create them as needed.

Sorry I could not be of more help, I will try some more to see if there is a way to reclaim that space some other way.

**_I would not do anything until you get that part figured out._**

I may have just had to reboot the machine after deleting the partition could be as simple as that, I'll try that too, but anyhow I'll post back with more info

I would like to know about this topic also it's very interesting.

And probably can help a lot of people.

:)

---

### Post by jpittack on 2007-10-11
I could use vista to put that unallocated space back into vista.  I have the option of extending the space of vista.

---

### Post by AgentZ86 on 2007-10-11
Ok,

I've retested doing this with Gparted

It appears it may have been a fluke, Gparted allowed me to reclaim the unallocated space pretty much anyway I desired, I don't know why it didn't work properly the first time around, perhaps I just needed to restart and have Gparted scan the drives again.

Anyhow I think this will work.

Copy the existing partition (Dell Utility) to an external drive partition I would setup a 4GB partition on the external drive for this, unless you have things on that drive that can't be backed up or critical.

Then delete the Dell Utility partition and this should reclaim the unallocated space, you should now have 3) paritions and unallocated space.

Then create extended partition and use the full unallocated space
Then create a 4GB logical partition, then create another logical partition of your desired size/sizes and so on.

Then copy the external hard drive partition to the the new 4GB logical partition you just created

And that should do it, hit apply and you should be good.

Thats initially what I though should happen but when I tried it for some reason the machine was giving me extra unallocated partitions for some reason.

Thats should do it.

And once you get to this point you should be able to resize them anyway you want them.
:guitar:

---

### Post by jpittack on 2007-10-11
Much thanks be to you.  I will try this fix tonight and post back with the results.  I am considering writing a how to for dell owners, who will always run into my same problem.

---

### Post by AgentZ86 on 2007-10-12
> **jpittack said:**
> Much thanks be to you.  I will try this fix tonight and post back with the results.  I am considering writing a how to for dell owners, who will always run into my same problem.

Yep, your right, and others as well, I actually have a new dell desktop as well, and basically from new I deleted all the partitions and re-installed everything since that was easier then installing all the trial ware they put on there LOL

Anyhow post back the results, should work fine.

---

### Post by jpittack on 2007-10-12
Worked like a charm!  Happy dual boot with swap.  Now if i could just fix my graphics driver...

---

### Post by jpittack on 2007-10-12
Tell me what desktop you bought.  I am eager to find out.

---

### Post by AgentZ86 on 2007-10-12
> **jpittack said:**
> Tell me what desktop you bought.  I am eager to find out.

I have a few machines, but the one is the Dell Dimension B110

And Glad to hear it's working nicely now.

What kind of video card, try the restricted drivers ?

---

### Post by jpittack on 2007-10-13
I am trying to use the latest driver from ati.  The restricted drivers work fine, but thats the problem.  I want them to work great.  I have an IGP in my laptop, a radeon xpress 1150.  some where around 700 fps on gears.

---

### Post by AgentZ86 on 2007-10-13
> **jpittack said:**
> I am trying to use the latest driver from ati.  The restricted drivers work fine, but thats the problem.  I want them to work great.  I have an IGP in my laptop, a radeon xpress 1150.  some where around 700 fps on gears.

Probably should open a new thread on this topic and post it here so I can subscribe.

And other might be able to help.

---

### Post by jpittack on 2007-10-14
Here is the link. [http://ubuntuforums.org/showthread.php?p=3532675#post3532675]("http://ubuntuforums.org/showthread.php?p=3532675#post3532675")

I am going to tell you though.  This is a massive amount of questions.  You have been such a huge help with me already, mabye its time you took a break and passed the torch to someone else.  Thanks again man.  Could not have done this without you.

---

### Post by AgentZ86 on 2007-10-16
> **jpittack said:**
> Here is the link. [http://ubuntuforums.org/showthread.php?p=3532675#post3532675]("http://ubuntuforums.org/showthread.php?p=3532675#post3532675")

I am going to tell you though.  This is a massive amount of questions.  You have been such a huge help with me already, mabye its time you took a break and passed the torch to someone else.  Thanks again man.  Could not have done this without you.

LOL, thanks
:)

---

