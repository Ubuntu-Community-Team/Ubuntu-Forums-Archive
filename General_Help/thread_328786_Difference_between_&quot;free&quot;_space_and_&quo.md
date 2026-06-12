---
title: "Difference between &quot;free&quot; space and &quot;available&quot; space for all EXT3 partitions"
date: 2006-12-31
forum: General Help
---

### Post by Nintendud on 2006-12-31
Last night, I noticed something odd was happening to one of my EXT3 partitions; every hour, it lost approximately 1 gig of space. I only had one application, Azureus, writing to the drive at the time, but the space was already allocated, so my free disk space should not have been decreasing.

This morning, I opened up gnome-system-monitor to check out my HD usage, and I was treated to something odd... there were two columns describing the free space on the drive; "free" and "available". I decided to go straight to the command "df -h" for help, and look at the output for my EXT3 drives:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              20G   12G  6.9G  64% /
/dev/hda3             206G  165G   30G  85% /downloads
/dev/hdd1             276G  250G   12G  96% /phantom

As you can see, the difference between the "size" and "used" columns is not the same as the "available" column. My ReiserFS and Windows NTFS drives were not affected.

I am quite alarmed, since I have lost about 13+ gigs on one hard drive to this mystery. If anyone has any ideas for why this is happening, please respond to this thread! I've already tried remounting some of the non-root drives, and it didn't help anything.

I am currently using Ubuntu Dapper Drake [I haven't upgraded yet].

---

### Post by Stabicron on 2006-12-31
Maybe and I am probably wrong on this but I think Azureus caches data to the same location as the Jar files for the program itself in addition to the allocating done in the spot where you want the stuff to go. If thats the case it could be really easy to see whats going on. However that program is supposed to free up that cache as soon as the download is completed and seeding begins, if Azureus has a bug and it is not for some reason this could be a real problem and I would suggest looking around for your Azureus stuff and checking file sizes. Thats my guess anyways.

---

### Post by Nintendud on 2006-12-31
That would be an impossibility, since cached data would appear under the amount of data used. Also, my Azureus directory is /home/nintendud/.Azureus/azureusbin, so it would only affect the root partition, which suffered the least damage.

However, thanks for trying to help. :)

---

### Post by Nintendud on 2006-12-31
I forgot to mention something terribly important: I ceased losing space once the extremely large 50 gig torrent finished. However, as I mentioned before, the space was allocated ahead of time, and the folder never exceeded the amount allocated. Also, there were no cache folders on the drive. I cannot help but think the two events are linked. The torrent contained numerous 20 meg files, and was downloading at around 400-900KB/s.

In any case, this does not explain the same behavior on my other partitions, especially my root partition which lost a little bit, that do not have files downloaded via Azureus on them.

