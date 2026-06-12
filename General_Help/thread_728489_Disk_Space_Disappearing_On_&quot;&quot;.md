---
title: "Disk Space Disappearing On &quot;/&quot;"
date: 2008-03-18
forum: General Help
---

### Post by ogron on 2008-03-18
Strange things have been happening in my "/" folder... it's 16.5 GB but the amount of free space left varies wildly, seemingly at random, and it's starting to become a big problem.

At one point I got the "your session lasted less than 10 seconds" message when trying to log in, and had to log in via terminal and delete some programs first. The problem that time turned out to be large crash logs in /var/crash - which I deleted. The free space on "/" went up to 134MB. A week later, it miraculously went up to 258MB without me deleting anything else - "ok" I thought, and carried on.

Today it's suddenly standing at 34MB. There are no crash logs in /var/crash, I have cleaned everything up as best as possible, and I can't find any new 200MB+ files in my "/" directory. This is a dangerously small amount of space, and I wondered if anyone could help me sort it out. 

Why might over 200MB suddenly have disappeared from "/"? And where can I find the file(s) that have done it, and delete them? I'd really appreciate any help.

(Incidentally, I'm still using Edgy if that makes any difference)

---

### Post by ajmorris on 2008-03-18
does your /tmp folder contain anything? Perhaps it is not being cleaned regularly

---

### Post by ogron on 2008-03-18
No, tmp is empty (should have mentioned that, sorry).

I've also run autoclean, etc.

---

### Post by ajmorris on 2008-03-18
do you have tracker enabled? Tracker is a utility that indexes files, you can see if indexing is turned on through here: System->Preferences->Indexing Preferences

---

### Post by unutbu on 2008-03-18
Perhaps do this:
```

du . | sort -nr | head -n 100 > 2008-03-18-du.log

```

Each day run this and save the output in a new file.
You can use then use emacs ediff (or any diff tool you like) to see where all the bytes are going.

The above command saves the du output for the top 100 largest directories.
I'm guessing that should catch the culprit, but if not you might have to increase that number.

---

### Post by ogron on 2008-03-18
> **ajmorris said:**
> do you have tracker enabled? Tracker is a utility that indexes files, you can see if indexing is turned on through here: System->Preferences->Indexing Preferences

Apparently my home folder is being indexed, nothing else. Should I add additional paths?

---

### Post by ogron on 2008-03-18
> **unutbu said:**
> Perhaps do this:
```

du . | sort -nr | head -n 100 > 2008-03-18-du.log

```

Each day run this and save the output in a new file.
You can use then use emacs ediff (or any diff tool you like) to see where all the bytes are going.

The above command saves the du output for the top 100 largest directories.
I'm guessing that should catch the culprit, but if not you might have to increase that number.

Thanks... but when I ran this, I just got a long wait then finally this output: 

du: `./gsopcast-0.2.10/src': Permission denied

Nothing else. That can't be right... can it?

---

### Post by unutbu on 2008-03-18
Sorry, the command should have been 
```

du / | sort -nr | head -n 100 > ~/2008-03-18-du.log

```

This command might take a long time, and there might be a few errors related to directories you don't have permission to read as a normal user. If you feel the problem might be in one of those directories, you may have to put 'sudo' in front of the command. 

When the command is done, you'll get the log file in your home directory and it will be called '2008-03-18-du.log'.

---

### Post by ogron on 2008-03-19
Thanks. I studied the log. Nothing leapt out. 

Obviously, the largest directory on the / partition is /usr, which is just under 3GB.  /var is the next largest at 230M. That leaves 17 other directories, all apparently smaller than 230M, some of them only containing a few bytes. I'm not sure how I've managed to fill a 16.5GB partition, in that case - although I know very little about partitioning generally, and it's possible some of that space is in use somewhere else (a friend did the partitioning for me, some time ago). This is one area where I'm still effectively a complete newbie... which might be why I can't locate the problem here.

Anyway, somehow this 200mb of free space that's vanished from my slash partition overnight doesn't appear to have gone anywhere - at least it doesn't all seem to have gone to the *same* place, because there aren't any directories over 200MB except /usr and /var. I'm really stuck now. Is there anywhere in these directories (other than /var/crash) where I should look for crash logs or any other large files that could be causing the problem - or could be deleted, at least?

---

### Post by ajmorris on 2008-03-19
you could try running ```
sudo apt-get clean
``` also, you might like to check ~/.trash. Also, you can un-index your home partition if you like, although, i doubt it will make that much of a difference.

---

### Post by unutbu on 2008-03-19
Backup. Then you can delete some more stuff and then try to solve this problem without being in danger of painting yourself into a corner.

---

### Post by ogron on 2008-03-19
Thanks everyone. Still looking into this - I've done all the things suggested, none has made any difference. My / partition  is still only showing 34mb free space, for no apparent reason.

Frustratingly, I have 7GB free in my home folder, and I could easily spare one of them. I might have to take a crash course in partitioning (or get someone else to do it) and re-allocate 1GB, if nothing else works out... but right now I'm still determined to find out where all that space has gone.

---

### Post by kidders on 2008-03-20
Hi guys,

As I was reading this thread, it occurred to me that it surely isn't a good idea to be running an OS with only 1% free space on its root filesystem. Small amounts of space like that can appear & disappear for a variety of reasons, for instance...[LIST]
[*]Log files being compressed as they're rotated.
[*]Caches, temporary data, state information & so on being created & deleted in dotfiles/dotdirs, /tmp, /var and other places.
[*]Filesystem fragmentation.
[/LIST]

Imo, there's unlikely to be one individually identifiable cause that can be rectified with an **rm -R ...** Also worth noting is that the amount of free space on a filesystem does not equal the total capacity minus the amount of used space. Especially after a lot of use, the difference can be significant, and will tend to get even bigger as a filesystem starts to get full.

Anyhow, rather than pulling your hair out chasing after a couple of hundred megabytes, I would suggest just chalking it up to normal bloating, and maybe re-evaluating your partitioning scheme. Unfortunately, that's kind of a big job, so in the meantime, how about...

Pick something sizable (but maybe not *too* large) that's not critical to the boot process. Pitch for about 20 or 25% of the size of your root filesystem ... depending on your usage, the contents of /var, /usr/local or /opt might be suitable candidates. Taking /opt as an example, if you were to do **mv /opt /home && ln -s /home/opt /opt**, you'd gain back all the space it took up, and your Ubuntu would be none the wiser. Naturally, you wouldn't want to be doing something like that with any applications running though (eg Xorg).

Longer term, if you happen to have some unallocated hard disk space, one easy solution could be to create a /usr partition. Failing that, you're left with backing everything up and resizing or recreating partitions.

---

### Post by ogron on 2008-03-20
Problem solved.

I had two data directories that seemed to be mounted on the root partition, but weren't - it turned out that one of them actually was (confusion stemming from the fact that the other one wasn't). This explains the missing 12G or thereabouts. D'oh.

Ended up shifting a couple of gigs from there into the /home folder, and hey presto, lots of free space in /. As I had begun to suspect, there was a simple answer here that I was missing purely because someone else partitioned the hard drive and I couldn't remember exactly what was what. Time for me to fill that gap in my knowledge, I think.

Thanks for all the help, though, I've learned a few new things, so it's been very useful.

> **kidders said:**
> it surely isn't a good idea to be running an OS with only 1% free space on its root filesystem. Small amounts of space like that can appear & disappear for a variety of reasons, for instance...[LIST]
[*]Log files being compressed as they're rotated.
[*]Caches, temporary data, state information & so on being created & deleted in dotfiles/dotdirs, /tmp, /var and other places.
[*]Filesystem fragmentation.
[/LIST]

This is something I've come to understand, and have taken to heart. Next step: buying a nice new 500GB HD, so that after a fresh install I can have everything arranged sensibly, and not end up poaching space like this...

---

