---
title: "Are Firefox snaps replacing .mozilla?"
date: 2023-04-25
forum: General Help
---

### Post by lou6 on 2023-04-25
Just checking to make sure I understand what info is good for use.  I have been backing up the .mozilla folder and the snap on a daily basis.  One thing I've noticed that raises questions is that I see in the snap data multiple entries labeled as "default release" - seems like this could cause confusion when deciding what to restore when restore is needed.  I've added 'time last modified' to my Nautilus display to help in deciding what to restore.  I don't actually have a question but would like to hear any thoughts from those wiser than I about what effect this might have on backup and restoration of Firefox.  Thanks for any thoughts you Ubuntu gurus may have ...

---

### Post by #&amp;thj^% on 2023-04-25
If I ever install the snap version of Firefox it has now imported my profiles from the original directory inside ~/.mozilla/firefox/ into the new directory of ~/snap/firefox/common/.mozilla/firefox/ this is where they are stored now.
It doesn't replace .mozilla but the profile info is moved to ~/snap/firefox/common/.mozilla/firefox/

If you navigate to **about: profiles** it will show your current profile and it's full path.
remove the space between : and profiles

---

### Post by lou6 on 2023-04-25
Thanks for the about: profile suggestion - much better than the date/time as a way to find the current profile.  I'll leave this post up for another day or so in case anyone else has a useful nugget of info...

---

