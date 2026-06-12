---
title: "Queue multiple files for copy/paste"
date: 2017-02-18
forum: General Help
---

### Post by k0tt0n on 2017-02-18
I want to transfer around 50G of music from my laptop to an sd card. All the music is organised in folders A to Z and within those, artists folders, then album folders. Is there a way I can select the albums I want and queue them to just do one transfer? When I used windows I used a program called Teracopy where I could drag and drop them and it would create a queue that I could start and pause/resume and add to as it was copying. I've spent hours trying to find a similar program that works for Ubuntu but have had no real luck. the closest I've come is Krusader.

---

### Post by TheFu on 2017-02-18
rsync with pattern matching is how I'd do it - or I might use an exclude pattern, if there are fewer of those.
You could also build a list of files/directories using find, then pass that list into rsync to be copied/moved.

The great thing about rsync is that if the file has already been moved, re-running it again won't copy it again unless the source file is newer than the target file.

rsync is one of the most amazing tools available.  There is a GUI for it, but I've never used it.

I've used teracopy. Pretty much any Linux file manager does the same thing as far as I can tell.  Just open 2 instances - one in the target area and use the other to drag-in-drop files there. They should be queued.  I don't do this much, since rsync is easier and faster for me.  Of course, I'm not a typical desktop user, so others could find rsync difficult.

