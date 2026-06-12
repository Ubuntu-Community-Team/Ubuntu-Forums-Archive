---
title: "Cannot Log In"
date: 2007-01-23
forum: General Help
---

### Post by igknighted on 2007-01-23
This one has me stumped.  I am trying to fix my friends Ubuntu box, and for some reason she cannot log in.  The system boots with no errors into KDM (it's kubuntu) and I get the normal log in prompt.  Then when I type in the password and hit enter the screen goes dark for a few seconds, sometimes I get a panel across the bottom for a brief second, and then I get kicked right back to the login screen.  After trying to log into GNOME as well as KDE (and failsafe for good measure), all with equal degrees of failure, I tried to login via tty1.  The login prompt here is not normal (the hostname, usually 'Edgar', says '(none)'.  I type in the username and the computer thinks for 5/10 seconds and then I get the login prompt again (sometimes the KDM GUI one, sometimes not... i couldn't figure out a pattern to this).  It never even asks for a password.  Finally (not really sure of what I was looking for at this point anyways) I restarted into recovery mode.  Here the command 'ls' decided that I didn't have permissions to use it (even though I was root).  Everything else seemed ok, I could find where I was via 'pwd' and could edit files via nano, I fingered the main username even and it said I had just logged in a few minutes before, even though I had never been able to.

Anyone with advice on where to go from here would be greatly appreciated, as I am at the end of what I know what to do.  Thank you.

---

### Post by Ecthelion on 2007-01-23
I've also had this problem and after searching for an hour I decided that reinstalling only takes 30 minutes...
So I reinstalled.
Unless you want to find the cause to file it as a bug, I advice you to do the same...

---

### Post by igknighted on 2007-01-23
> **Ecthelion said:**
> I've also had this problem and after searching for an hour I decided that reinstalling only takes 30 minutes...
So I reinstalled.
Unless you want to find the cause to file it as a bug, I advice you to do the same...

I suppose this is a possibility but I don't like to resort to slash and burn tactics if I don't have to.  I thought I might have found the culprit earlier today, after I installed the ext3 driver for windows to look around the drive I realized that /home was nearly full (on its own partition), so I copied a few things over to windows to free up space (several DVD images) and tried to log in.  There was no effect, still got kicked back to KDM.

---

### Post by Zerhash on 2007-01-28
Ive got the same issue

it may be linked with being out of hard disk space, or deleting a theme

---

### Post by munkiepus on 2007-01-28
I had the problem where it get to the kde login screen and after i entered the password it would return to the login screen after a few seconds.

Just to confirm this was caused by lack of disc space i deleted some stuff from my home directory and it logged in a treat. :D

Cheers

---

### Post by Ecthelion on 2007-01-29
That couldn't have been the problem with me.. I had 30+ Gb left on each disk...

---

### Post by igknighted on 2007-02-01
I fear the issue may be a bad hard drive.  Last time I tried to boot it went to disk check and got hundreds of inode errors... I have thrown in the towel on this install and am hoping that reformatting will fix the disk.

---

