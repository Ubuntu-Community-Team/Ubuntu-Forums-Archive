---
title: "Partition issues"
date: 2007-03-25
forum: General Help
---

### Post by profXavier on 2007-03-25
Ok, ill try to make a long store short.  I have used smartctl to check over one of my partitions, with the output being [here]("http://paste.ubuntu-nl.org/11967/"). So what happenes is I have a 300GB ATA HD I was using to backup.  It was an NTFS, i recently moved to ubuntu from windows, and so I decided to switch over to ext3, which also caused the same issue, and now I have just made it a reiser file system.  What I am finding is that my system freezes, so I can do nothing except reboot it (reset button).  So here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=64926d5f-1db6-4d4d-b259-eda464b4962c /               reiserfs notail          0       1
# /dev/sda6
UUID=83dea69d-a5c3-40ea-9c13-a40f7656835b /home           reiserfs defaults        0       2
# /dev/hda5
/dev/hda5 /mnt/hda5     reiserfs    defaults            0       1
# /dev/sda5
UUID=6fe926b6-0a6c-4c47-818c-b42d8c8b37e1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Now, as you can see, I am concerned about /dev/hda5, in this issue. I have both a /mnt/hda5 and a /media/hda5, which is odd of course.  I did have it ONLY in /media/hda5, but recently I tried to just move it to /mnt to try something different. The sizes of each are different as well, the /mnt/hda5 is the entire size of the HD, which it should be, where as the /media/hda5 is only appro. 10GB.


I have attempted to move smaller files, most was about 20-30GB, of about 2-3GB and I have had success (about 2 or 3 times), and I am sure this file system supports file sizes even larger than that.  When I first removed data off of the NTFS partition, i copied it to my reiser and some of the copies were 100GB+.

So with that said, I am just looking for questions about needing more information from me, or suggestions for me to try.  I have been working on this situation over the past 3 days, so whats a few more right?

---

### Post by SuSUntu on 2007-03-25
I found a fellow who posted a very, very similar output as you have posted, and he said he was getting system "lockups" as well, though the specific file transfer / copy symptoms that you have described were not  mentioned.

The link below is his story as told on LinuxQuestions.org:

[http://www.linuxquestions.org/questions/showthread.php?t=480669](http://www.linuxquestions.org/questions/showthread.php?t=480669)

Bottom line: after switching HDDs and trying a few hdparm commands, his **problem was ultimately fixed by replacing the PSU**. 

Sorry I couldn't be of more help.

---

### Post by profXavier on 2007-03-26
Well, 

I really do want to test on different hardware, but I do not have another HD that I could use.  As for the PS, I guess I could go out an buy one, but my issue doesnt appear to be the same as the link you gave.  I have found I have a pretty stable system, so I dont agree with changing the power supply at this time.  Since I am new to Ubuntu, maybe in time I will have enough knowledge to find a solution.  

But in the meantime, if anyone else has some suggests, I would be more than happy to hear them.

---

