---
title: "Disk Full - Help!?"
date: 2007-07-03
forum: General Help
---

### Post by casperlingus on 2007-07-03
OS:  Ubuntu 7.04
System:  Dell Precision M90

I am writing this from windows because Ubuntu will no longer even let me log in.  

Yesterday, I knew I had about 2 GB free space on my main drive. Today I get into work and find out I can't save any of my work, and all sorts of things were breaking.   I got a "Disk full" error.  This isn't right, a "df" gave me something like this:

[FONT="Courier New"]
Device  Mounted         type         Blocks             Used            Avail
/dev/sda3        /                       ext3      15000001      15000000       0%
[/FONT]

My HDD filled up overnight and I have no idea what it's filled with.  This isn't the first time this has happened either.  This happened previously and I ended up reinstalling my OS.  I suspect that a program went crazy, filled up the swap, and then filled up every free byte of disk space.  However, the two times this has happened I had two completely different things going.

First time:   I left "neverball" running over night.  I think I had a spreadsheet open as well (most likely MS Excel using Crossover Offfice).   I *was not* connected to the internet.
This time:  I had a ton of stuff running:  Evolution, OO Word, many xterms running vim, a few firefox instances, probably others I can't think of, and I *was* connected to the internet.

Last time, I know I had 7 GB free space, and I went through nearly every top- and second-level directory adding up usage, and found that I should've had about 7 GB free -- I couldn't find the data that was filled, so I couldn't delete it.  Same thing now.   This is so frustrating!

Is this a known bug?  What can I do?  I am about to burn a live CD and back up my stuff, but I'd like to not have to reinstall... Thoughts???

-Casper

---

### Post by casperlingus on 2007-07-03
verucabong wrote about a nearly identical-sounding problem, but claimed that var/log/cups folder was the problem.  That does not appear to be my problem.  

I was not previously aware of baobab.  I just booted into a kubuntu live CD (I run gnome, but all I had on hand was kubuntu) and I installed baobab and used it on my disk.

It tells me that /dev/sda3 only has 5.4 GB of used space, despite being a 15 GB HDD at 100% usage.  The 5.4GB sounds about right to me.  /usr is about 3.8 GB and my /home is about 1.0 GB.  (Apparently for the past two months there has been ghost data filling 7GB of my disk, but I didn't realize it until today when it filled up the rest)

What is going on here??  How can the OS fill up 9-10 GB of space, tell me that it's full, but not let me get to it to delete it??  Is there a utility I can use??

---

### Post by bodhi.zazen on 2007-07-03
boot with a live CD

Mount your ubuntu partition

Look for what is filling your disk.

Check ~/.Trash and /root/.Trash

Check your logs.

To see disk usage use du :

See if this helps at all : [http://www.linux.com/articles/51600?theme=print](http://www.linux.com/articles/51600?theme=print)

---

### Post by casperlingus on 2007-07-03
Okay, I found the problem.

I saw that my *Simple Backup* directory had 8.9GB, but that is on an external HDD... or so I thought...

It turns out that my external HDD wasn't auto-mounted at the last boot, b/c there was a power outtage the day before which turned off the drive,  So my computer started doing full backups (to an unmounted sbackup directory) of a 20 GB partition to my main drive which only had 10 GB left.  

It's unfortunate that I couldn't see that before.  When you run "du" there's no way to tell that the directory is not mounted when it should be.  I can't think of a way around that, just experience, I guess.

-Casper

---

