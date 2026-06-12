---
title: "Serious memory leakage problems (my disk fills incredibly fast Ubuntu 13.04"
date: 2013-08-11
forum: General Help
---

### Post by Fsirett on 2013-08-11
Last week I had a probem running out of memory so I moved things and doubled the size of my system partition. This week, that is also filled-

I tried to use:

echo 3 > /proc/sys/vm/drop_caches

and I was told I had no permission.

I then went to: 

gksudo nautilus

And looked at the proc file and changed the permissions but that was the same thing.

I think I need to clean the caches and reconfigure the bbackup system that I thought I had stopped last week, but there they are!

I am at a loss as to what to do. I went t:

gksudo nautilus

and changed permission on the /proc file, but I still get denied.

I would try to change the tother permissions but the system does not seem to like me to see them as root- They display on request when I am running normally, but...

Is there any help for me?

Cheers 

Frank Sirett

---

### Post by steeldriver on 2013-08-11
Are you having problems with memory or disk space? they are not the same thing

If your disk is filling up for some reason then the right course of action is to hunt down any unusually large files and see what processes are causing them - most often it's a logfile

---

### Post by Fsirett on 2013-08-11
Cheers! Quite right, I meant disk space.

In case this might help,  Last week, when this forst happened, I was running the system at about  125 Gig, I expanded it to 250 Gig (Yes, I am speaking about Gigabytes  here) and that was filled in a week. I have just added another 100 gig  to the partition but if I do not gt this solved, I shoud have the system  down again by Wednesday. 

I have looked at the files and found a few surprises, at least to me. The biggest files are:

Home  -41.9 Gid    Possibly not that surprising, but I do not know
lost & found 66 Gig    This one strikes me as being out of line completely
media 390 gig    I have no idea what is normal here, but I do have quite a bit  of extra disk space, so I assume that is okay
usr 12Gig     I assume this one is good as wel

My  problem appears to reside in the lost& found folder, but I am not  certain what should be in there! If it is safe to dispose of it, I shall  do so, but I would not mind some advice. 

As an aside, I seem to  remember a few months back getting swamped in the shared folder as  well. I do not remember exactly what I was told to do, but I did it and  the problem seemed to have moved on.

Thanks again for your help

Frank Sirett

> **steeldriver said:**
> Are you having problems with memory or disk space? they are not the same thing

If your disk is filling up for some reason then the right course of action is to hunt down any unusually large files and see what processes are causing them - most often it's a logfile

---

### Post by grahammechanical on 2013-08-11
Please tell us how you found out that you were running out of disk space. It might provide an important clue. Also, are you using Disk Usage Analyser to get those figures? Disk Usage analyser can give results that are confusing to us.

For example, I am running Ubuntu on a 38GB partition without a separate /home partition. Disk Usage Analyser says that the root folder ( / ) is 9.8GB and it is 100.0% used. The root folder can vary insize and it is only as big as it needs to be. So, it always has 100% usage. Actually only 22GB of this 38GB partition is used.

Regards.

---

### Post by Fsirett on 2013-08-11
Cheers! 

I am afraid the machine warned me about low memory and then refused to load the graphics. 

I then booted from a live disk and looked at the properties for the disks as a first step and found it came out with a sum total of zero free space ( again! The same thing happened last week) 

I used the properties window to see just what I really had in the files. Disk usage Analyser is very nice, but I find it is just a little confusing for any real detail in my experience

Another indication is when I try to save some of my libre office files and they refuse to save due to "lack of space."

The disk with the system on it is a 500 Gig drive. It is nroken up into two partitions. The main one that I have me system on is now 324.7 Gig and the other partition , that I do believe was created when I loaded the system is 132 Gig. It calls itself a "Linux Swap."

I do know I have a lot on my machine, but I try to move as much as possible onto other disks and try to keep my system disk area near free of storage of stored information.

Your system makes me think I have a rather large problem or that I am going to have to do some very major reconfiguration! 

I do know when I opened a poorly thought out backup a few months ago it overloaded my target file  the system decided it would store in my system partition and that certainly had a go at the memory. There could be legacy configuration problems

Frank Sirett

---

### Post by oldos2er on 2013-08-11
A 132GB swap partition? Can you run these commands in a terminal and copy/paste the output here? ```
sudo fdisk -l

df -h
```

---

