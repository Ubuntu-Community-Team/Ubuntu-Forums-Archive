---
title: "Disk Space Analyser Misreporting Disk Full?"
date: 2013-04-09
forum: General Help
---

### Post by Bearly Able on 2013-04-09
After I did this morning's updates, Disk Space Analyser popped up with a message that my hard drive is almost full.  I can't see how that's possible; I have a 1TB hard drive, with not much more on it than I had on my previous system with a 160GB hard drive, and I never ran into problems then.

I did the obvious, and deleted old Linux kernels, etc., but it's made no difference.  Disk Space Analyser says I have used 925.2GB and have 55.1GB free space.  I'd expect it to be pretty much the opposite - and adding up the figures from DSA's breakdown accounts for only around 50-odd GB of usage.  Is DSA misreporting - in which case, can I do anything to correct it? - or am I misunderstanding something here?

---

### Post by Cheesemill on 2013-04-09
Can you post the output of...
```
cd /
sudo du -h --max-depth=1 | sort -hr
```

This will list the content size of all of the directories in you root directory sorted by size.

I suspect that you may have a runaway log file that is taking up all of your space, but post back with the output of the above commands and we'll take it from there.

---

### Post by Bearly Able on 2013-04-09
Thanks for the reply.  Here it is:

```
du: cannot access `./home/lesley/.gvfs': Permission denied
du: cannot access `./proc/3225/task/3225/fd/3': No such file or directory
du: cannot access `./proc/3225/task/3225/fdinfo/3': No such file or directory
du: cannot access `./proc/3225/fd/3': No such file or directory
du: cannot access `./proc/3225/fdinfo/3': No such file or directory
1.3T	.
819G	./root
408G	./media
36G	./home
5.3G	./usr
955M	./var
397M	./lib
49M	./boot
18M	./etc
8.7M	./bin
8.6M	./sbin
3.4M	./lib32
1.3M	./run
904K	./opt
84K	./tmp
16K	./lost+found
4.0K	./srv
4.0K	./selinux
4.0K	./mnt
4.0K	./lib64
4.0K	./dev
0	./sys
0	./proc
```The reason for the discrepancy in size between this and the previous screenshot is that I have a 500GB external hard drive plugged in now.  I'd disconnected it earlier, to see if it would make any difference to the analyser results as the external dive really *is* 80% full, but no joy.

---

### Post by Bearly Able on 2013-04-09
Problem solved, thank you. 

I realised from the above that the problem was mine, not the Disk Analyser's. I finally tracked the culprit down to a trash folder full of deleted backups in .local/share.

---

