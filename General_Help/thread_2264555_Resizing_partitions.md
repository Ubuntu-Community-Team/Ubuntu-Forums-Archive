---
title: "Resizing partitions"
date: 2015-02-08
forum: General Help
---

### Post by KayeNg on 2015-02-08
Hi guys.  Although there's no mention of Linux or Ubuntu in this question, your answers would greatly assist me in partitioning my hard disk in preparation for my Lubuntu installation.

[COLOR=#000000][FONT=Helvetica Neue]If my laptop is running Windows 7, the partitions on the hard disk would look like this on a GUI of a partitioning program: [/FONT][/COLOR]
(From left to right on the graph)
[COLOR=#000000][FONT=Helvetica Neue]1st partition = System Reserved (NTFS) [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]2nd partition = drive C: (NTFS) [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]3rd partition (made by me, for storing data) = drive D: [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Question 1. If I already have MANY files stored on D:, and I resize drive C: to make it smaller, thus making drive D: even bigger, would that cause any loss of data or corruption on either drive? (I repeat, drive D: already has much files stored in it)[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Question 2. Vice Versa. Make drive D: smaller so that drive C: becomes bigger, would it cause corruption on either drives? [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue](I repeat, drive D: already has much files stored in it)[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]I'm talking about one physical hard disk with two partitions, excluding the "System Reserverd".

Thank you![/FONT][/COLOR]

---

### Post by v3.xx on 2015-02-08
> Question 1. If I already have MANY files stored on D:, and I resize drive C: to make it smaller, thus making drive D: even bigger, would that cause any loss of data or corruption on either drive? (I repeat, drive D: already has much files stored in it)
There is always a chance of corruption when editing partitions.  Better to have backup.

---

### Post by Bucky Ball on 2015-02-08
1. If you shrink drive C, drive D won't get bigger unless you make it bigger. Shrinking C will leave free, or unallocated, space between C and D.
2. See 1.

Resizing a partition has no effect on the partitions next to it. They stay the same size.

Use the Windows disk management software to shrink the Windows partition, NOT Gparted from the Ubuntu install media. Backup any valuable media before commencing your adventure. Good luck. ;)

PS: Defragment the Windows drives, or any other NTFS drives you want to resize, a couple of times before resizing and then check how much space the data takes up. Win spews info all over the partition so you need to put it all together again to get back available space on the partition.

Also, if you are not booting in UEFI (check in the BIOS), you may be limited to four partitions on the drive. In this case, you need to create an extended partition as the fourth drive, which is like a container, and install Ubuntu onto logical drives inside that. For Ubuntu you will need two partitions with the mount points:

/ = where the operating system goes;
/swap = like a Win pages file, 2Gb or the size of your installed RAM if you intend to hibernate.

---

### Post by KayeNg on 2015-02-08
> **Bucky Ball said:**
> 1. If you shrink drive C, drive D won't get bigger unless you make it bigger. Shrinking C will leave free, or unallocated, space between C and D.

That's what I'm trying to say.  Sorry for the confusion. Please see below.  I shrank C, resulting in a 110GB of unallocated space between C and D. 
[ATTACH=CONFIG]259836[/ATTACH]

Then I dragged the left edge of D towards the left, thus deleting the 110GB space in the process, and making D bigger.
[ATTACH=CONFIG]259837[/ATTACH]

So now I'm wondering if I should continue.  I have 130GB of data on D, and I don't want to lose them.
[ATTACH=CONFIG]259838[/ATTACH]

---

### Post by Bucky Ball on 2015-02-08
Where are you intending to install Lubuntu? You need a solid plan prior to resizing partitions, so please share. Can't really say whether to proceed without knowing exactly what outcome you're looking for. ;)

---

### Post by KayeNg on 2015-02-09
> **Bucky Ball said:**
> Where are you intending to install Lubuntu? You need a solid plan prior to resizing partitions, so please share. Can't really say whether to proceed without knowing exactly what outcome you're looking for. ;)

My question and screen shots are just hypothetical.  I'm a newbie but I've created dual boot systems quite a few times already so don't worry about it. I appreciate your concern :popcorn:

So, given the screen shots, any chance my data in drive D: would be corrupted or deleted by either increasing D: (thereby decreasing C) or decreasing D: (thereby increasing C) ?

If the data in D: would not be affected, I have a few more questions:

1.  I have 2 desktop computers.  When I'm running Windows OS and using a third party partitioning program, why is it that on the graph, one has a partition for "System Reserved", and the other does not? Like so:
       Computer 1:    
        | System Reserved | Windows |

       Computer 2:
        | Windows |

2.  Does the graph reflect the actual disk? What I mean is, based on my screenshots, is Windows actually in the "front" or "first" part of the disk? Is there such a thing? Dumb question, I know.

3.  Would there be a difference in performance depending on how I place my Lubuntu OS, "/home" partition, and swap partition? For example, what's the difference between:
      
      | Windows | Shared data by both OS | Lubuntu | /home | Swap |    
          
           and
      
      | Windows | Shared data by both OS | Swap | Lubuntu | /home |

    Is there even a recommended order? Like Lubuntu first, then /home, then swap on the right-most side?

4.  I was hoping to have my "Shared data by both OS" partition to be the "/home" in my Lubuntu.  Unfortunately it's not possible because "/home" must be ext format, and if it is ext format, then I cannot access that partition when I'm on Windows.  Therefore I've no choice but to make "/home" NTFS or FAT32 format.

