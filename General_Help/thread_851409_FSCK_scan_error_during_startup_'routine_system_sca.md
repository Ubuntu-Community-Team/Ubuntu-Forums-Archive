---
title: "FSCK scan error during startup 'routine system scan' - please help!"
date: 2008-07-06
forum: General Help
---

### Post by Pipps on 2008-07-06
**Summary**
Error during routine system scan.

**When did it happen?**
During the system startup procedure at the 'Ubuntu' orange and black splashscreen.

**What happened?**
A small message at the bottom read 
"Routine scan of /dev/shm/root - x% complete."

Then after a minute or two, I received the following page of white text on a black screen. I took a photo of it and have copied it out verbatim.

> /dev/shm/root: UNEXPECTED INCONSISTENCY: Run fsck MANUALLY.
		- (i.e. without -a or -p options)
fsck died with exit status 4
checking drive /dev/shm/root: 93% (stage 4/5, 50/105)

An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash:  no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolours: command not found
bash: Command: command not found
bash: The: command not found
root@rp-laptop:~#_

At this point, I typed 'exit' <CR>

The system restarted. I loaded ubuntu and pressed <ESC> at the system scan and it loaded normally.

**My question**
What should I do to resolve this problem?

Please help! :confused:

---

### Post by VMC on 2008-07-06
It sounded like you didn't preform the steps suggested:

> The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolours: command not found
bash: Command: command not found
bash: The: command not found
> root@rp-laptop:~#_
At this point, I typed 'exit' <CR>

Can you type in the fsck at the prompt "#"

---

### Post by Pipps on 2008-07-07
Thanks for your help. I let the scan run at startup again and did as you suggested. I was then presented with the following prompts:

> /host/ubuntu/disks/root.disk contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks and sizes
Inode that were part of a corupted orphan list found. Fix(y)?
In bewilderment, I hit 'y', as it seemed that Ubuntu was trying to do something nice for me.

> Inode 353947 was part of the orphaned inode list. FIXED.
Inode 353966 was part of the orphaned inode list. FIXED.
Inode 353975 was part of the orphaned inode list. FIXED.

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 409457
Connect to /lost+found(y)?
I hit 'y'.

> Inode 409457 ref count is 2, should be 1. Fix(y)?
I hit 'y'.

> Inode 411406 ref count is 1, should be 2. Fix(y)?
I hit 'y'.

> Unattached inode 750789
Connect to /lost+found(y)?
I hit 'y'.

> Inode 750789 ref count is 2, should be 1. Fix(y)?
I hit 'y'.

> Unattached inode 751470
Connect to /lost+found(y)?
I hit 'y'.

> Inode 751470 ref count is 2, should be 1. Fix(y)?
I hit 'y'.

> Pass 5: Checking group summary information
Block bitmap differences: -(1419345--1419347) -(1423962--1423969) -(1431397--1431404)
Fix(y)?
I hit 'y'.

> Free blocks count wrong for group #43 (8641, counted=8660).
Fix (y)?
I hit 'y'.

> Free blocks count wrong (2290571, counted=2290590).
Fix(y)?
I hit 'y'.

> Inode bitmap differences: -253074 -255983 -(255997--255998) -353947 -353966 -353975
Fix(y)?
I hit 'y'.

> Free inodes count wrong for group #31 (4755, counted=4799).
Fix(y)?
I hit 'y'.

> Free inodes count wrong for group #43 (4713, counted=4716).
Fix(y)?
I hit 'y'.

> Free inodes count wrong for group (714944, counted=714951).
Fix(y)?
I hit 'y'.

> /host/ubuntu/disks/root.disk: ***** FILE SYSTEM WAS MODIFIED *****
/host/ubuntu/disks/root.disk: ***** REBOOT LINUX *****
/host/ubuntu/disks/root.disk: 141849/856800 files (0.7% non-contiguous),1127378
/3417968 blocks
root&rp-laptop:~#_
At this point, I typed exit.

Ubuntu rebooted. There was no automatic system scan. The boot appeared to have been completed successfully.

