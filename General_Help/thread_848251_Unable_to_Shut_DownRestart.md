---
title: "Unable to Shut Down/Restart"
date: 2008-07-03
forum: General Help
---

### Post by Unevolved on 2008-07-03
I was looking at some pictures on a wedding last night, and they had a script on there that threw up an error message any time someone tried to "steal their hard work" i.e. right click, etc.  Turns out, they also set it up for any use of the Ctrl or Alt keys.  So when I tried to Alt-Tab out of the window, it threw up a message.  It did this several times, until I just closed Firefox.  Then I noticed Alt-Tab wouldn't work anymore, in fact none of Compiz's tricks would (wobbly windows, etc.)  

But the most agitating and disturbing issue is that certain system processes seem to have been affected.  I no longer have "Shut Down" or "Restart" options in the upper-right menu, and the Login Screen menu will not run.  It prompts me for my password, then closes.

This is very agitating, mostly because its so confusing.  Any help would be greatly appreciated.

---

### Post by jimv on 2008-07-03
Try killing X and logging back in.  Control+Alt+Backspace

---

### Post by Anzan on 2008-07-03
Unfortunately, I have found that killing the X session does not kill all of GNOME's processes in Hardy. The lack of the log-out menu is a symptom of this. (Pidgin or Evolution crashing results in the same thing.)

Sadly, a reboot is required. This should never happen in Linux.

---

### Post by Anzan on 2008-07-03
To add: ALT+Sysrq+k doesn't fix this either.

---

### Post by jimv on 2008-07-03
Nevermind

---

### Post by Unevolved on 2008-07-03
A reboot won't fix the issue, although the only way I know to shut it down is with a motherboard cutoff.

Any other issues?  This is very agitating.

---

### Post by GuitarRocker2562 on 2008-07-03
applications -> accessories -> terminal

type: reboot

tada

---

### Post by Unevolved on 2008-07-03
Hahaha yes thank you, but that's not the issue I was looking to fix.

---

### Post by GuitarRocker2562 on 2008-07-03
do you have your files on a seperate /home partition? Then you could re-install very easily.

---

### Post by Unevolved on 2008-07-06
I suppose that's about my only option, isn't it?  What all directories should I make backups of in order to preserve most of my settings and directories?

---

### Post by Unevolved on 2008-07-11
Bump for more help, this is a very agitating issue.  I'm betting its going to be one of those things that's a 5 minute fix that takes 3 hours to find.

---

### Post by dracayr on 2008-07-11
to preserve your settings you just have to backup your home folder. But installed programs will be deleted.

EDIT: have you tried reinstalling compiz? tried Safe mode boot -> Fix X server?

dracayr

---

### Post by Unevolved on 2008-07-13
OK, just tried both of those.  No dice.

Any other thoughts?  I really don't want to reinstall the OS.

EDIT:  Oh great, now Compiz doesn't work at all.  I reinstalled, and it stopped working.  I tried completely uninstalling and reinstalling, but no luck.  I just get a "Desktop Effects Could Not Be Enabled" message whenever I try to turn on effects in the System>Preferences>Appearance menu.

---

