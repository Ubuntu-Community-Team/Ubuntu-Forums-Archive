---
title: "Sessions: keeps loading old session after restore."
date: 2007-01-25
forum: General Help
---

### Post by Gen2ly on 2007-01-25
Hi all!  Does anyone have experience working with sessions?  Yesterday, I had to restore my Ubuntu install - I restored over my older Ubuntu.  So everything is absolutely perfect, *except* Ubuntu keeps attempting to bring up the previous session.  This happens everytime I log in.  Is there a preferences file that I could erase?  Is there someway someone knows how to fix this bad behavior?

---

### Post by Gen2ly on 2007-01-25
Ah! I went into .gnome2 and found a couple files (session and gnomemeeting) that were locked so I just

sudo chmod -R 777 *

to fix.

---

### Post by Gen2ly on 2007-01-25
Dang didn't do it.  Any ideas?  I still have the same programs popping up.

---

### Post by Gen2ly on 2007-01-26
Hah voila!  I went to the Menu > System Tools > Configuration Editor.  Looked up session went to /apps/gnome-session/options and checked auto_save_session.  I logged back in and now those apps that are old don't pop up no more!

---

### Post by Gen2ly on 2007-01-29
rats.  I looked back and configuration editor and the auto_save is checked off, so I checked it on again  I logged off with a two programs open and now I see them pop up at every login.  There is a file that must be locked up looking thru .gnome folders doesn't reveal anything.  I don't want to delete these preferences if possible.

---

### Post by Gen2ly on 2007-02-01
I'll post until I get a reply :P

---

### Post by Gen2ly on 2007-02-06
Figured it out.  K.  The .dmrc file in the home directory was being ignored.  Why, because apperently when I restored my system my home folder permissions were changed. fix:
> sudo chmod 755 /home/username

---

### Post by Gen2ly on 2007-02-07
actually this fixed some issues like my HOME/.dmrc file, and I can now check in configuration editor to auto_save and it will remember it.

---

### Post by Gen2ly on 2007-02-13
don't know why I didn't think of this before.  System > Preferences > Sessions.  Add session, I used my username, then delete the old one.  I know I sounds stupid but Im pretty new to all this still.

---

### Post by jms1989 on 2007-02-16
> **Dirk.R.Gently said:**
> don't know why I didn't think of this before.  System > Preferences > Sessions.  Add session, I used my username, then delete the old one.  I know I sounds stupid but Im pretty new to all this still.

You know, this actually worked. I used to have the same problem and now it's history.

Thanks man.

---