**My questions**
1. What caused all of these problems?
2. Was I correct to hit 'y' at the prompts in an attempt to fix the problems?
3. Have the problems now really been fixed, or should I most likely expect further related problems in the future?

I look forward to your advice. Thanks.

---

### Post by Pipps on 2008-07-07
Any thoughts, anyone?

---

### Post by dentaku65 on 2008-07-07
> **Pipps said:**
> Thanks for your help. I let the scan run at startup again and did as you suggested. I was then presented with the following prompts:
At this point, I typed exit.

Ubuntu rebooted. There was no automatic system scan. The boot appeared to have been completed successfully.

**My questions**
1. What caused all of these problems?
2. Was I correct to hit 'y' at the prompts in an attempt to fix the problems?
3. Have the problems now really been fixed, or should I most likely expect further related problems in the future?

I look forward to your advice. Thanks.

1. Who knows? Maybe some black-out or hard reboot or some custom strange installation?
2. Yes, the "-y" option in fsck command is used to fix errors on trouble hard drive (man fsck)
3. The problem has been fixed I supposed

---

### Post by bodhi.zazen on 2008-07-07
> **Pipps said:**
> Any thoughts, anyone?

1. Always run fsck with the target partition UNMOUNTED, in the case of / this means a live CD.

2. ```
fsck -rfv /dev/sdxy
```

where "sdxy" is the partition to check, this way you do not have to keep typing in "y"

:lolflag:

Why ? gremlins

---

### Post by Pipps on 2008-07-08
Ok, I suppose it must just be one of those things.

Thanks for the help and support anyway. I'm glad it's resolved.

---

### Post by mafaldaspeaks on 2008-08-12
I was having exactly the same problem. I followed this thread and voila! now I'm able to log in again! Thanks for posting and for those who replied to pipps!

---

### Post by gabo.cr on 2008-08-15
Hello
I'm reading this post a little late.
I have the same problem but I just ran **fsck**.
I said yes to all the questions and then the system rebooted without being able to load Edubuntu graphics. It is saying that it was not able to load the theme and default theme. I'm getting a window where I can type the username and password under Gnome but  then I get an orange screen and nothing happens.

What should I do now?

---

### Post by gabo.cr on 2008-08-16
I reinstalled everything and now is working just fine.
:)

---

### Post by Scunge on 2008-08-29
> **bodhi.zazen said:**
> 2. ```
fsck -rfv /dev/sdxy
```

where "sdxy" is the partition to check, this way you do not have to keep typing in "y"

Can I check this?

According to "man fsck", ```
       -r     Interactively  repair  the  filesystem  (ask for confirmations).
```

So surely you mean ```
fsck -yfv /dev/sdxy
``` so that fsck will ```
       -y     For  some filesystem-specific checkers, the -y option will cause
              the fs-specific fsck to  always  attempt  to  fix  any  detected
              filesystem corruption automatically.
              ...
``` assuming it allows it.

And a question.

I had to do a manual fsck but ran only with options "-fv", and hence it asked me about all sorts of things with inodes and duplicate blocks and all sorts of stuff like was seen by the OP, which frankly I have no idea whether pressing "y" was the right thing to do.

Is there any circumstance (easily explained) where entering "n" is the correct course of action, i.e. what sort of fixes should I not let it do. Put another way, is there any reason for me **not** to run with the "-y" option?

Ok, another question.

If the "-y" option doesn't work for me, as it advises in the "man fsck" entry is a possibility, is this right to get the same effect? ```
fsck -fv /dev/sdxy < yes
```

Thanks.

---

### Post by smokey_58au on 2008-09-01
> **bodhi.zazen said:**
> 1. Always run fsck with the target partition UNMOUNTED, in the case of / this means a live CD.

2. ```
fsck -rfv /dev/sdxy
```where "sdxy" is the partition to check, this way you do not have to keep typing in "y"

Thanks for this info, I was able to recover from the error although as Scunge mentioned, it still asked for the "y" prompt (I didn't see his suggestion to replace "r" with "y" until after I had done it). I just said yes each time and my system now reboots and works perfectly.  Thanks again for everyone's input.

---

