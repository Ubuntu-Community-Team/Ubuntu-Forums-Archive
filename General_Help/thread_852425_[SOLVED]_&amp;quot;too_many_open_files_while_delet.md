---
title: "[SOLVED] &amp;quot;too many open files while deleting...&amp;quot; when trying to empty trash"
date: 2008-07-07
forum: General Help
---

### Post by Afkpuz on 2008-07-07
I am trying to empty my trash bin, but I get the error I listed in the title of this thread.  "Too many files open while deleting [anything]"  I searched around on the forums a little and got linked to threads about torrent problems.  I actually just got done downloading something from a torrent and wonder if it's related.  I downloaded a large file with multiple folders in it, so I broke them up and think that might have something to do with it.  Anyone have any advice?

---

### Post by HalPomeranz on 2008-07-07
Well it sounds like some program is leaking file descriptors and holding too many files open.  You could do something like this to figure out which programs have lots of open files:

```

sudo su -
for i in /proc/[0-9]*; do
    echo -n "$i  "
    ls $i/fd | wc -l
done | sed 's/\/proc\///' | sort -n -k2

```

That'll give you a list of all the PIDs on your system followed by the number of open file descriptors per process, sorted numerically by the number of open file descriptors.  The ones with the most open files will appear at the end of the list-- figure out what those processes are and kill or restart them to get them to give up their open file descriptors.

---

### Post by Afkpuz on 2008-07-08
Well, my ubuntubox pulled a windows move because after a reboot, I can empty my trash and am not getting that error any more.  Oh well.  Thanks for the help

---

### Post by sayakb on 2008-07-08
Please mark the thread as solved..

---

### Post by HalPomeranz on 2008-07-08
> **Afkpuz said:**
> Well, my ubuntubox pulled a windows move because after a reboot, I can empty my trash and am not getting that error any more.

That's what I'd expect.  Your reboot restarted all the processes on the system, so whatever process is leaking file descriptors was reset.

The next time you have this problem, you might try running the code in my previous posting to see which process is the guilty party (and perhaps file a bug report against this process).

---