Please try and help me. I want my space back! :(

---

### Post by Magnes on 2006-12-31
Well, I run df -h to test, and here are some results (from some of my ext3 partitions):

size used avail
30G  5,4G   23G 
58G   31G   25G 
30G   16G   15G 
8,7G  5,9G  2,4G 

As you see it looks familiar (funny ist the third one 16+15 > 30). Maybe it's because of large number of files and the size of journaling file?

---

### Post by smoker on 2006-12-31
just a suggestion, have you emptied the wastebasket recently, i'm not sure if the space from files deleted is made available, until maybe it is emptied.

---

### Post by Nintendud on 2006-12-31
I do not have any wastebaskets full, since I delete files directly without a wastebasket (I'm running XFCE4, not Gnome). Also, that would not explain the difference between my used space, total space, and free space.

As for Magnes, that is odd. Maybe this only happens with EXT3? As for the journaling file, I don't know... anyone have any idea if journaling can take up over 13 gigs in about 7 hours? That seems a bit harsh to me. Also, ReiserFS has journaling, and its totals are fine.

Thanks for trying to help though.

---

### Post by Nintendud on 2006-12-31
I'm exhausting some things with a few Linux friends online, and we just looked up the size of the journal on /phantom (/dev/hdd1), the filesystem that lost over 13 gigs of available space. As root, I performed "debugfs -R "stat <8>" /dev/hdd1". Here is the output:

Inode: 8   Type: regular    Mode:  0600   Flags: 0x0   Generation: 0
User:     0   Group:     0   Size: 134217728
File ACL: 0    Directory ACL: 0
Links: 1   Blockcount: 262416
Fragment:  Address: 0    Number: 0    Size: 0
ctime: 0x44bbfc14 -- Mon Jul 17 17:07:32 2006
atime: 0x00000000 -- Wed Dec 31 19:00:00 1969
mtime: 0x44bbfc14 -- Mon Jul 17 17:07:32 2006
BLOCKS:
(0-11):538-549, (IND):550, (12-1035):551-1574, (DIND):1575, (IND):1576, (1036-2059):1577-2600, (IND):2601, (2060-3083):2602-3625, (IND):3626, (3084-4107):3627-4650, (IND):4651, (4108-5131):4652-5675, (IND):5676, (5132-6155):5677-6700, (IND):6701, (6156-7179):6702-7725, (IND):7726, (7180-8203):7727-8750, (IND):8751, (8204-9227):8752-9775, (IND):9776, (9228-10251):9777-10800, (IND):10801, (10252-11275):10802-11825, (IND):11826, (11276-12299):11827-12850, (IND):12851, (12300-13323):12852-13875, (IND):13876, (13324-14347):13877-14900, (IND):14901, (14348-15371):14902-15925, (IND):15926, (15372-16395):15927-16950, (IND):16951, (16396-17419):16952-17975, (IND):17976, (17420-18443):17977-19000, (IND):19001, (18444-19467):19002-20025, (IND):20026, (19468-20491):20027-21050, (IND):21051, (20492-21515):21052-22075, (IND):22076, (21516-22539):22077-23100, (IND):23101, (22540-23563):23102-24125, (IND):24126, (23564-24587):24127-25150, (IND):25151, (24588-25611):25152-26175, (IND):26176, (25612-26635):26177-27200, (IND):27201, (26636-27659):27202-28225, (IND):28226, (27660-28683):28227-29250, (IND):29251, (28684-29707):29252-30275, (IND):30276, (29708-30731):30277-31300, (IND):31301, (30732-31755):31302-32325, (IND):32326, (31756-32196):32327-32767, (32197-32768):33301-33872
TOTAL: 32802

We're currently under the impression that the journal is 134 megs (It says "Size: 134217728"), but we are not 100% certain on what the output is measured in. If this is true, we still don't know where my 13 gigs went! :(

Thanks for reading. Hopefully someone has an answer for me soon! Also, I have rebooted, so the space is not being taken up by any application that has deleted files loaded.

---

### Post by Nintendud on 2006-12-31
My problem is still around...

I'm extremely confused as to why this is happening.
If you have any idea, or know of a forum where people might know, please tell me.

---

### Post by dcstar on 2006-12-31
> **Nintendud said:**
> My problem is still around...

I'm extremely confused as to why this is happening.
If you have any idea, or know of a forum where people might know, please tell me.

I'd suggest you just accept that df isn't providing the answer you are looking for, install the **baobab** package and look at it's output (Applications-Accessories-Disk Usage Analyzer) - I have just done that and while the "Size" and "Used" numbers are reported the same as with df, the "Available" with baobab is much larger (in other words, it adds up correctly).

It seems that df is just making its calculations differently (or incorrectly), so you are probably not "losing" any disk space whatsoever.

---

### Post by vigleik on 2006-12-31
Apparently, with the default way of making an ext3 filesystem, something like 5% of the space is reserved for root, in case you run out of space or something like that. That might be unnecessary, and can be avoided if you format the partition with the right options (I'm not sure how to format a partition manually in the first place, but Google is your friend). Google for "ext3 overhead" to learn more. There seems to be another active thread about the same issue on the forum:

[http://www.ubuntuforums.org/showthread.php?t=215177](http://www.ubuntuforums.org/showthread.php?t=215177)

Another way to learn about this is to read the manual. "man mkfs.ext3", in particular the part about the "-m" option.

---

### Post by dcstar on 2006-12-31
> **vigleik said:**
> Apparently, with the default way of making an ext3 filesystem, something like 5% of the space is reserved for root, in case you run out of space or something like that. That might be unnecessary, and can be avoided if you format the partition with the right options (I'm not sure how to format a partition manually in the first place, but Google is your friend). Google for "ext3 overhead" to learn more. There seems to be another active thread about the same issue on the forum:

[http://www.ubuntuforums.org/showthread.php?t=215177](http://www.ubuntuforums.org/showthread.php?t=215177)

Another way to learn about this is to read the manual. "man mkfs.ext3", in particular the part about the "-m" option.

Yep, apparently the "Available" reported by df is the space available for non-root users, not the total free space on the FS.

---

### Post by Nintendud on 2006-12-31
The thing is, my file manager, Thunar, reports the same thing df reports, and I wanted to know if that is really true. I'm a little afraid to transcend what it says, because... well.. what if it's true?

Anyway, you have introduced me to a fantastic tool that I have never used before. This will make it so much easier to find out where my hard drive space is going... thanks!

I guess maybe I should see what other file managers report? This is still kindof alarming.

---

### Post by Nintendud on 2006-12-31
If the root space was reserved when I formatted, then why was I randomly losing space yesterday? I was losing space (1+ gig every hour), and nothing was being written to the disk except data from the torrent, but the space needed for that was allocated long ago and its directory never increased in size. However, the available space ceased decreasing when the torrent finished, but the directory never increased in size.

This space did not disappear when I formatted... it just began disappearing out of nowhere. So, that doesn't make any sense :(

EDIT: Sorry for double posting, I didn't see all three responses...

EDIT2: As for the link, he is reporting losing data from his TOTAL amount of data available. I am losing data from available data to write to.

EDIT3: Also, as you can see, his EXT3 values add up. His available space and used space equal his total space. This still makes no sense. :(

---

### Post by Dread Knight on 2006-12-31
I lost too 13 gb using the latest version of Azureus on **Windows XP SP2 Pro**.

I was trying to download about 200 mb from a 13 gb torrent... and Azureus cached it all, so i switched to another application.

As for Linux (ubuntu), Opera works pretty well... but i will try uTorrent soon... (the windows version is very nice).

---

### Post by Nintendud on 2006-12-31
Dread Knight, in my case, there is **no extra information stored on the hard drive**. I have 250 gigs on that drive. Nothing more, nothing less. Azureus did not cache anything there at all. I have a total of **276 gigs** available to nonroot users. However, I only have a reported **12 gigs** free. This can't be right, but at the same time, I don't know how to prove that it's wrong. It seems that my free space up and vanished. **The same thing happened on partitions that did not have anything downloaded with Azureus on it**. And, oddly enough, all of these partitions are EXT3.

I need to know where the space went on my partitions, or why my applications are reporting the wrong amount of free space. Baobab doesn't help me in that regard, but it does confirm that 250 gigs are in use on the main drive in question, /phantom. Also, I have no directories owned by root on this drive, except for lost+found, which is empty.

I am still confused, and I thank you all for your concerns, but I still have no idea where my space went.

EDIT: Baobab does report a total free space amount which is more than what df says, but I still want to know why df and all my other programs say I have less space.

---

### Post by Nintendud on 2007-01-01
So, am I safe to exceed the free space amount output by df? Is it something that can easily be measured wrong like that?

:(

---

### Post by Nintendud on 2007-01-01
*Bump*

I certainly hope "bump"ing is allowed... my problem still exists. :(

---

### Post by pmreimer on 2007-02-03
I am having the same problem, azureus is likely the culprit also.  I am missing only 1.9 gigs right now.  I have noticed when I delete a torrent that is still in use by azureus, it's not actually deleted, it's turned into "free space" but available isn't changed.  This means that azureus is doing something with it, I just can't figure out what.  Now I have nothing active in azureus, but i've apparently deleted something WHILE azureus was using it.  I ran into this problem before and due to other reasons, I installed ubuntu on a different drive.  This solved the problem, just the wrong way.  I will try uninstalling/reinstalling azureus, to see if that does anything, but short of that I'm clueless.  (It is not 5% reserved for super user)

---

### Post by BBSeXoDuS on 2007-02-04
Anyone found anything more about this problem? I'm missing 7GB and I also think Azureus is the one carrying with the guilt. I once remember deleting a torrent FROM azureus to free some space, to immediatly after notice that df reported no more free space available, although the file wasn't in the filesystem at all! It would seem that Java is doing something wrong allocating disk space, I don't think Azureus is there to blame, but the Java platform we use to run it. What Java version are you guys using?

Regards,
Xavier.

---

### Post by pmreimer on 2007-02-05
I'm running java 1.5.0-08ubuntu package, if that helps.  Would uninstalling/reinstalling java do anything?

---

### Post by Matthai on 2008-03-04
You can release this reserved space with:

  sudo tune2fs -m 0 /dev/device

---

### Post by LeDechaine on 2008-03-24
He's right :P

> **"man tune2fs"] -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208 said:**
> 

I've just found this thread after seeing that my **free** space was 443,1mb and my **available** space was 204,7mb on my 4.6gb partition.

By looking at "**df**", my partition is exactly 4806904kb.

**Rough math:**
4806904 / 1024 (mb) = 4694,2mb (*Entire drive size*)
4694,2 x 5% = 234,71mb (*The 5% for privileged processes*)
443,1 - 234,7 = 208,4mb (*Disk space remaining* according to this)
Available space: 204,7mb (*Disk space remaining* according to the **System Monitor**)

**So, for your drives/partitions:**
[QUOTE=Nintendud;1951173]
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              20G   12G  6.9G  64% /
/dev/hda3             206G  165G   30G  85% /downloads
/dev/hdd1             276G  250G   12G  96% /phantom

**Rough maths again:**
*hda2:*
20 - 12 = 8gb ("**Free**" space)
8 - 6,9 = 1,1gb (The **5%**)
20 x 5% = 1gb (***5%**, confirmed*)
*hda3:*
206 - 165 = 41 ("**Free**" space)
41 - 30 = 11gb (The **5%**)
206 x 5% = 10,3gb (***5%**, confirmed*)
*hdd1:*
276-250 = 26 ("**Free**" space)
26 - 12 = 14gb (The **5%**)
276 x 5% = 13,8gb (***5%**, confirmed*)

The default of 5% causes you to lose a **lot** of space.
I do not recommend setting this to zero, because this *seems* useful (according to **man tune2fs**), and above all quite practical to me if, for example, you full your entire drive/partition. Believe me, I can confirm that this causes weird system behavior, and you don't want that :P

*So what i'd recommend myself is to change the percentage to 1:*

[B]sudo tune2fs -m 1 /dev/hda2
sudo tune2fs -m 1 /dev/hda3
sudo tune2fs -m 1 /dev/hdd1[/B]

*Or, better: leave this alone if you don't mind. ;)*

Hope it helps. :)

---

### Post by rexxxlo on 2008-04-05
i just noticed the wine takes 3.6 gigs of space on my drive....

i was locking around and i noticed that too then in system monitor it  gives you the virtual memory that everything uses, when i reorganized by that column wine was on top 

my free and avaliable space isnt matching just yet but i see tis too 

just a comment dont know if it will help but i figured i would add my observations to the post

---

