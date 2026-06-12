---
title: "[SOLVED] chkrootkit and lastlog"
date: 2008-01-26
forum: General Help
---

### Post by Maximos on 2008-01-26
When I run chkrootkit (on Gutsy), I get the following line as one of the results: > Checking `z2'... user <username> deleted or never logged from lastlog!

Of course, instead of '<username>', it ouputs my actual username.  In any case, I was curious why it gave this result, so I ran lastlog, and discovered that lastlog reports that no user has ever logged into my system; it says, for every user (even the one that I am currently logged in as), "**Never logged in**".  I've logged into this system numerous times, so why does lastlog give this output?  Is this something I should be concerned about, or is lastlog just not working?

Thanks!

---

### Post by dcstar on 2008-01-26
> **Maximos said:**
> When I run chkrootkit (on Gutsy), I get the following line as one of the results: 

Of course, instead of '<username>', it ouputs my actual username.  In any case, I was curious why it gave this result, so I ran lastlog, and discovered that lastlog reports that no user has ever logged into my system; it says, for every user (even the one that I am currently logged in as), "**Never logged in**".  I've logged into this system numerous times, so why does lastlog give this output?  Is this something I should be concerned about, or is lastlog just not working?

Thanks!

When I run lastlog it outputs data that I expect, with info about my system's accounts' last login on the TTY terminals - it does not report on X logins.

---

### Post by Maximos on 2008-01-26
Any further hints as to what might be the "problem with my system?"  I'm a bit skeptical that something intruder-related has happened, considering that I only installed Ubuntu about three days ago, do not leave the system running while unattended, have not downloaded any suspicious packages, and am basically operating with the standard Ubuntu install.  Also, when I run "last," the system does show my logins.  I've done another check for rootkits (to corroborate ckhrootkit) with rkhunter, and it finds nothing.  chkrootkit gives no problematic output except for the one that I mentioned in the original post.  Firestarter is constantly running, so I'm monitoring my firewall.  When I check my system for open ports, all ports are closed.  

Any further suggestions?  Maybe someone know something about the inner workings of lastlog?

Thanks!

---

### Post by Maximos on 2008-01-26
Incidentally, lastlog uses /var/log/lastlog as its log file.  That file is, for some reason, empty.

---

### Post by Maximos on 2008-01-26
Just did some further testing.

Initially:
/var/log/lastlog is empty
lastlog reports that no user has ever logged in
chkrootkit gives the aforementioned output

I re-logged in to Gnome, and the same conditions obtained.

Next, I went to a tty and logged in.  Now things change:
/var/log/lastlog reports a login on the proper terminal
lastlog reports that a user has logged in
chkrootkit gives different, better sounding output

This indicates that the login data relevant to lastlog is recorded only on login to standard terminals, and not on login to Gnome.  As I'm writing this, dcstar, I see that you have edited your initial post to say that lastlog reports on tty logins, but not on logins to X.  So we seem to have discovered the same thing (or maybe you didn't discover it; you might have known it already, but I did not).  Apparently I was receiving this output because -- given that I had installed Ubuntu only recently -- I had not yet logged in via a standard terminal (I had used the terminal within X, after logging into X, but that's different).

Presumably this resolves the problem and is nothing to worry about?  If I hear verification, I'll mark the thread solved (although, even if I don't hear verification, I'm presuming that this was the issue the whole time: no login to standard tty yet).

---

### Post by Maximos on 2008-01-26
Sorry about all of the follow-ups, but I've done the following and so am now marking this thread as "solved."  I created a new user, logged that user in via X, and checked lastlog to verify that it showed no login for this user.  I then logged that user in via a terminal window and checked lastlog again.  The user's login only showed after login via the terminal.  So, that's what was going on in my initial case as well.

---