### Post by Fsirett on 2013-08-11
From the fdisk command I come up with :

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a5d56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       929878016  1953523711   511822848   83  Linux
/dev/sda2   *     3719168   929878015   463079424   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c24f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   471621631   235809792   83  Linux
/dev/sdc2       471623678   488396799     8386561    5  Extended
/dev/sdc5       471623680   488396799     8386560   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084724

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   276879359   138438656   82  Linux swap / Solaris
/dev/sdd2       276881406   976771071   349944833    5  Extended
/dev/sdd3       976771072   976773119        1024   82  Linux swap / Solaris
/dev/sdd5       957364224   959995903     1315840   83  Linux
/dev/sdd6       959997952   976771071     8386560   82  Linux swap / Solaris
/dev/sdd7       276881408   957362175   340240384   83  Linux

Partition table entries are not in disk order

Disk /dev/sdj: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a183

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1            2048   976707583   488352768    7  HPFS/NTFS/exFAT
Note: sector size is 1024 (not 512)

Disk /dev/sdi: 3986 MB, 3986546688 bytes
256 heads, 63 sectors/track, 241 cylinders, total 3893112 sectors
Units = sectors of 1 * 1024 = 1024 bytes
Sector size (logical/physical): 1024 bytes / 1024 bytes
I/O size (minimum/optimal): 1024 bytes / 1024 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   ?  4294967295  4294967293  4294967295   ff  BBT
/dev/sdi2   ?  4294967295  4294967293  4294967295   ff  BBT
/dev/sdi3   ?  4294967295  4294967293  4294967295   ff  BBT
/dev/sdi4   ?  4294967295  4294967293  4294967295   ff  BBT


From the df -h I get :

df: &#8216;/root/.gvfs&#8217;: Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd7       320G  242G   62G  80% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            4.0G   12K  4.0G   1% /dev
tmpfs           810M  1.1M  808M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            4.0G  632K  4.0G   1% /run/shm
none            100M   48K  100M   1% /run/user
/dev/sdj1       466G   43G  424G  10% /media/frank/My Passport
/dev/sda2       435G  380G   34G  92% /media/frank/One
/dev/sda1       481G  454G  2.1G 100% /media/frank/Two
/dev/sdb1       459G  315G  121G  73% /media/frank/500g
/dev/sdc1       222G   17G  194G   8% /media/frank/200


I am sorry, but I do not know how to encapsulate the readout, so the post is quite long. 

I know what you mean about the swap, but it seems to me that I just let the original install just have what it asked for. 

To be honest, when I first put Ubuntu on someone told me I would be fine with fifty gig for the entire system so I sort of doubled that just to be certain. I have not been paying too much attention to tweaking the OS as work piles in hot and heavy. Hence all my disk space, and even with all that, I have to spend quite a time cleaning that up so as not to run out-

Rhanks again for your trouble. I have few problems with Ubuntu, and you guys really spoil me. I can always find or get answers. With Windows things were a touch different.I have a large stack of old ide drives laying around that I used to use to rescue me when Windows went south. It was just easier to take a disk drive with a faulty OS to be repaired and put in an alternate to keep n working until the problem was (not often) traced to source-

Cheers

Frank Sirett

P S I notice before the end of the first block there is a mesage that looks a touch odd to me. I am not certain what it means. However, just to let you know I am not a complete idiot (or to remove all doubt) I thought I might mention I saw it.

F S

---

### Post by oldos2er on 2013-08-11
Is the message you're talking about "This doesn't look like a partition table
Probably you selected the wrong device." I don't think I've seen that one before, but if /dev/sdi is a removable device I wouldn't worry about it too much.

You have four swap partitions, looks like /dev/sdd1 is the huge one. You really only need one, which can be shared between all Linux distros.

This is just my opinion, so take it for what it's worth: You've got plenty of disk space, but it could be organized a bit better. Have you considered putting /home on its own partition? I find it's very convenient to keep my personal files in /home/user separate from /. Naturally you'd need to backup any data you want to save before creating/destroying/moving partitions. Just a thought.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Fsirett on 2013-08-11
Cheers! I am afraid my disks are more a matter of add as I need or. more likely, add as old ones die. I used to have a lot of 80 gig drives but rhey did not last. 

I suspect the best thing to do would be to put everything in backup somewhere and completely reinstall with some structure to it, but that would be logical and time consuming.

Do you think it is the home folder that is eating the memory and causing me the problems? That makes sense and I just happen to have been given a new 1Terra drive that I can install and do it. very easily. 

Out of curiosity, well actually much more, what can I remove from the sytem that is safe to call /home? I am afraid I have only one Ubuntu distro loaded, but more, ever so much more in the system. 