[http://ultracopier-wiki.first-world.info/](http://ultracopier-wiki.first-world.info/) seems to be an alternative.  I've never heard/used it. Doesn't appear to be in the repos. Building from source seems to be necessary. Get source here: [https://github.com/alphaonex86/Ultracopier](https://github.com/alphaonex86/Ultracopier)  Looks like this was formerly known as SuperCopier.

---

### Post by ajgreeny on 2017-02-18
I think TherFu is right about **rsync** which should be able to do what you want easily; in fact even the copy command **cp** could do it, I think, but has fewer options than rsync.

The application **grsync** is a very good GUI alternative to rsync but again does not have quite so many detailed options as the cli way; it should, however, be able to handle what you want to do very easily.

---

### Post by dragonfly41 on 2017-02-18
grsync is rsync with GUI

---

### Post by vanadium on 2017-02-18
> **TheFu said:**
> Pretty much any Linux file manager does the same thing as far as I can tell.  Just open 2 instances - one in the target area and use the other to drag-in-drop files there. They should be queued.
They are not queued but run in parallel instead, and unfortunately there is no control over this. Apart from that, I also would recourse to rsync for such task.

---

### Post by dragonfly41 on 2017-02-18
There is another option I remember .. luckyBackup
This GUI uses rsync and you can define tasks which I guess are similar to queues.
Looking at luckyBackup (superuser) you can add a task, go to advanced and drag files into the window.
You can also do dry runs.

---

### Post by k0tt0n on 2017-02-18
thanks for the reply guys, but it all seems to be way too much work compared to just a simple drag and drop like windows programs do. having to go though all the steps of target and destination etc for every album folder is just way too time consuming when I have about 100 albums from different directories to move. I just want to drag album folders into a queue and when I'm done start the transfer.

---

### Post by dragonfly41 on 2017-02-18
For *any *such tool you will need to specify source and target .. possibly only for the first time
to define a profile.
As I explained you can  drag files into luckyBackup then hit go.
There are other tools which do the same job.
If you use Krusader then that does a good job too.

Read Krusader queue manager here ... [https://docs.kde.org/trunk5/en/extragear-utils/krusader/basic.html](https://docs.kde.org/trunk5/en/extragear-utils/krusader/basic.html)

---

### Post by k0tt0n on 2017-02-18
> **dragonfly41 said:**
> For *any *such tool you will need to specify source and target .. possibly only for the first time
to define a profile.
As I explained you can  drag files into luckyBackup then hit go.
There are other tools which do the same job.
If you use Krusader then that does a good job too.

Read Krusader queue manager here ... [https://docs.kde.org/trunk5/en/extragear-utils/krusader/basic.html](https://docs.kde.org/trunk5/en/extragear-utils/krusader/basic.html)

Decided to use Krusader. Managed to get a queue of about 90 cds setup, then started the transfer only to have it freeze after about 5 minutes. Went through the whole tedious process again and again it froze up. Tried a 3rd time and same thing. Went to the wife's windows 10 laptop, downloaded supercopier, dragged and dropped what I wanted and was done in 10 minutes.

---

### Post by Skaperen on 2017-02-19
running rsync at the command line would have explained the failure to some degree, depending on the cause. to do things at the command line you would need to know the paths for relevant folders and devices.  most people are afraid of command line and won't go there. most GUI tools don't give detailed error message since most users don't understand those details.

---

### Post by k0tt0n on 2017-02-19
> **Skaperen said:**
> running rsync at the command line would have explained the failure to some degree, depending on the cause. to do things at the command line you would need to know the paths for relevant folders and devices.  most people are afraid of command line and won't go there. most GUI tools don't give detailed error message since most users don't understand those details.

it's not that I'm afraid of the command line, it's just there were so many folders within other folders that using the command line would have taken forever. drag and drop is just so much easier and time efficient.

---

### Post by TheFu on 2017-02-19
> **k0tt0n said:**
> it's not that I'm afraid of the command line, it's just there were so many folders within other folders that using the command line would have taken forever. drag and drop is just so much easier and time efficient.

I would disagree, but I'm comfortable at the command like.

Need a list of all the directories from here down?
$ find . -type d > /tmp/dir.list

Quickly edit that list to what you want (or don't want). Feed that into rsync with include/exclude options.  Done.
--exclude-from=FILE     read exclude patterns from FILE
--include-from=FILE     read include patterns from FILE

Probably would take 3 minutes for me.  This is how I handle doing the exact thing you are trying to accomplish.  For me, it is how I move music onto portable devices over the network.

But we each have different backgrounds and needs. Happy you found a solution that seems to work without too much hassle.

---

### Post by ajgreeny on 2017-02-19
> **k0tt0n said:**
> it's not that I'm afraid of the command line, it's just there were so many folders within other folders that using the command line would have taken forever. drag and drop is just so much easier and time efficient.
I think you are totally missing the way rsync works, and how easy it is to use. Unless you tell it otherwise rsync will move files and folders recursively without changing the folder structure, no matter how deeply the folders are stacked.  If you had re-recorded or ripped some of your music CDs only those new files would be moved next time you run that rsync session and any files that are still identical to the old version would be ignored.

If there are some folders that you do not want moved you can easily tell it to exclude that folder.

If you use grsync you can set it to show the actions taken in a verbose manner so you get the same errors shown as if you used the command line, and you can also setup and save various Sessions, ie different sources and destinations depending on what you're doing, which means it is a simple click in the window to choose that session and away you go.

What could be simpler than that and what could do the job quicker and more easily?

---

### Post by dragonfly41 on 2017-02-19
> [COLOR=#000000][INDENT]The application **grsync** is a very good GUI alternative to rsync but again does not have quite so many detailed options as the cli way; it should, however, be able to handle what you want to do very easily.

Note with grsync (the GUI) you can, if you wish, include raw rsync (or other) commands in the "Extra Options" tab. 
This surely offers the best of both worlds - GUI and CLI.[/INDENT]
[/COLOR]

---

### Post by k0tt0n on 2017-02-20
> **TheFu said:**
> I would disagree, but I'm comfortable at the command like.

Need a list of all the directories from here down?
$ find . -type d > /tmp/dir.list

Quickly edit that list to what you want (or don't want). Feed that into rsync with include/exclude options.  Done.
--exclude-from=FILE     read exclude patterns from FILE
--include-from=FILE     read include patterns from FILE

Probably would take 3 minutes for me.  This is how I handle doing the exact thing you are trying to accomplish.  For me, it is how I move music onto portable devices over the network.

But we each have different backgrounds and needs. Happy you found a solution that seems to work without too much hassle.

Thanks for the tips. Appreciated





> **ajgreeny said:**
> 

What could be simpler than that and what could do the job quicker and more easily?

Drag and drop into a file queue

---

