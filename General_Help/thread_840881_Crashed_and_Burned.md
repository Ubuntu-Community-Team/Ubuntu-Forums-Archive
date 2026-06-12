---
title: "Crashed and Burned?"
date: 2008-06-25
forum: General Help
---

### Post by smkoberg on 2008-06-25
Earlier today I was on my laptop running Ubuntu and she killed herself. 

I tried rebooting. When I get to the splash screen with the ubuntu logo and the progress bar, the progress bar reaches about 20-25%  and it freezes with this message below:

```
Routine check of Drivers /dev/sda1
Press ESC to skip

2% (stage 1/5, 23/577)
```

If I let it sit for a minute I get the following: 

```
Checking drive /dev/sda1: 2% (stage 1/5, 23/577)
Error reading block 753829 (Attempt to read block from filesystem resulted in short
read) while getting next inode from scan. 

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
 (i.e., without -a or -p options)
fsck died with exit status 4

*An automatic file system check (fsck) of the root filesystem failed. 
A manual fsck must be performed, then the system restarted. 
The fsck should be performed in maintenance mode with the 
root filesystem mounted in read-only mode. 

*The root filesystem is currently mounted in read-only mode. 
A maintenance shell will now be started. 
After performing system maintenance, press CONTROL-D 
to terminate the maintenance shell and restart the system. 
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not ofund
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@seth-laptop:~#
```

I WAS going to try and put the ubuntu disk in and try to run from that and fix any errors (if it would allow it), but SOMEBODY decided to install Ubuntu on their desktop and keep the CD. 

So not only can I not possibly fix errors through the CD, I can't do a fresh install without having to download again. 

Any ideas on how I can fix this, preferably without having to do a fresh install and lose all my stuff?

---

### Post by dominiquec on 2008-06-25
I'd guess that you have a physical problem with your hard drive.  Have you got your backups made?  That's the first thing I'd do, and for that you probably need a boot disk.

You can try fixing the problem, though, by running fsck manually.  From where you are, run fsck /dev/sda1.  You'll have to sit and monitor it as it prompts you about bad blocks.

---

### Post by smkoberg on 2008-06-25
Okay, now I'm completley confused. 

after I got that message I shut down my laptop and waited a while for a responce (which came rather quickly, thank you), so I rebooted to try your suggestion and it booted with no problem. 

Any ideas now on what I could do now to keep this from happening again?

---

### Post by VMC on 2008-06-25
> **dominiquec said:**
> I'd guess that you have a physical problem with your hard drive.  Have you got your backups made?  That's the first thing I'd do, and for that you probably need a boot disk.

You can try fixing the problem, though, by running fsck manually.  From where you are, run fsck /dev/sda1.  You'll have to sit and monitor it as it prompts you about bad blocks.

Make sure you run that fdisk command from a "live cd" and not from a live system that is already mounted.

---

### Post by mattman85 on 2008-07-13
> **smkoberg said:**
> Earlier today I was on my laptop running Ubuntu and she killed herself. 

I tried rebooting. When I get to the splash screen with the ubuntu logo and the progress bar, the progress bar reaches about 20-25%  and it freezes with this message below:

```
Routine check of Drivers /dev/sda1
Press ESC to skip

2% (stage 1/5, 23/577)
```

If I let it sit for a minute I get the following: 

```
Checking drive /dev/sda1: 2% (stage 1/5, 23/577)
Error reading block 753829 (Attempt to read block from filesystem resulted in short
read) while getting next inode from scan. 

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
 (i.e., without -a or -p options)
fsck died with exit status 4

*An automatic file system check (fsck) of the root filesystem failed. 
A manual fsck must be performed, then the system restarted. 
The fsck should be performed in maintenance mode with the 
root filesystem mounted in read-only mode. 

*The root filesystem is currently mounted in read-only mode. 
A maintenance shell will now be started. 
After performing system maintenance, press CONTROL-D 
to terminate the maintenance shell and restart the system. 
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not ofund
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@seth-laptop:~#
```

I WAS going to try and put the ubuntu disk in and try to run from that and fix any errors (if it would allow it), but SOMEBODY decided to install Ubuntu on their desktop and keep the CD. 

So not only can I not possibly fix errors through the CD, I can't do a fresh install without having to download again. 

Any ideas on how I can fix this, preferably without having to do a fresh install and lose all my stuff?



I get the same thing.  It just started about a day and a half ago...  It says its doing the routine check of /dev/sda3...  gets to about 25% and then freezes, and the line with the % done, and the stage number start screwing up.  Half the numbers start jumping to other areas of the screen.  I'm pretty sure that it isn't a physical issue, since I keep my laptop on my computer desk, and I shut the laptop down regularly..  Any ideas, aside from FDISK, which I will do in a bit.


EDIT:: FDISK showed that everything was fine, so I'm a little confused.

---

### Post by mattman85 on 2008-12-10
I realized that I never updated my reply to this thread...  after upgrading to hardy, everything was fine.  I haven't run into any issue like this yet...

---

