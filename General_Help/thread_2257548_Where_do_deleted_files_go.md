---
title: "Where do deleted files go?"
date: 2014-12-20
forum: General Help
---

### Post by lusbyclark2 on 2014-12-20
My PC has a 120 GigaByte Solid State Hard Drive.  There are several multiple GigaByte files stored somewhere on my SSD that I very much would like to remove completely. The entire data set probably amounts to about 15 GigaBytes, maybe more.   So completely ridding my PC of these unwanted files will really free up a great deal of memory.   Will dumping these files into the Trash bin completely rid my PC of these files, or rather does the operaring system store these files at some out of the way, hard to get-at locartion on my SSD?   Is there a special software application I can download to help me with this problem?

---

### Post by Bashing-om on 2014-12-20
lusbyclark2; Hi !

The act of moving files to 'trash' merely moves the pointers to the file(s). No space will be reclaimed until such time as the 'trash" is emptied.
On the otherhand, in terminal the 'rm' command will remove those pointers and release the space. BUT, there is no "undo" operation. Once removed from terminal, extremely difficult to retrieve a 'rm'd' file.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by coldraven on 2014-12-21
In Nautilus pressing the delete key sends your files to the Trash can.
Pressing Shift+Del erases them permanently, you cannot get them back.

---

### Post by HermanAB on 2014-12-21
As for the original question: Where do deleted files go?  The pointers and electrons are recycled and the data goes to Lostralia.

---

### Post by lusbyclark2 on 2014-12-21
Hypothertically speaking, let's say I have a list of phone number stored on my hard drive.  At some point I decide it would be best for me to to remove these numbers from my hard drive.  Could a sufficently skilled computer hacker dive into my computer and still locate those those phone numbers, and having copied them to his/her computer, use them against me as well as perhaps the owners of those phone numbers?  Or are they really gone for good, never to be seen again?

---

### Post by dragonfly41 on 2014-12-21
Just google search for "forensic data recovery" to see the array of tools available to dive into hard drives to recover deleted data.

In Ubuntu the widely used utility is testdisk.

Try testdisk to analyse your "clean" disk to see what can be recovered.

---

### Post by josh109 on 2014-12-21
Well, moving files to the trash meerly "ques"  them for deletion (in case you accidentally deleted something that you didn't mean to delete). To *completely *get them off of your PC, you need to move them to the trash, then empy the trash. Since you are on a solid state drive, once they're gone, *they're gone. *So make sure you *really want the files gone before you wipe them!*Also, when you said that you had a solid state drive, you shouldn't need to "seucre empty" the trash. But if these are confidentail files you are talking about,* I highly reccommend secureley erasing them. *Otherwise, you should be fine.

Regards,
J

---

### Post by josh109 on 2014-12-21
> Just google search for "forensic data recovery" to see the array of  tools available to dive into hard drives to recover deleted data.

In Ubuntu the widely used utility is testdisk.

Try testdisk to analyse your "clean" disk to see what can be recovered.
> 120 GigaByte Solid State Hard Drive
Forensic Data Recovery doesn't normally work on SSD, because data isn't over written, it's *forgotten.*
Things on SSD's aren't usually recoverable unless there is a third-party factor like backups involved.

---

### Post by josh109 on 2014-12-21
> Hypothertically speaking, let's say I have a list of phone number stored  on my hard drive.  At some point I decide it would be best for me to to  remove these numbers from my hard drive.  Could a sufficently skilled  computer hacker dive into my computer and still locate those those phone  numbers, and having copied them to his/her computer, use them against  me as well as perhaps the owners of those phone numbers?  Or are they  really gone for good, never to be seen again?
Well, it depends on the type of hard drive that is in your computer. If you have a Solid State drive, they are gone for good (but be sure they aren't in backups!)
If it is on a traditional hard drive (most machines), then you *really need to wipe them multiple times. I'm talking like 400 times. *

---

### Post by HermanAB on 2014-12-21
As for wiping a magnetic disk: They all have a special erase program in the drive controller, that can be activated with hdparm.  This special routine can erase the whole surface, including the spaces between the tracks.  Whether it is truly necessary to be that paranoid, depends on who is after you.  For most people, hammering a disk with a medium sledge would be more satisfying than waiting for the erase program though.

---

### Post by dragonfly41 on 2014-12-21
My ancient development setup does not yet use SSD.

But following a line of curiosity ... I found this ...

[http://nvsl.ucsd.edu/index.php?path=projects/sanitize](http://nvsl.ucsd.edu/index.php?path=projects/sanitize)

> Our results show that naively applying techniques designed for sanitizing hard drives on SSDs, such as overwriting and using built-in secure erase commands is unreliable and sometimes results in all the data remaining intact.

All depends on the level of sensitivity of data, I guess.

---

### Post by kpatz on 2014-12-21
After deleting a file on an SSD, its data does still remain, for a while anyway.  When a TRIM command is executed (immediately if mounted with discard option, or via a weekly cron job), the OS tells the drive which data blocks are free.  The drive then, either immediately or over time, shuffles things around to maximize free space and minimize wear.  During this shuffle process, empty blocks are erased and the data is then gone.

---

