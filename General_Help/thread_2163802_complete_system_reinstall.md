---
title: "complete system reinstall"
date: 2013-07-19
forum: General Help
---

### Post by silconsystem on 2013-07-19
Hi all,I,ve been wanting to do something for some time now but I havent had the courage yet. 

Now I've got some weeks off and I'm going to try it...
But..Before I'd like to ask some seasoned ubuntu users whats the best approach, here goes:
I've got an old PC I've built myself;
1.9 Ghz AMD Athlon xp 2600+Nvidia GeForce FX 5200
2 GB Ram
ASRock K7S8X Motherboard
1 x 40 GB Drive (holds Xubuntu)
1 x 80 GB Drive (holds 4 partitions, 1 x 19 GB Backup partition, 1 x 13 GB Files, mostly music & games, 1 x 16 Gb Files, mostly tar & zip for sharing, 7 x Gb of Backtrack dictionary, tables caps, etc and 22 GB for Backtrack.   the remaining GB' s are swap space.)
The reason for all the mess is that I've tested, used, broke and repaired lots of distros shifted data around etc. But Xubuntu (11.10) has been faithfull to me for some 2-3 years now.
 I' ve customized many things and updates mostly resulted in broken programs and boot problems so I'd like to keep it how its now.
 I've got a much better computer which I use for the heavy lifting like graphics, coding, etc. And I've learned how to maintain a linux system on my old xubuntu/many other linux flavours box.

So...
 I'd like to backup my entire customized Xubuntu box + all the files in my home folder + my music & games drive (although not everything).
Then use a live cd/stick and use Gparted (or similar) to format my drives.
 40 GB drive for Xubuntu and split my 80 GB in half, 40 GB Files, 40 GB backup drive.
I've used `backintime` to make snapshots of Xubuntus root/ directory and my home/ directory (although I'm not sure why this program is split in user and root, if I backup root/ isnt home/ included?)

How should I proceed now? Format and repartition I know, but how do I restore my old system? Since I was (and still kinda am) not very wealthy I never had enough space to make backups so I'm a total virgin in this area, I know its stupid but (I've been fiddling with computers since I was born actually, started with opening Atari cardridges to "change" the games, didnt work though ;) )

I've never bothered to make backups of anything, just burned some cds and filled some usb-sticks with files that I wanted to keep.
Could you throw me a bit in the right direction? My Xubuntu OS is getting kinda slow and all these partitions annoy me too.I dont want to upgrade, just empty the disks, make em fresh, make good use of the space and put my customized Xubuntu 11.10 back on it without all these partitions I created installing god-knows what.
Backtrack has been replaced by Kali and put on my newer box and the files for it I remove with usb-stick.
Some reading material about backing up linux and sheduling it would be very welcome. I dont want to lose data on any machine anymore.
Also keep in mind that I cant buy additional kit easily. I have to work with the stuff I have unless there is absolutely no other solution than buying new stuff (my wife cant be easily convinced that SSD drives or NAS boxes are a must-have life priority, prefers food and paying rent for some reason).


Cheers,Rob

---

### Post by sudodus on 2013-07-19
Backup should be on a separate drive or computer. It is best if it is in a separate house (if there would be a fire). In your case I would suggest that you use ***the 80 GB drive for backup*** and the 40 GB drive for Xubuntu (and maybe a small test partition (8 - 12 GB)).

You should decide if you want a ***complete backup*** of everything: an image by Clonezilla, or a ***backup or the important files***, that is run frequently (once a week or every night) or some kind of ***combination***. And maybe you can use the 80 GB drive to backup also (the important files from) the new computer. Backup of important files (or whole directory trees) can be made with rsync or some graphical user interface for rsync.

You can find tutorials on the internet describing tools and methods. But before you get too deep into details, try to think a lot about ***what you really don't want to lose***, and how often you need to run your backup.

---

### Post by lukeiamyourfather on 2013-07-19
I would advise against reinstalling Xbuntu 11.10, it's no longer supported (which means no security updates) and frankly it wasn't a very good release to begin with. I'd try up to date software after you wipe out the drives and see how you like it, maybe Lubuntu 13.04 or Xubuntu 13.04 if you really like Xfce. If you don't like the newer software then you can reinstall Xubuntu 11.10 like you were planning on doing anyway.

As for backing up everything before reinstalling, if you have a spare disk laying around I'd clone everything over with Clonezilla. Then you'll be able to grab whatever you need (it's easy to forget little things, this way you have all of it). If you don't want to save everything then I'd use rsync (-a) to copy /home, /etc, /opt, /usr/local, and any other directories you've manually created on the root level.

---

### Post by sudodus on 2013-07-19
> **lukeiamyourfather said:**
> I would advise against reinstalling Xbuntu 11.10, it's no longer supported (which means no security updates)

+1
I did not notice it, but yes, you should install a current version of Xubuntu. The current versions are Xubuntu 12.04.2 LTS with support until April 2015, and the short-life versions 12.10 and 13.04, which are newer, but it is probably an advantage only with new hardware.

---

### Post by lukeiamyourfather on 2013-07-19
> **sudodus said:**
> 
The current versions are Xubuntu 12.04.2 LTS with support until April 2015

Good call, I had to double check that it was supported that long. It used to be that Xubuntu treated LTS releases like any other (18 months or whatever). I might give it a shot myself knowing it's supported for longer now!

---

### Post by silconsystem on 2013-07-20
Hi guys,

Thanks for your advice, I think I'll use the 80 GB for backups from now on then. If I'm correct backintime is an rsync GUI so I have the snapshots of both home/ and root/ directories.
I'm not upgrading for this PC, its only connected to the internet if want to install something new and I didnt do that for ages, like I said I've set everything just how I like it and prior upgrades always created problems in the past mostly with programs I compiled from source due to dependencies changing and stuff like that.
My newer machine I can maintain and upgrade without any problems, since I've learned from all the mistakes I've made with my Xubuntu/other distros box.


Anyhow,


thanks for your good advices, if I run into problems I'll check back in if not Xubuntu 11.10 is happily running on a cleaned up environment.


Cheers,


Rob

---

