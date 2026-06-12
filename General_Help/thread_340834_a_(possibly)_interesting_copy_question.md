---
title: "a (possibly) interesting copy question"
date: 2007-01-17
forum: General Help
---

### Post by mdurham on 2007-01-17
Assume that I only have one partition and that I have rsync-ed an image of the system to a backup drive. Would it be possible to rsync it back on top of the changed active system that I'm using, that is, the system that I would be running rsync on?
Can you see any problems doing that?
Cheers, Mike

---

### Post by po0f on 2007-01-18
mdurham,

I don't think it will work.  Doesn't rsync only move files when there is a newer one available?  If you continued to use the system you backed up, all the atimes on the files would have changed (time last accessed).  Maybe rsync works based on the mtime (time last modified), but even then, you won't get a complete restore.

Your best bet would be to either selectively restore individual files or look at [cp's man page](http://unixhelp.ed.ac.uk/CGI/man-cgi?cp) for options that sound like they'll do what you want them to do.

---

### Post by mdurham on 2007-01-18
As far as I can ascertain, rsync works on mod-time and size. So if I modify the system, maybe do an update or some such thing, I wonder if I could do a complete rsync from the backup to the system while the system is still running? If you see what I mean?
Maybe I'll just try it!
Cheers, Mike

---

