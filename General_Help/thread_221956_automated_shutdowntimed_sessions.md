---
title: "automated shutdown/timed sessions"
date: 2006-07-24
forum: General Help
---

### Post by danti on 2006-07-24
Hello,

I want to limit the time that people are logged on my computer to 30 minutes.  The first thing I tried was putting a script in etc/init.d that called "shutdown -h +30", and incorporating this into the boot cycle using update-rc.d.  This caused me not to be able to login anymore, for as soon as I'd entered a username, a message appeared saying "Computer going down at such & such time".
I had to undo this by going in restore mode, deleting the scripts, using update-rc.d .. remove.  I also tried a similar solution by having the "shudown" called by "at".  This behaved exactly the same way, and I had to remove this similarly (+ atrm to remove jobs).

Since I only want this behavior for certain users, I decided to try this in user/.bash_profile, but problems with this are (1) the users will need sudo (which may not be a problem, since they do not know their own passwords), (2) sudo cannot be passed a password, so they will have to enter it.

If anyone has a good solution to this, I would sure appreciate it.

Dan

---

