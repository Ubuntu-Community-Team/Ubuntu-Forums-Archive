---
title: "Dead Again"
date: 2007-04-15
forum: General Help
---

### Post by phoenixfirebird on 2007-04-15
Once again, my Ubuntu (Feisty) seems to have died.  I didn't change anything that I'm aware of, but it was working great this morning and now it won't even boot up!  Here is the error message I recieved while trying to boot:

```
/dev/hda7: UNEXPECTED INCONSISTENCY, RUN fsck MANUALLY
(i.e., without -a or -p optons)
fsck died with exit status 4
[RIGHT][fail][/RIGHT]
*An automatic file system check (fsck) of the root file system failed . A manual fsck must be performed, then the system restarted.  The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem in currently mounted in read-only mode.  A maintenance shell will now be started.  After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed.  You can install it by typing: apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found
The program 'apt-get' is currently not installed.  You can install it by typing: apt-get install apt
bash: apt-get: command not found
```

This is not the first time this has happened, but I have no idea what I can do.  I really don't want to re-install Ubuntu AGAIN, as this is the second time this has occured.  What causes this, and what can I do to fix it/'prevent it?  Thanks

---

### Post by dfm21 on 2007-04-16
seems like your filesystem is corrupt.
If you did not change anything, then maybe your HD is broken.
fix: buy a new one...

---

### Post by Death_Sargent on 2007-04-16
Use edgy or dapper 

Fiesty is not finished yet and really should not be used as a primary OS.

---

### Post by ubukool on 2007-04-20
Hi,

You have to do a manual fsck.  This happened to me this morning too, so at this point you type 'fsck' at the command prompt and just follow what it says.  Answer 'yes' to the questions and see where it gets you.  My system is now back up and running again, so don't give up hope.

---

### Post by justmoon on 2007-04-28
Exactly the same problem here. Feisty Fawn final. Very strange. I updated Ubuntu on my highly customized system without any problems, then encouraged my mum to update too. She has pretty much a default install on an off-the-shelf system and she got this. -_-

fsck is currently running... first she read every message one by one (I have to instruct her over the phone as I'm out of the country), after a while she pressed Enter herself and as I'm writing this she's keeping Enter pressed as the error messages are running through. 
Error reading block 18219165 (attempt to read block from file system resulted in short read) while doing inode scan. Ignore Error <y>?
Force rewrite <y>?

And in between:
[ 2033.411299] Buffer I-O Error on device fda1, logical block 18186662

Is this normal? The hard drive never showed the slightest of problems and the partitioning was done automatically by the Ubuntu Dapper installer one year ago (fresh install on an empty drive).

And why the hell fda1? The floppy drive is empty and not doing anything.

---

### Post by LoneSt4r on 2007-04-29
Hello!

This is my first post in the forums. :)  I have been testing Ubuntu on my older PC for a couple of weeks and I loved it.

This problem happened to me too last night.  I tried installing Ubuntu on my main machine as OS#2, but with too small partitions it seems (8Gb / and 8Gb /home).  I was then unable to log into my account.

I booted back in WindowsXP where I used Partition Manager to enlarge the two Ubuntu partitions.  After touching each one, I received the warning "Update LILO".

Now, I get this error when trying to boot Linux.  Is the fsck command is 100% guaranteed to bring back my system?  If not, what steps should I take?

Ultimately, I will move my files from Windows to Ubuntu and perform the same operation again.  How should I proceed to do this "by the book"?

Thanks!

---

