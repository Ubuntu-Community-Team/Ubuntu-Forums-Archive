---
title: "Folders in use disappeared"
date: 2017-05-31
forum: General Help
---

### Post by drigorj on 2017-05-31
Hello guys,


First of all, sorry for my bad english and some issue.


[I have dual boot with Ubuntu 16.04 and Windows 7 but I'm using predominantly only Ubuntu. I have 4 partitions: 1 ext4 (where Ubuntu is installed) and 3 ntfs (1st for Windows, 2nd that Windows itself maked and 3rd for my personal files)]


On Saturday (05/27) strangely, 3 folders that were in use in the last session disappeared:
* "Estudos" (with abstracts in open txt)
* "Download" (with active torrents)
* "Steamlibrary" (with Steam open and 2 games installed)
The 3 folders are from the NTFS partition with personal files.


I looked in the trash, inside other folders, but found nothing.


I already searched about in many places and one link that I found was this: [http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/)
But what I understood this is specificaly for ext partition and mine is NTFS


I ran Recuva on Windows and tried the chkdsk too but found nothing.
After this, when I started again in Ubuntu I noticed that a folder called found.000 appeared. Inside it were some of the files from 2 of the 3 folders but they were not all.
On Sunday I tried the Recuva and Check Disk again and again nothing. And starting at Ubuntu, the SteamLibrary folder came back with the correct structure but the final content was not there.


Anyway, the most important folder is the "Estudos" and only 10 txt files from there, which are my summaries.
Please, I need so much of help to recover these files and understand what happened.


Grateful!
Rodrigo

---

### Post by ajgreeny on 2017-05-31
You say these missing folders are in partitions that are NTFS, so I wonder if an update of your Windows OS has occurred and re-enabled fast start meaning the system is again using the hibernation that has been the default since, I think, Windows 8.

Hibernation means that the partitions will not be accessible from ubuntu if they were not fully shutdown when last used in Windows.
Check that fast start is not enabled and if it is disable it again then fully shutdown Windows to see if the partitions/folders are still present and can be seen in Ubuntu.

---

### Post by drigorj on 2017-05-31
> **ajgreeny said:**
> You say these missing folders are in partitions that are NTFS, so I wonder if an update of your Windows OS has occurred and re-enabled fast start meaning the system is again using the hibernation that has been the default since, I think, Windows 8.

Hibernation means that the partitions will not be accessible from ubuntu if they were not fully shutdown when last used in Windows.
Check that fast start is not enabled and if it is disable it again then fully shutdown Windows to see if the partitions/folders are still present and can be seen in Ubuntu.

I think the hibernation in the Windows is enabled since I installed it. And I looked at the Windows updates, they were installed on Sunday, 28, and the files disappeared on Saturday, 27 (and others updates were installed only on 04/29, the last time that I used Windows)
I didn't "power off" the Windows with hibernation, I only restarted. 
And Ubuntu is seeing the partition normally, including all others folders that weren't in use are perfect both in Ubuntu and Windows.
By the way, Ubuntu was suspended on Saturday, I power on it, restarted normally and I power on in Windows. The problem would be the suspend in Ubuntu, or not?

---

### Post by ajgreeny on 2017-06-01
Sorry, this is now all beyond my knowledge as I am very out of date with Windows and I do not know what is needed to ensure it totally shuts down when powered off.

---

### Post by drigorj on 2017-06-02
> **ajgreeny said:**
> Sorry, this is now all beyond my knowledge as I am very out of date with Windows
And in Linux, do you know anything I can try to recover?

---

### Post by ajgreeny on 2017-06-03
No sorry, I have never needed to recover any files from disks or partitions, so my experience of this is zero.

Many users have, I believe, had success with Testdisk and the photorec application included within it, but again I have no experience of it so can't tell you any more.
Go to [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) for more info.

---

### Post by drigorj on 2017-06-06
No problems, thanks for the help
I already tried both Testdisk and Photorec but didn't can recover them.

---

