---
title: "How do i backup to dvd when they're always read-only"
date: 2007-04-12
forum: General Help
---

### Post by Gumper on 2007-04-12
I'm really having troubles understanding something here. In my windows installation I'm able to do incremental type backups of my files to dvd+r disc by using SyncBackSE,  but unfortunately I can't seem to figure out how to do this with Ubuntu or if it is even possible.

I installed GRSYNC and k3b hoping this would enable me to do this but it's not working. Let's say that i copy a folder to a blank dvd+r disk with k3b. I would then like to compare this folder with the original one on my hd with GRSYNC to see if there are any changes that need to be copied to the dvd. When i try this i receive errors from GRSYNC saying that the media (dvd) is "Read-only file system. 

I don't get it. How comes I'm able to do this in windows but not here in Linux? 

Is this even possible in linux?

Thanks for the help,

Gumper

---

### Post by tictacman on 2007-04-12
Did a google for you. Is this any good?

[http://www.theblackpawn.com/step-by-step-tutorial-to-burn-a-multisession-cd-in-linux.php](http://www.theblackpawn.com/step-by-step-tutorial-to-burn-a-multisession-cd-in-linux.php) in know its cd but it might yield some clues for setting it up for dvd

---

### Post by Gumper on 2007-04-12
Well i tried to burn a dvd using multi-session as in the link you posted but that's not working either. I still get errors that the disk are read only when i run GRSYNC.

This really stinks.

Could it have to do with permission rights?

Gumper

---

### Post by pointone on 2007-04-12
Just for clarity: You're not actually trying to burn anything with (g)rsync? You're just trying to compare files already on the disc to files on the hard drive?

*EDIT* Is this of any help?

[http://samba.anu.edu.au/rsync/FAQ.html](http://samba.anu.edu.au/rsync/FAQ.html)

> If you get "Read-only file system" as an error when sending to a rsync daemon then you probably forgot to set "read only = no" for that module.

---

### Post by Gumper on 2007-04-12
Yeah I am trying to burn to the disk with GRSYNC. I guess it's not designed to do that? 
I just figured it would be able to burn to dvd because I'm able to have it write to a USB stick. 

I'd like it to compare what's on the dvd to what's on the hd and then update the dvd with any changes. I'm able to do this with windows. 

If i try to burn to the dvd with GRSYNC, shouldn't it just use the dvd burner program built into Ubuntu?

Is there any backup program that is able to write directly to dvd?

Gumper

---

### Post by tictacman on 2007-04-13
Take a look at this thread there are some ideas for incremental backup to dvd.

[http://ubuntuforums.org/showthread.php?t=283954&highlight=incremental+backup+dvd](http://ubuntuforums.org/showthread.php?t=283954&highlight=incremental+backup+dvd)

---

### Post by FastZ on 2007-04-17
You can only burn to a DVD+R once, after that, it's read-only. Try doing this with a DVD-RW disc and see if that will work.

---

### Post by Gumper on 2007-04-17
Thanks. I've tried both DVD+R and DVD+RW with the same results. I always get the message that they are "read only". 

I presently don't have any DVD-RW disc's. Is there that much difference between them and DVD+RW?

Gumper

---

