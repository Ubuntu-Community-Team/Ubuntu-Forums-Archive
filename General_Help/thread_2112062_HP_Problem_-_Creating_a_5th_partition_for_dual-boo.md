---
title: "HP Problem - Creating a 5th partition for dual-booting"
date: 2013-02-03
forum: General Help
---

### Post by JorgeNevada on 2013-02-03
Hello everyone.

I have been using ubuntu installed on windows for a couple of months now. Since it is not an ideal situation, I am just about ready to make a proper instalation with a partition just for ubuntu, on top of windows 7.

The thing is, I have a HP laptop, and it already comes with 4 partitions for its operations, and I dont feel confortable messing with those since I really dont know what would happen.

If I try to create a fith partition, the disk manager prompts me to make the disk dynamic, otherwise it wont go further; it seems that the maximum number of basic partitions is four. Since ubuntu wont install on dynamic disks, I am really out of ideas of how to proceed.

Since I am no computer genious and am new to this kind of problems, I was hoping for a simple, straightforward solution that doesn't involve me doing risky things that I don't understand that might compromise the behavior of my PC.

Any thoughts?

---

### Post by Mark Phelps on 2013-02-03
Sorry, there is no straight-forward solution as the limit you're up against is standard for MBR-formatted systems.  There is no way around it that will work with Linux.  You would have to remove a partition to make way for another -- which is not what you want to do.

---

### Post by Impavidus on 2013-02-03
You will have to mess with partitions.

You can either delete one of the primary partitions, which will remove all of its contents, possibly resize some other partitions (all using the windows tools) and finally use the ubuntu live disk to create an extended partition in the unallocated space, with the ubuntu root and swap (and possibly home) partitions.

Or you can change one of the primary partitions into a logical partition within an extended partition. I forgot the name of the tool that can do this (it has been mentioned several times on these fora), but you need at least one unallocated sector between the to be converted partition and the one before that. Don't convert the windows system partition to logical, that may kill windows. When you have done so, you can shrink the logical partition to get free space and use the ubuntu live disk to create logical linux partitions.

---

### Post by mcduck on 2013-02-03
If use the HP program that came with your machine to create a recovery disc, you can then safely remove the recovery partition form the machine. And after that you'l be able to resize the existing partitions and create logical partitions where you can install Ubuntu.

THe HP tools partition is actually safe to remove as well, but that will stop some of the extra tools that your laptop has from working. If it makes sense or not depends if you are actually using those tools or not.

Either way, you'll have to delete one or both of these partitions to be able to dual boot. And no, doing so will not mess with any normal use of your computer.

---

### Post by JorgeNevada on 2013-02-03
> **Mark Phelps said:**
> Sorry, there is no straight-forward solution as the limit you're up against is standard for MBR-formatted systems.  There is no way around it that will work with Linux.  You would have to remove a partition to make way for another -- which is not what you want to do.

Well, if that is the case (it is unbelievably annoying that HP makes their system like this...), I am up to other solutions.

Here is the list of my partitions:

C: -> main partition where I have all my files.
HP_TOOLS -> i supposed this one is responsible to control all the HP tools and programs.
Recovery (D:) -> probably shouldn't mess with this one?
SYSTEM -> i think this one is responsible for booting windows

Which one would you suppress, and how do I do it.

EDIT: Is there any downside on making the C partition logical?

---

### Post by Mark Phelps on 2013-02-03
> **JorgeNevada said:**
> Well, if that is the case (it is unbelievably annoying that HP makes their system like this...), I am up to other solutions.
Other OEM vendors generally do the same -- use up all four partitions on the drive.

> Here is the list of my partitions:

C: -> main partition where I have all my files.
HP_TOOLS -> i supposed this one is responsible to control all the HP tools and programs.
Recovery (D:) -> probably shouldn't mess with this one?
SYSTEM -> i think this one is responsible for booting windows

Which one would you suppress, and how do I do it.
I said earlier there is no straighforward solution because any solution will be a lot of work ... but if you want do it anyway, I would recommend the following:
1) Download and install the FREE version of Macrium Reflect on your HP.
2) Use MR to perform an image backup of your Windows partitions (boot and OS) to an external drive
3) Use the MR Option to create and burn an Linux Boot CD
4) Boot from the Linux Boot CD, with the external drive connected, and see that you can see the backups when using the Restore option -- but do NOT perform the actual restore.
5) Now, you can remove the Recovery partition -- as you no longer need it since you have a way to restore your PC.

---

### Post by JorgeNevada on 2013-02-03
@Mark Phelps

It is funny that while browsing the internet on this problem I ran into a forum where you participated on this very issue :D

[http://www.sevenforums.com/general-discussion/164884-adding-5th-partition.html](http://www.sevenforums.com/general-discussion/164884-adding-5th-partition.html)

---

### Post by JorgeNevada on 2013-02-03
> **Mark Phelps said:**
> Other OEM vendors generally do the same -- use up all four partitions on the drive.


I said earlier there is no straighforward solution because any solution will be a lot of work ... but if you want do it anyway, I would recommend the following:
1) Download and install the FREE version of Macrium Reflect on your HP.
2) Use MR to perform an image backup of your Windows partitions (boot and OS) to an external drive
3) Use the MR Option to create and burn an Linux Boot CD
4) Boot from the Linux Boot CD, with the external drive connected, and see that you can see the backups when using the Restore option -- but do NOT perform the actual restore.
5) Now, you can remove the Recovery partition -- as you no longer need it since you have a way to restore your PC.

Thank you for the step-by-step guide, I think I am able to follow it.

But just for curiosity sake, would you recommend me keeping the On-windows install type, instead of going through all this trouble? Or go with any other type of installation?

---

### Post by Mark Phelps on 2013-02-04
> **JorgeNevada said:**
> But just for curiosity sake, would you recommend me keeping the On-windows install type, instead of going through all this trouble? Or go with any other type of installation?

If by "on-Windows install type", you mean that you installed from INSIDE Windows using Wubi, that was not designed to be used for the long run and often, does not survive version updates well.

You CAN migrate a Wubi install to an actual Linux partition, but it's a lot of work and you would really do better to do the following:
1) Uninstall Ubuntu from Windows (like any other app)
2) Use the Win7 Disk Management utility to shrink Windows down -- but leave at least 20% free space.
3) Do the MR install, imaging, and boot CD creation I recommended.
4) Confirm that you can boot from the CD and find the restore image.

THEN, remove the Recovery partition.

Now you should have a lot more free space to use for Ubuntu.

---

### Post by oldfred on 2013-02-04
I think all the previous posts have covered what you have to do. But if you want confirmation from other sources. And whatever you do, do not let Windows convert to dynamic partitions as that will not work with Linux.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by SeijiSensei on 2013-02-04
Having suffered through this problem once before, let me add that the way HP orders partitions on its drives makes it very difficult to allocate enough space for Ubuntu.  The Windows partition is usually third, and usually consumes 90% or more of the drive.  You really cannot resolve this problem without imaging the Windows partition first.

See [http://ubuntuforums.org/showthread.php?p=11299287#post11299287](http://ubuntuforums.org/showthread.php?p=11299287#post11299287) for the steps I used.  This was with a brand-new machine, though, so I had no compunction about recreating the Windows installation from scratch.

I don't generally engage in conspiracy theorizing, but this practice seems almost intentionally designed to make it very difficult to add another operating system to a Windows machine. Nothing prevents the manufacturer from using a more friendly partitioning scheme with one small primary and one large extended.

---

