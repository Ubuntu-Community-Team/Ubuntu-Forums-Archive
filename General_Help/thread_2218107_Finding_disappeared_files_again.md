---
title: "Finding disappeared files again"
date: 2014-04-19
forum: General Help
---

### Post by Fabzil on 2014-04-19
Hello community!

I'm currently travelling around the world so I was saving all my pictures and HD video on external hard-drive N°1
My brother convinces me to buy external hard-drive N°2 to have a **back-up of the back-up.**

It was a brilliant idea because 1 week after, **exHD_N°1** greatly suffer from a fall and about 50% of the files are now read/write error. All the pic and video were already saved :)

Then, I was copying movies from corrupted exHD_N°1 to exHD_N°2 to get at least half of them (something you are bored when you travel), when **the computer froze** (reading corrupted files take a LOT of ressources and we are talking about big files likes movies, and a lot of them. Me stupid)

After the hard reboot, exHD_N°2 got some of the movies **BUT THE FOLDER WITH ALL THE PIC AND VIDEO** was empty ! oO 
For no reasons, I was working with another folder, and all the other files (music, movies) are fine, but the WHOLE folder of pic and video is now empty, right-click properties shows 4 Ko.

BUT **the files are still there**, because the total size of all the root folders is "44,8 Gb", when the drive has "Free space: 309,0 GiB (Total 465,8 GiB)". That about 120 GiB for my pic and video

Knowing I could **recover** those files with a recovery tool, I start looking around and I found this : [Five Best Free Data Recovery Tools]("http://lifehacker.com/5237503/five-best-free-data-recovery-tools")
I started using **PhotoRec** and I configured it to look at the whole drive just to make sure. I'm writing the recovered data on **external hard-drive N°3** so I don't mess things up.

It has been running for about an hour now, and I got about 4 hours remaining. I'm happy to tell you that **some videos and pictures are showing up!** :)


Now, I just wanna make sure I got this right so please answer my question if you have any knowledge about this : 
- **Am I doing this right?** *Because I'm using a laptop, so 5 hours of constant CPU usage is something I would like not to do in vain too many time ^^*
- **Is there anyway I can get the hierarchy of folders back?** *Sorting all those pictures is gonna take me hours and hours, I mean, days!*
- **What if I don't recover everything when the recover is done? Is there anyway to go deeper/better/stronger?*** (pun intended)*

Thx you very much for your help, this is really not cool happening to me between Laos and Vietnam!

Fabzil

---

### Post by dragonfly41 on 2014-04-19
Sorry to hear about your loss .. but in fact your story shows that even making one backup can lead to data loss.   It is prudent to keep n copies where **n is greater than 2**.

First point I would make is don't scrap damaged exHD_No1 since in the limit you might be able to recover data even from mechanically damaged drives.   So just stow it away safely for now (but after cloning disk image .. see below).

For a short time after dropping your drive you were left with no redundancy and this led to another mishap.

The link you posted points to photorec .. which will be able to recover files .. but using this utility (which is excellent) you will lose directory structure and file names.

Also it can take **many hours**, sometimes days of 24 hour running for the files to be recovered so you must leave your PC running.  Which can be problematic if you're travelling around the world.  i.e. you can't pause the recovery process and restart.

If you were copying .. rather than moving .. files then there is a good chance that they can later be recovered from exHD_No1 .. even if mechanically damaged.

What you should have done .. and perhaps now is the time to do it .. is to first clone the entire disk image of exHD_No1 to a fresh drive exHD_No2 .. perhaps drive attached through a USB port .. and if the data is very important do this to a second drive so you always follow the rule that redundancy is > 2.

You'll read here in this forum  that sudo command dd may be used to create a cloned image .. but there are too many stories of this command going badly wrong if the command is badly written and the source disk is then zeroed as a result.

So I suggest using a safer cloning approach than dd .. using a GUI tool.

Clonezilla can clone images .. or gparted can clone partitions.

Then you try to recover data from the cloned image .. not from your original damaged drive which is stowed away. 

You could consider uploading your image or recovered files to a cloud service (DropBox or other) so you can retrieve these later when you finish your travels.

You haven't explained if these files were on NTFS, or ext formatted partition.   If you were on windows then there are other recovery tools.

Another linux tool to try is from Easus.

I would also try **testdisk** which can recover directory structure and file names.  Testdisk and photorec are companions.

Some links .. supporting your current approach ..
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Search this forum for "data forensics" and "data recovery".

---

