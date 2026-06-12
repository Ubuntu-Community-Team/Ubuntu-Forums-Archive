---
title: "imaging non raid ubuntu to raid"
date: 2008-02-20
forum: General Help
---

### Post by cashmoney on 2008-02-20
Hey fellas and ladies,
      I need some help pull up a chair and eat a sandwich because this might be long winded.

Originally my PC was set-up with two HDDs one Ubuntu and one XP.  Now I have 2 (250) sata drives Raided.   I partitioned my HDD using windows then imaged my XP drive over to the first partition of the raid (FakeRaid my bad).  Now I have installed Ubuntu onto the 2nd half of the FRaid but I am having loads of problems setting it up the way I want.  So I decided to follow this thread [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore) and just backup and restore.  Well when I went to restore it my GRUB got severely whacked and I couldn't load Linux at all even with a super Grub Disc.  I believe the partition information was copied from the non-raid to the FRAID and it jacked everything up.  With the SGD I fixed the mbr to load xp then re-installed Ubuntu so I have a fresh install but I cannot get SLI to work with the video cards and whatnot.

It would be easier if I could backup my Non-Raided Ubuntu and restore it to the FRAID set up but I do not know how to go about that.  I could use some suggestions because I am getting tired of installing Ubuntu on the raid set up when something fails to install miserably like Nvidia drivers and setting up SLI.  It took me three weeks of tweaking my Ubuntu to get everything working the way I want it.

Thanks in advance
Nate

PC Specs
AMD athlon FX 64 4GB Ram
Geforce 8800gts 640MB SLI
Crosshair Mobo
(2) 250GB sata (hopefully Ubuntu will be on sata soon)
and ubuntu on IDE

---

### Post by cashmoney on 2008-02-22
Ok so I finally figured it out.  If anyone out there wants to migrate their non-raid ubuntu to a Raid ubuntu this is how you do it.

Step one:   Follow these directions to install ubuntu on the FakeRaid 0  [http://ubuntuforums.org/showthread.php?t=630644&highlight=howto+fakeraid](http://ubuntuforums.org/showthread.php?t=630644&highlight=howto+fakeraid)

Step Two:  Then restart your pc and load up the NonRaid Ubuntu drive.  Follow these directions to backup your stuff DON'T RESTORE IT YET!! [http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup+restore](http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup+restore)

Step 3:  Next I loaded up the Raid0 Ubuntu and mounted the non raid drive.  Copied the backup to the desktop.  Then I made a copy of /Boot and /initrd.img ... Next I ran the restore command from the link above and when that finished I then went to terminal and made my way to my Desktop with all of the backups.

sudo cp -fr  /boot /   

sudo cp -f initrd.img /

I lost networking capabilities and couldn't access the internet at all after restoring.  I then restarted ubuntu and all of my settings popped up and everything is working great on the new Raid0
 :popcorn:

Nate

---