5.  With regards to number 4, if I am forced to make my "Shared data by both OS" partition an NTFS or FAT32 partition, that means I would probably use the ext-formatted "/home" partition to only store settings of GUIs, among other insignificant things, correct?  If so, how big a partition should I make for "/home"?

That's it for now. I hope you can answer the questions one by one. Thanks a lot!!!

---

### Post by Mark Phelps on 2015-02-09
> any chance my data in drive D: would be corruptedYou were already told that there is ALWAYS a chance of data corruption.  IF you're looking for guarantees, you won't get them here.

> 1. I have 2 desktop computers. You haven't told us which apps they are -- so we are left guessing completely in the dark -- which is a waste of time.  Different apps use different code; no one knows why they show different results.

> 2. Does the graph reflect the actual disk? Yes

> 3. Would there be a difference in performanceIn your example, no. But ... there is a limit of 4 upper-level partitions on an MBR-formatted disk -- and your example shows five.  You would need to create a single Extended partition and then create all your Linux filesystem partitions inside that.

> 4. Therefore I've no choice but to make "/home"NO -- do NOT do that!  Home needs to be a Linux filesystem; do NOT share it with Windows.

> 5. With regards to number 4, iA data partition shared with Windows should be NTFS, and NOT be Home. Your actual /home partition in Linux does not need to be very big, in fact, you don't really need a separate /home partition at all.

---

### Post by Bucky Ball on 2015-02-09
If you would give us a plan as to what you intend your final partition layout to be, we may be able to help you. As it is, we are in the dark, as Mark Phelps has mentioned. We can't really recommend or confirm one thing or the other.

---

### Post by KayeNg on 2015-02-09
> **Mark Phelps said:**
> You were already told that there is ALWAYS a chance of data corruption.  IF you're looking for guarantees, you won't get them here.
.....but in theory everything should be fine, right?

> **Mark Phelps said:**
> You haven't told us which apps they are -- so we are left guessing completely in the dark -- which is a waste of time.  Different apps use different code; no one knows why they show different results.
.....I actually used the same app, it's called Aomei Partition Assistant; same version too.  Same app, same version, used in two desktop computers.  One showed a separate partition which is "System Reserved", the other does not.  And I believe it's the same Windows Seven version too.  Anyway, it's not all that important.

> **Mark Phelps said:**
> NO -- do NOT do that!  Home needs to be a Linux filesystem; do NOT share it with Windows.
Sorry, I typed incorrectly. I know Home needs to be a Linux filesystem. I was going to say that I have no choice but to make "/home" ext format, and therefore cannot share it with Windows. Sorry for the confusion.

> **Mark Phelps said:**
> A data partition shared with Windows should be NTFS, and NOT be Home. Your actual /home partition in Linux does not need to be very big, in fact, you don't really need a separate /home partition at all.
Yes, I've tried NOT making a separate /home partition, but I'm just curious as to why a lot of people recommend a separate partition for /home.  They say it's for preserving settings, besides my personal data.  But I won't be saving my data on /home, I would save my data on the NTFS partition which is shared with Windows.  That leaves using /home partition for preserving settings only, like GUIs for instance, correct me if I'm wrong.  If that's the case, how big should the /home be? And is it even worth it?  Again, I'm just wondering why so many people recommend it.

Thanks for your patience.:p

---

### Post by ptn107 on 2015-02-09
Please please prepare your Windows partition before you re-size it.  You could really screw up Windows if you don't.

From within Windows:
1) Disable the pagefile.
2) Defrag windows, twice.
3) Re-size the Windows partition with Disk Management.

---

### Post by fantab on 2015-02-09
> I'm just curious as to why a lot of people recommend a separate partition for /home

A separate /home is an advantage to have during OS upgrades and/or  reinstallations. Keeping your data on a different partition than system parition it the right thing to do.
Since you won't be keeping data on /home you don't need separate /home. Just a '/' partition will do.
Shared NTFS partition with Windows is not a bad idea. 
Good luck...

---

### Post by KayeNg on 2015-02-10
thank you ptn107, fantab, Bucky Ball, Michael Phelps, and others ):P

---

### Post by Bucky Ball on 2015-02-10
Solved? Please share with the community how. Thanks ... ;)

---

### Post by KayeNg on 2015-02-16
Well there wasn't any problem in the first place, I just really wanted to get some opinion.  I've decided to have the first partition as Primary which hosts Windows, then 2nd partition is Extended, inside of which are:
1st Logical partition -- NTFS, data partition shared by Windows and Lubuntu
2nd Logical partition -- EXT4, Lubuntu OS
3rd Logical partition -- swap

Is this ok?

---

### Post by Bucky Ball on 2015-02-16
Yep, that is fine. Windows has to be on a primary partition and the first primary partition is ideal. Sizes are about all you'd need to think about, because you have options. As you have no separate /home partition, for instance, you could have Lubuntu on a 20Gb logical drive and [symlink]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979") to folders like /Documents, /Music, etc., on the NTFS partition. Win could go on a 40Gb primary partition and, from memory, although it's been awhile, you can set Win to look at these same folders for its Documents, Music, etc. folders. This way, 60Gb for your OSs, 2Gb for /swap, gives you the rest of the space for the NTFS data partition.

With the above setup, if you need to re-install Win or Lubuntu, your data is on the NTFS partition and NOT the OS partition. 

Good luck. ;)

---

### Post by KayeNg on 2015-02-16
Excellent! Thanks! :p

---

