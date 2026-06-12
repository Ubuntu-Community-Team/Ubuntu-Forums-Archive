---
title: "file access time"
date: 2017-03-06
forum: General Help
---

### Post by r.stiltskin on 2017-03-06
I was looking at some of my home directory file properties entries in thunar and noticed that the Accessed time for some of them seemed odd, so I ran

**ls -lt --time=atime**

and I see a group of 18 files with an access time of 20:52 last night and a group of directories with access time of 07:39 this morning.  I'm certain that I didn't open any of those files at those times, and nobody else uses this computer.  I ran

**stat -c %F,%n,%x  ***

to see the times with more precision and within each group most have exactly the same time, e.g. 2017-03-05 20:52:45.822843143 -0500 and the rest differ by less than 0.2 seconds.

So, now I'm running 
**inotifywait -mr -eaccess ***
in my home directory and watching the output, and it appears sensible - an output is issued each time I cat a file in another terminal, or open one with nano, etc.   There are no unexpected accesses showing up.  And there are no worrisome entries in /var/log/auth.log.  And **who** reports only me.

On the other hand, the outputs from **stat -c %F,%n,%x  *** don't seem to change -- I just ran **stat** again and the access times it shows for the files that I've been opening with cat and nano are exactly the same times it showed before.

What's going on?  Why don't these access times seem to make sense?

---

### Post by &amp;KyT$0P# on 2017-03-06
My first thought would be, maybe the cron job for updating the [FONT=Courier New]locate[/FONT] database?

See what gets accessed when you run this -
```
sudo updatedb
```

---

### Post by r.stiltskin on 2017-03-06
I ran sudo updatedb and then rechecked file access times and didn't find any that changed.

And while looking again at the directories that show access time of 07:39 this morning, I realized that all of the files in those directories show access times of 20:53-20:54 last night (all within 2 seconds of the access time of the ordinary files in my home dir.

---

### Post by r.stiltskin on 2017-03-07
Mystery solved.

After examining more files it turned out that every single regular file in my home directory tree had the same atime of Mar  5 20:52, except for a few files that I know I used more recently.  And, every single directory in my home directory tree had the same atime of Mar  6 07:39, except for a few that I entered more recently.  Until this morning, when suddenly all the directories had a new atime Mar  7 08:01 but the regular files, except for a few, still hadn't changed.

So, I'm not certain exactly what I did at 8:01 this morning but since I was still puzzling over this, I probably ran **ls** on my home directory or opened thunar at that moment.  I finally realized that this all must be due to the relatime mounting of the partition.  File reads are changing the atime only once in a 24 hour period unless the file has been modified in that period.

But the mystery remained, why did _all_ the regular files at every level in this directory tree have the same atime?  After pondering this for a while it finally occurred to me to review my .bash_history and DUH ... the night of Mar 5 I was searching to see if  term 'ulimit' appeared in any of my config files and I ran **grep -r ulimit *** and then realized that wouldn't check any hidden files so I ran **grep -r ulimit .*** so I literally opened every regular file in the tree.

No evil hackers -- just one dummy.

---

