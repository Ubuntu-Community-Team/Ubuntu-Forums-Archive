---
title: "firefox and thunderbird won't start"
date: 2007-04-18
forum: General Help
---

### Post by jabb0r on 2007-04-18
I'm having a very frustrating issue with firefox and thunderbird.  It happens intermittently and I haven't been able to correlate it to anything yet.

When I start firefox, it will ask if I would like to start a new session or restore previous session.  No matter which buttom I press, the window disappears and firefox never appears.  'ps' shows the firefox process running.  Similarly, thunderbird will ask for the password for my imap server, and then never appear.  Process is still running.  Running from the command line, I get no errors...just a blinking cursor.

These applications both use the mozilla framework, so I expect they're related.  Removing or moving the '.mozilla' directory from my home directory does not fix or change the problem.  Repeatedly killing and restarting the hung process has no effect.  This issue has been plaguing me for months, so I would appreciate any help.  Thanks.

--Phillip

---

### Post by strabes on 2007-04-18
Have you tried purging & then reinstalling the program? ```
sudo aptitude purge firefox && sudo aptitude install firefox
```

---

### Post by ajgreeny on 2007-04-18
It sounds as if your profiles may be corrupt.  In your home folder, make sure hidden files are showing (Ctrl+h) and  select
.mozilla
Rename it .mozillabackup (dont forget the dot in front of the name) then restart firefox.  Hopefully a new firefox profile will be made and firefox will start OK.  You can then copy back in the various filesin the old profile, bookmarks is the most important, I suspect,  one by one and see if all is OK.  It is quite possibly one of the add-ons, if you have any, that is causing the problem, so do this bit preferably by reinstalling the ones you want from the mozilla website, not by copying them from your old profile.

The same procedure will probably also work with thunderbird's profile which will be in the .mozilla-thunderbird folder.

You could also try uninstalling the add-ons one at a time and see if that makes any difference to your programs.

Good luck and I hope this does the trick.

---

### Post by jabb0r on 2007-04-18
Deleting the .mozilla directory does not help.  Incidently, I tried using the official firefox binary and it worked without issue, so it has something to do with the ubuntu binary.  I'm using Feisty, but I saw this issue before I upgraded.

--Phillip

---

### Post by bartwijnants on 2007-06-11
I have the same problem in feisty, just had to restart 3 times completly (not just Gnome) before it worked. I think it has something to do with the information from the last session... I think that could be corrupted or something, but I'm not sure and I don't know where to find it....

---

