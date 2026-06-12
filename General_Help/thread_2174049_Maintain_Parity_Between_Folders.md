---
title: "Maintain Parity Between Folders?"
date: 2013-09-12
forum: General Help
---

### Post by mamamia88 on 2013-09-12
I mostly listen to my music on a portable mp3 player around the house.  Well the the thing is so tiny I know I'll manage to lose it someday so I would like to make sure my music is all backed up just in case.  I know I can redownload it again from amazon but that would be a pia if i could just copy it back from a backup folder.  My music is all stored in a single folder in .mp3 files and tagged with proper metadata.   I would like to have at least 2 backups.  I usually just dump an entire album onto the mp3 player and when a song comes up that i don't like i delete it directly on the player.  My question is, is there any easy way to automatically delete the files from the backup folder that no longer exist on the mp3 player?   Something like diff but that appends an rm it?

---

### Post by vasa1 on 2013-09-12
Parity?

---

### Post by The Cog on 2013-09-12
I would use rsync for that kind of job. Something like
```
rsync --delete /media/myname/musicplayer /home/myname/music/myplayer
```
but that is from memory, and using made-up names. Still, it should give you the general idea.

---

### Post by mamamia88 on 2013-09-12
hmm i need to look into rsyn.    Sounds promising.  Edit the usage for rsync in the manual says 
For usage> rsync [OPTION...] SRC... [DEST]
and > --delete                delete extraneous files from dest dirs So would the mp3 player be the SRC and the backup as the DEST?

---

### Post by ajgreeny on 2013-09-12
> **mamamia88 said:**
> hmm i need to look into rsyn.    Sounds promising.  Edit the usage for rsync in the manual says 
For usage
and  So would the mp3 player be the SRC and the backup as the DEST?

Yes, that's correct.

I've never used it, but I think unison could also do the same job, but if rsync works for you, stick with it.

---

### Post by mamamia88 on 2013-09-12
> **ajgreeny said:**
> Yes, that's correct.

I've never used it, but I think unison could also do the same job, but if rsync works for you, stick with it.

Well that doesn't work. I created two folders called A and B.   I then created text files 1 2 3 in A and Copied them to B.  I then deleted 3 in A.  I ran the command rsync --delete /home/user/A /home/user/B and it told me it wouldn't work without the --dirs option.  So i through that in the command and all it seemed to do was create an empty folder called A in B.   Any ideas? Unity gui with option to resolve differences for first root seems to work.  Wonder what the similar command would be

---

### Post by mamamia88 on 2013-09-12
AHHHH this is driving me crazy.  rsync -r --delete /path/to/A /path/to/B just copies files in A minus files in B to a folder in B called A.  And rsync --dirs -delete /path/to/A /path/to/B just creates and empty folder called A in B.  And it won't let me use --delete without running either dirs or -r

---

### Post by The Cog on 2013-09-13
**[FONT=Courier New]rsync -r --delete /path/to/A /path/to/B[/FONT]**
will duplicate folder A into folder B so now you have a copy of folder A in folder B. 

If you want to just duplicate the **contents** of folder A into folder B, put a slash after the A like this:
**[FONT=Courier New]rsync -r --delete /path/to/A/ /path/to/B[/FONT]**

Adding a -v option may help understand what it's doing.

---

### Post by tea for one on 2013-09-13
I also get a bit bamboozled by the rsync syntax and flags so I regularly use Grsync

---

### Post by ajgreeny on 2013-09-13
> **tea for one said:**
> I also get a bit bamboozled by the rsync syntax and flags so I regularly use Grsync

Same here.

If you use grsync and browse to the folders you are wanting to sync, it adds the trailing / to folders automatically, avoiding the problem you had.

---

### Post by mamamia88 on 2013-09-13
> **The Cog said:**
> **[FONT=Courier New]rsync -r --delete /path/to/A /path/to/B[/FONT]**
will duplicate folder A into folder B so now you have a copy of folder A in folder B. 

**If you want to just duplicate the [B]contents** of folder A into folder B, put a slash after the A like this:
**[FONT=Courier New]rsync -r --delete /path/to/A/ /path/to/B[/FONT]**[/B]

Adding a -v option may help understand what it's doing.

This did the trick for me.   Can't believe I got so frustrated with this that I had a headache for nearly 12 hours when all i was missing was a slash.   I love that linux can do that in a single command but still.  Can this command be used for say 3 different directories? Say I connect my mp3 player and the 2 external harddrives in my drawer? Edit again grsync does the same thing but i still have to add the / manually it appears

---

### Post by ajgreeny on 2013-09-13
Interesting!

I could have sworn that grsync added the trailing / all by itself, but having just tried it I see you are right.  I wonder if it has changed its behaviour over the many years I've been using it?

---

### Post by The Cog on 2013-09-13
> **mamamia88 said:**
> This did the trick for me.   Can't believe I got so frustrated with this that I had a headache for nearly 12 hours when all i was missing was a slash. 
Yes, it's not obvious. It is there in "man rsync" in the USAGE section, but even so it's not obvious on  a first reading. It took me a while to figure it out, too. I have used these in the past:
**[FONT=Courier New]rsync -r A/. B[/FONT]**  (I think that's the same as just using A/)
**[FONT=Courier New]rsync -r A/* B[/FONT]**  (Not so good. Expands the contents into a list before calling rsync, and misses hidden files.)
>   I love that linux can do that in a single command but still.  Can this command be used for say 3 different directories? Say I connect my mp3 player and the 2 external harddrives in my drawer?
It can copy multiple files or folders to one destination. It can not copy to multiple destinations in one command. So for instance, 
**[FONT=Courier New]rsync -r A B C D E[/FONT]**
would copy A, B, C and D to E. If you want to replicate to multiple destinations, put multiple rsync commands into a script and call the script.

---

### Post by dcstar on 2013-09-17
Use the **remmina** package.

---

