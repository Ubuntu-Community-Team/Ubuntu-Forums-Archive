---
title: "Mysteriously lost files ; where to find?"
date: 2007-09-26
forum: General Help
---

### Post by Atypicas on 2007-09-26
Hello :)

My hard-drive is split into three main partitions ; Windows XP, Ubuntu (Feisty Fawn) and one that stores all my music, some programs and my personal files -- many of which are non-replaceable and important to me.

I was running Ubuntu and leaving my computer open to pursue downloads and when I came back home, after work, I noticed that my desktop had a broken shortcut. I deleted it and went to create a new shortcut, but noticed that, on this third partition, my folder with my personal things named Atypicas (including the folder that this shortcut linked to) was completely empty. Everything else was unaffected. I ran a search to see if it had just been moved and I looked into my Ubuntu trash can as well as the trash can specific for non-Ubuntu partitions (hidden .trash folder) and I still found nothing. I also rebooted Ubuntu and now I am on XP and still, nothing.

I can not think of anything that would have affected this folder since I last used things within it.

Is there anywhere I could find what I lost? :confused:

---

### Post by tgm4883 on 2007-09-26
sounds like it's not mounting.  Try manually mounting it from the command line and see what kind of errors you get.

---

### Post by Atypicas on 2007-09-26
Thank you for the reply!

I should have noted that I'm quite new to Ubuntu ; I have no idea how to mount the folder. I'll be googlin' and if I find an answer I'll edit this post, but a brief search gave no obvious command.

---

### Post by tgm4883 on 2007-09-26
What kind of partition is it?  NTFS?  EXT3?

---

### Post by Atypicas on 2007-09-26
Hmm, could it be both? Look at [this image](http://i127.photobucket.com/albums/p129/Atypicas/HD.png).

There is a Swap partition, a Linux partition of around 20gb, a NTFS partition for Windows of around 20gb and my other partition, of around 260gb, seems to show up twice on partition lists, one as the subset of the other (on Partition Magic and the Live CD if I recall). Both Extended and NTFS tend to show up in the names.

By the way, for my problem, everything else on the partition shows up, it's just media/sda5/atypicas/ that is empty, but /musique, /downloads, /programs are all fine.

---

### Post by Atypicas on 2007-09-27
[IMG]http://i127.photobucket.com/albums/p129/Atypicas/Partitions.png[/IMG]

---

### Post by tgm4883 on 2007-09-27
Hmm.  Well if the other directories are there then it's being mounted.  

Try enabling hidden files and see if they are hidden.  Also, check in the trash folder and see if they are there.  Lastly, it is a ntfs partition, so perhaps there is some form of corruption on that part of the disk.

---

### Post by Atypicas on 2007-09-28
I checked all of this and even used an undelete program (with Windows; couldn't find one with a GUI on Linux). I might have been able to recuperate what I lost, but because i had ktorrent active, downloading to that same drive, the deleted files were even less likely to be recuperated. I doubt there's anything I can do, except start looking for a tool to sync data between two partitions/hardrives or, ideally, gmail "drive" and my main folder. I tend to forget to make backups

I still would feel more secure knowing why it all disappeared. I really do not see how it could be a mistake on my part and it, if it was a because of the HD, it would seem strange that only the contents of one folder  and its subfolders) would be wiped without a trace.

---

