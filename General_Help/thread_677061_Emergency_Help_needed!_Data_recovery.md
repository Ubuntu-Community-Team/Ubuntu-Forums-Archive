---
title: "Emergency Help needed! Data recovery"
date: 2008-01-24
forum: General Help
---

### Post by moreon on 2008-01-24
The situation is as follows:

I wanted to install Ubuntu on the second partition (ntfs) of the hard disk (sda5) where I have all my data and where there were 25GB free. I wanted to resize the partition and use 18GB as ext3 for the linux install. Here is where the sh*$ happened (my fault). I used the guided partioning in the intsallation process and then instead of using 18GB for ext3 I used the opposite and left 18GB free on the resized one.

So I messed it up and now I have one 140GB ext3 partition, 18GB unpartiotioned space and I lost all my data.

Is there any way of recovering the lost data? I would appreciate any help. Thanks

P.S. On the first partition of the disk there is WinXP installed.

---

### Post by LaRoza on 2008-01-24
Use Testdisk, see the link in my sig.

---

### Post by moreon on 2008-01-25
Can you be a little more specific? 

I mean, which are the operations I should do in testdisk so that I can unformat the second partition of my hd and change it back to ntfs with the now unpartitioned space and recover my lost data?

---

### Post by Herman on 2008-01-25
Here, take a look at this, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")  Using TestDisk to Recover from partitioning disasters demonstrated
              [CENTER](Edited on Friday the 13th!)

[LEFT]TestDisk is a program that can scan your entire hard disk looking for traces of what look like they might be the start blocks of old file systems  or partitions.

When it finds the most obvious ones it will give you a list, and you will need to pick out which ones in the list that you want written to a new partition table.

You'll see what I mean if you look in that link.
If you have any other old hard drives around that you can practice on first it would be a good idea.

Not all the partitions in this list might be your recent partitions, often TestDisk will bring up old partitions that you may have deleted a while ago. If you try to restore the wrong partitions, some might interfere with others because the file systems might overlap.
If you restore all the right partitions everything will be fine and dandy.
Even if you restore the wrong ones, you can still recover the data from them and copy it to a disk and then try again.

In your particular situation, it should in one way be simple, but in another way maybe not so simple. 
Since you didn't change the start point of your file system, it means you'll easily know where the partition was that you're trying to restore. Just run 'sudo fdisk -ls' and you'll see exactly where your partitions are on your disk.
On the other hand, it's better if the start blocks of your new file system didn't overwrite the important blocks of your old file system because that could have destroyed them already, so you might not be able to get them back.

It's probably best to try anyway, run TestDisk like the examples in that link show, and even try 'searching deeper', as shown in the second example.
If it works then good, you'll probably get all your files back, 100%.

I'm not sure if TestDisk is going to do it for you, because I'm guessing that your file system start blocks have been overwrtten with ext3, and the Ubuntu operating system, depending on how it got distributed physically on your disk, would be will be on top of some of your files, hopefully only on top of your old Windows operating system files. 

If TestDisk isn't able to get your old file system back, there is always PhotoRec, TestDisk's companion program. You might need to use Photorec.
Photorec can recover most of your files. Try TestDisk first though and see if you're lucky.

Regards, Herman :)
[/LEFT]
[/CENTER]

---

### Post by az on 2008-01-25
> **moreon said:**
>  I used the guided partioning in the intsallation process and then instead of using 18GB for ext3 I used the opposite and left 18GB free on the resized one.

So I messed it up and now I have one 140GB ext3 partition, 18GB unpartiotioned space and I lost all my data.

The partitioner should have refused to shrink the partition if it didn't have enough free space.  Did you interrupt it while it was trying to mave data around?  Did it create the filesystem, or just try to resize the partition?


> **moreon said:**
> 

Is there any way of recovering the lost data? I would appreciate any help. Thanks


[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

---

### Post by moreon on 2008-01-25
First of all I would like to thank you for the help so far.

I ran testdisk from a GParted LiveCD and performed a deep search but it didn't find the previous ntfs partition. All I see is the current partitions.

> 
The partitioner should have refused to shrink the partition if it didn't have enough free space. Did you interrupt it while it was trying to mave data around? Did it create the filesystem, or just try to resize the partition?


At first I tried to manually create a partition in the free space of the ntfs partition I lost but when I proceeded the partitioner gave me an error that it couldn't create the new ext3 partition. So then I went back and selected the first option of guided partitioning and there was the mistake I made. In the next step I chose 18GB because I thought that this would be the new partition for Ubuntu but it was the other way round. It used the rest 120GB for Ubuntu and created another 18GB ext3 partition.

This procedure returned no error and just continued with the installation of Ubuntu uninterrupted. So it split the former 138GB ntfs partition into two ext3.

---

### Post by Herman on 2008-01-25
Hello moreon,
If I'm understanding you right and my maths is correct, you had 133 GB or so of files. A new Ubuntu install will probably overwrite about 1.8 GB of that. Apart from the fact that you have lost the file system information that links you to your files, most of them will still be there, you just need to use the right software and find and recover them. 

What you decide to do next depends on how valuable your files are and how much of a hurry you are in. Generally, it's best not to hurry. A hard disk can sit around for years and you can still recover your old data.

It might be worth considering buying a new hard disk to use for now, if that will give you more time to work at recovering your files at a relaxed pace, plus it might make things easier if you have somewhere to copy your rescued file to.

Read the page az linked you to first and choose a suitable program.

If you decide to use PhotoRec here is a link to a page that help you, [COLOR=#c0c0c0][How to recover lost files after you accidentally wipe your hard drive]("http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss") [COLOR=Black]by Shawn Hermans.

Hello az,
I have updated my TestDisk Page with links to the page you recommended, and added the advice for people to go to that page first, before doing anything. 
Thanks az, that's a great page, I want to try out some of that software soon.

Regards, Herman :)



[/COLOR][/COLOR]

---

