---
title: "Copy lots of files"
date: 2007-04-13
forum: General Help
---

### Post by nik on 2007-04-13
Hi

I recently had a fatal harddrive error. Had to change harddrive. Recovered a lot of the files, but not my music, about 50 Gb...

Now, I have a quite recent backup on several DVD's. But when I try to copy them to harddrive, I get lots of errors (I/O error). So my questions are;

1, Is there a utility that is better to copy files than normal gnome / nautilus?
2, Is there a way to copy the files and automatically ignore the errors?
3, If so, is there any way to get a log of the errors, preferably in a text file (not just terminal) so I can check later what files got errors?

I'd really appreciate some help here, as I've spent a lot of hours ripping this music...

---

### Post by Adramelech on 2007-04-13
1. use the cp command.
   use: cp source dest
   help: man cp
3. Redirect output to a file
    use: command > file
            cp source dest > log.txt

---

### Post by m.musashi on 2007-04-13
Does the problem happen if you try to copy/move files from other sources? Can you rule out any kind of hardware failure (HD or DVD)? Can you check the DVDs on another drive/OS to see if they are fine? How about copying one file at a time (just as a test) to see if you still get the error.

I ask just to try and figure out what is causing the problem. Normally, you shouldn't have any problem copying files so my first thought is something else is up.

---

### Post by nik on 2007-04-13
Cheers. Excactly what I was looking for :D 

Using linux for more than a year now, I'm still amazed at how easy things can be done :D

---

### Post by anaconda on 2007-04-13
dd_rescue is meant for that kind of jobs. I think cp cant handle the errors wery well. dd_rescue wil try to read the corrupted part several times before it gives up, so it can rescue files that cp can't copy

here is some info:
[http://ubuntuforums.org/showthread.php?t=318390&highlight=dd_rescue](http://ubuntuforums.org/showthread.php?t=318390&highlight=dd_rescue)

good luck!

PS. you might have to install dd_rescue before you can use it.. the name of the packkage is either ddrescue or dd_rescue..

---

