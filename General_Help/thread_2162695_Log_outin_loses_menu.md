---
title: "Log out/in loses menu"
date: 2013-07-15
forum: General Help
---

### Post by momist on 2013-07-15
Hi,
I'm running Lubuntu 13.04, a recent clean install.  When I log out and then immediately back in again, there are only two entries in the menu: Run, and Logout.  I have also had a report of a crash, but found I could not copy the details (should have used pencil and paper?)  I can't find any relevant log, or indeed any recent log file.

This is repeatable, but a reboot gives me the menu back.  Another log out/in shows the same problem.

Any ideas where to look please?

---

### Post by ajgreeny on 2013-07-15
Look in the **~/.xsession-errors** file in your home, or perhaps after a reboot you will need to look at the **~/.xsession-errors.old** which will be the backup from the previous session, ie the one where your menu was missing.

---

### Post by momist on 2013-07-15
Thanks ajgreeny,

There's nothing in there about this problem, but it did show where the lxsession log is kept, so I had a look in that.  Still nothing about this problem, but an awful lot about key file problems, window border problems and font problems along with other stuff.  The file is over 18KB and goes on for pages.  Of course, this is not the log for the session when the problem occurred.

Having said it is repeatable, it was then, but didn't happen when I tried a log out/in just now.  Not infallibly repeatable.  I'll come back if it happens again.

I have a separate /home partition, and am beginning to think this is more of a liability than a help.  There's a lot of cruft in there with files of mine going way back to 2004, and system files such as gnome2_private as far back as early 2010.  Maybe I should copy my own stuff elsewhere, and clean out everything else before a fresh clean install?  It just seems a lot of work, but might improve stability.  I'll sleep on that, and see if I can make time to devote to it later.

---

### Post by mm7hKDW on 2013-09-07
This problem still exists on fresh installed Lubuntu, on many configurations. After logout and login with the same user cause the menu crash. Only run and logout are there. All packages are up to date.

---

### Post by oldrocker99 on 2013-09-07
I have seen the same problem, but only intermittently. on my Acer C7 running Lubuntu 13.04 from the chrubuntu script. A reboot (I usually use CTRL-F1 to reboot) has fixed the problem for me, when it has happened.

---

