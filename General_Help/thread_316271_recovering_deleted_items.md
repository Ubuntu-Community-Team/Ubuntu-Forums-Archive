---
title: "recovering deleted items"
date: 2006-12-10
forum: General Help
---

### Post by maniacmusician on 2006-12-10
hey

so here's the situation. I just reinstalled Kubuntu on my computer, and I have my /home dir on another partition. From previous experience, I knew that leaving all the config files in my home dir has the potential to screw with the settings on the newly installed OS. So, I backed up all those settings files to another folder, and then I *deleted* them from my /home/<user> dir. So, I boot into my newly installed Kubuntu, and reinstall the programs I used to have, and copied over the backed up settings files to restore the programs to their previous state. A problem occurs; They didn't copy over properly! Particularly the .opera folder, was blank; no files in it, just the folders. Now, that is my most important application....it had stored passwords, lots of important bookmarks, various e-mail addresses that I managed with opera, etc. So it's just my luck that opera is the one that gets wiped out...

So my question is, is there any way I can now recover the .opera folder that I deleted from my /home/<user> dir? Please please please tell me there is. I already checked /home/<user>/local/share/Trash, and /home/user/.Trash-0 (the root trash folder) and it's not in either of those locations. If it helps, I deleted them as a normal user, not root. 

Please help me; I **need** those files

---

### Post by riven0 on 2006-12-10
Hmmm, not sure if this will help, but have you checked [this article]("http://www.linux.com/article.pl?sid=06/08/21/1558230") out?

---

### Post by maniacmusician on 2006-12-10
looks tough...
>  This means that the partition on which the recovered files are to be stored should have at least as much free space as the size of the partition on which PhotoRec is searching for recovered files.
this is impossible, as my /home/<user> partition is 200 GB, the largest I have by far (others are 20 (seperate hard drive, 80GB, 60 GB free space) and 100 (another partition on the same)). 

Also, since it is my /home/<user> partition, and the hard drive has to be unmounted during recovery, I would HAVE to use a live CD. Don't know if I have enough skills for it...because since it'll be on a live CD, I won't really have a storage medium...I'd have to create a partition on one of my hard drives (of maybe around 50GBs) and mount it using the live CD....my head swims. I shall attempt it at least...thank you very much for the link. If anyone has any other methods, that would be awesome too, but for now I'm off to try this one. Thanks again!

---

### Post by maniacmusician on 2006-12-10
ok, this space is getting used up really fast lol, I don't think the 50Gbs is going to last much longer. Also, big problem...all the files it's recovering are not retaining their original names. They're just named f with a number after them. like: f5756878.txt, stuff like that. and not all of these files are mine. I can see some videos I deleted a while ago, but there's a lot of weird text files (one contains an essay about Oedipus  Rex that I certainly didn't write).

So does anyone have any experience with this software? help? if the documents recovered don't retain filenames and folder structure then this is useless because I'm trying to recover config files for opera...

---

### Post by riven0 on 2006-12-10
Haha! It's recovering everything?! Alright, why don't you stop that and try [this program]("http://freshmeat.net/projects/addrescue/"). From the description it says you can pause and resume at anytime, so you can always look over what you recovered and delete what you don't need if you run out of room.

---

### Post by maniacmusician on 2006-12-10
okay, I stopped it. It had recovered 45 GB's of stuff! and yes, everything! Even after I narrowed it down to just txt files, and archives, and html files. It was getting stuff like license agreements, teacher lesson plans (??? I'm not a teacher), random blurbs of codes. It was interpreting xml files as txt and pulling in their code, it was also interpreting .odt and .doc documents as text, I foudn little bits and pieces of essays that I've done over the years. It was insane. okay so I guess I'll try that ddrescue program now, still on the livecd.

---

### Post by maniacmusician on 2006-12-10
[scratches head]...still trying to figure out how to use this thing, it completely baffles me.

---

### Post by maniacmusician on 2006-12-11
does anyone have any tips on how to use ddrescue or does anyone have another solution?

---

