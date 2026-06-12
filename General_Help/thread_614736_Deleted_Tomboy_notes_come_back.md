---
title: "Deleted Tomboy notes come back"
date: 2007-11-16
forum: General Help
---

### Post by mattack on 2007-11-16
My deleted Tomboy notes magically undelete themselves every day. I have to delete them twice for them to be gone for good. It only seems to happen to the "Note of the Day." Notes I create manually don't undelete.

I use the "Note of the Day" to keep track of things I need to do, things I've done, etc... I delete today's note at the end of the day, just before logging out. The next day, when I log back in, yesterday's Note of the Day is back... I delete it again and it's gone for good. It doesn't come back.

I've figured out that Tomboy keeps backups of deleted notes. My guess is if I delete the backup, it would not reappear. That seems silly though, when I delete a note it should be gone (unless I restore the backup). I shouldn't have to delete the note and it's backup.

Is there a preference that I'm missing? Plug-in conflict? Any help would be appreciated...

---

### Post by mattack on 2007-11-20
bump

---

### Post by mattack on 2007-11-26
It gets weirder...
Now Tomboy not only recreates my deleted Note of the Day, it creates a blank Note of the Day with the same title as the deleted one!

For example; On Monday, Tomboy will automatically create a note "Today: Monday November 19" that I use to keep track of tasks, meetings, etc... I delete this note at the end of the day, and log out of my computer. On Tuesday, Tomboy creates a note "Today: Tuesday November 20" and recreates my November 19th note with all the contents restored. And lately (for the past week) it's been creating another note for Nov. 19th that's empty.
So I get 3 new notes daily. The one that should be created, the one that I deleted yesterday (with all the contents I entered), and another one for yesterday (but empty).

Any insight would be appreciated.

---

### Post by -grubby on 2007-11-26
umm...the only thing I can suggest is for you to remove tomboy and install it again

---

### Post by atlfalcons866 on 2007-11-26
this might be weird but it happened to me before
are you using ext3 with journal data writeback? if so after a crash old data can reappear happened to me before.

---

### Post by mattack on 2007-11-29
> **atlfalcons866 said:**
> this might be weird but it happened to me before
are you using ext3 with journal data writeback? if so after a crash old data can reappear happened to me before.

I'm using the default file system that Ubuntu 7.4 uses. I assume it's ext3, I don't know about journal data writeback...  What's the best way to check for that? Also, what do you do to prevent old data from being written back?

---

### Post by mattack on 2007-12-03
> **nathangrubb said:**
> umm...the only thing I can suggest is for you to remove tomboy and install it again

Tried uninstalling and re-installing. The deleted notes still come back. :confused:

---

### Post by metalheart on 2007-12-03
The Note of the Day note is related to the The Note of the Day plug-in. If you Disable the plug-in, that note should not appear.

---

### Post by dimbulb1024 on 2007-12-03
Maybe try deleting all the notes in the Backup folder of your .tomboy folder in /home.

---

### Post by mattack on 2007-12-04
> **metalheart said:**
> The Note of the Day note is related to the The Note of the Day plug-in. If you Disable the plug-in, that note should not appear.

I want the note of the day. What I don't want is *deleted* notes of the day to *re*-appear, which is what's happening.

---

### Post by mattack on 2008-01-09
Yesterday's Tomboy update seems to have solved this.

---

### Post by mattack on 2008-01-29
I take that back...  It's doing it again. Un-deleting deleted Note of the Day.
grrr....

Anyone know anything about this?

---

### Post by sharm on 2008-01-29
Please file a bug in GNOME bugzilla if you'd like us (the Tomboy developers) to investigate this apparent problem with the Note Of The Day plugin.  We don't really track distro-specific forums.

---