My problem here is that I use the standard setup and  let it all have its way and I am not certain what I can cut out and put into another partition without causing problems. I have some five or six books on Ubuntu but I do not have the time to actually study them. Always my problem. I am criticised for being too thorough when I read. I can't let even the punctuation secape me without a goof think. I love James Joyce but I read him like a glacier. Non fiction is much worse. I cannot flip to the end and see who did it so on fiction catches me out trying to figure out why the button on my system is in another place when the book is five years and three releases old. I want that to ne funny, but it is actually true! Does that make me geek or anti-geek?

Frank Sirett

---

### Post by oldos2er on 2013-08-11
> **Fsirett said:**
> Cheers! I am afraid my disks are more a matter of add as I need or. more likely, add as old ones die. I used to have a lot of 80 gig drives but rhey did not last. 

I suspect the best thing to do would be to put everything in backup somewhere and completely reinstall with some structure to it, but that would be logical and time consuming.

Do you think it is the home folder that is eating the memory and causing me the problems? That makes sense and I just happen to have been given a new 1Terra drive that I can install and do it. very easily.  Hard disk space, not memory. :)  If you set your 1TB drive as one large /home partition, you wouldn't need to worry about running out of space for quite awhile. 

> **Fsirett said:**
> Out of curiosity, well actually much more, what can I remove from the sytem that is safe to call /home? Sorry, I don't understand the question.  

> **Fsirett said:**
> My problem here is that I use the standard setup and  let it all have its way and I am not certain what I can cut out and put into another partition without causing problems.

I was thinking more in terms of doing a clean manual install and setting your partitions up something like 25GB for root, 1TB for /home, 2GB swap (assuming this is a desktop system with 4 or more GB RAM) for example. There's no need to change any of your other data disks or partitions.

---

### Post by Fsirett on 2013-08-12
Duplicate removed

---

### Post by Fsirett on 2013-08-12
I seem to have sent the original reply to parts unknown. 

Now let me recap so I am certain I understand correctly. 

I think I have been labouring under the illusion that the /home file contained actual programmes; that is to say that it was an integral part of the  operating system. Do not ask me how I got that into my head, if I am wrong.

Assuming that is not the case, all I really need to do is to move the /home file into a new disk, wipe teh disk that is left and reinstall Ubuntu completely on new partitions that are more reasonable, thereby giving me what I had before but with lots of extra space? 

That does sound good to mem upgrades between major versions are sometimes fraught with problems. I solve them, but I think many times that I might be patching a crack rather than solving something that needs solving. I think it is due to my being a refugee from Windows that makes me ddelay. My old Windows reinstalls took all day to get back up and running again. As I remembr the installation process with Ubuntu I might lose an hour or maybe two if I have quite a few extras. 

What I could do do (if this is the correct way), is backup my root file by the recommendations of one of the backup programmes I am about to download, move all of my files and partitions about as suggested and then ask it to restore. 

Can I do this from a live disk or am I better off simply formatting, partitioning and going in completely new install. In that case I had best note all of my programmes so I can reinstall all of those later. In that case, are there any files from the /rooy that I might want to preserve and merge or replace after. I can think of one or two, but I am not certain that is a good idea. Since some of the coftware came from outside Canonical, it would probably make it easier. 

I should, in factm know all this and be prepared all of the yime, but there you have it. In a world of instant gratification, useful knowledge becomes a commodity we think we can do without.

Cheers

Frank Sirett

---

### Post by oldos2er on 2013-08-12
Most programs install to /usr/bin. Configuration files for programs are stored in both your home folder (mostly as hidden files and folders) and /etc. See [this]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for more info on linux file system hierarchy. It is quite a bit different than Windows.

> Assuming that is not the case, all I really need to do is to move the  /home file into a new disk, wipe teh disk that is left and reinstall  Ubuntu completely on new partitions that are more reasonable, thereby  giving me what I had before but with lots of extra space? That would the goal, yes. The link I posted in #8 will give you info on the best way to do it. Obviously it's not something you need to rush into. And yes, backup anything you've changed that you want to keep.

An easy way to make a list of packages you've installed is to use Synaptic Package Manager's 'Save Markings' and 'Read Markings'.

---

### Post by Fsirett on 2013-08-12
Cheers! That should do the trick!

I will follow your sage advice and move with some caution and thought (this time...for once!.) I am going to take a good lok at everything and try to get it a little tight this time and not break the whole thing. Not n keeping with my usual methods, but all leaves must turn at some time or another

Cheers! I really appreciate it!

Frank Sirett

---

