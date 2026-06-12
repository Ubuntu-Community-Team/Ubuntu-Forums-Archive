---
title: "[SOLVED] How do I let &amp;quot;locate&amp;quot; (or &amp;quot;slocate&amp;quot;) see a USB drive?"
date: 2008-01-22
forum: General Help
---

### Post by mjpatey on 2008-01-22
I have a 500GB external USB hard drive that stores all my photos, and is always connected to the computer.  I'd like to use the "locate" or "slocate" command to quickly find pictures I need.

Unfortunately, these commands seem to only return results from my main system drive.  Is there a way to make locate and slocate aware of my USB drive, too?

Thanks for any help you may have!

-Mark

---

### Post by diaa on 2008-01-24
By default, locate excludes /media and its subfolders, I assume your USB drive gets mounted under /media and this is why it's not indexed by locate.
To make locate include /media and its subfolders, edit the system file /etc/updatedb.conf by running(Alt+F2):
```
gksu gnome-text-editor /etc/updatedb.conf
```
then you'll find a line in this file that looks like
```
PRUNEPATHS="<something here>"
```
This is a list of folders that locate excludes when it runs, you just need to remove */media* from this list, then save the file.
**don't forget to keep a backup in case something goes wrong**
Now, the next time updatedb runs, it'll include */media*.
You can run it immediately by running
```
sudo updatedb
```

---

### Post by mjpatey on 2008-01-24
Love it!  Thank you so much!!!

updatedb hasn't completed yet, but as soon as I ran it, my external drive's light started flickering away.

And you are a man of few beans!  I predict a very high Thanks:Beans ratio.  :-)

Thank you!

-Mark

---

### Post by mjpatey on 2008-01-24
An update:  as expected, diaa's suggestion worked perfectly.  I'm able to search through the many thousands of files on that external drive.

Marked as solved!

I am curious... does this sort of additional indexing slow my system during times of normal activity, or  is updatedb only using resources when I'm not around?  I did find the following lines in updatedb.conf that I'd interpret to mean it'll try its best to work, but allow itself to be interrupted:

```
# 1 for real time, 2 for best-effort (3 for idle is only allowed for root!)
IONICE_CLASS=2
export IONICE_CLASS
# 0-7 (for IONICE_CLASS 1 and 2 only), 0=highest, 7=lowest 
IONICE_PRIORITY=7
export IONICE_PRIORITY
```

Am I interpreting that correctly?  I assume "realtime" would make it king of the processes, and "idle" would relegate it to the bottom of the heap?

-Mark

---

### Post by diaa on 2008-01-27
> **mjpatey said:**
> An update:  as expected, diaa's suggestion worked perfectly.  I'm able to search through the many thousands of files on that external drive.

Marked as solved!

I am curious... does this sort of additional indexing slow my system during times of normal activity, or  is updatedb only using resources when I'm not around?  I did find the following lines in updatedb.conf that I'd interpret to mean it'll try its best to work, but allow itself to be interrupted:

```
# 1 for real time, 2 for best-effort (3 for idle is only allowed for root!)
IONICE_CLASS=2
export IONICE_CLASS
# 0-7 (for IONICE_CLASS 1 and 2 only), 0=highest, 7=lowest 
IONICE_PRIORITY=7
export IONICE_PRIORITY
```Am I interpreting that correctly?  I assume "realtime" would make it king of the processes, and "idle" would relegate it to the bottom of the heap?

Yes I think so, you're correct, but I don't recommend changing the file.
As far as I know *updatedb* runs once a day at most automatically and it runs at low priority so you can do whatever you want while it's running.

---

