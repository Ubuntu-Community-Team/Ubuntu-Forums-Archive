---
title: "Konqueror freezes"
date: 2013-05-20
forum: General Help
---

### Post by Krister Hallergard on 2013-05-20
Have been away from Ubuntu for a couple of years, but thought I would give it another chance.  Installs fine and only real problem is file management.  Konqueror freezes and so does Dolphin.  And Nautilus has fewer functions than I remember from a few years ago.  What is one supposed to use as a file manager?  and Root file manager?

---

### Post by lykwydchykyn on 2013-05-20
Might be better to figure out why dolphin and konqueror are freezing up on you; are you using KDE or did you install them on top of Unity?

---

### Post by Krister Hallergard on 2013-05-20
On top of Unity, thanks

---

### Post by lykwydchykyn on 2013-05-20
Have you tried launching Konqueror from a terminal to see if there is any error output?  

I run dolphin in awesome window manager, the first run is usually a little sluggish since it has to load in all the KDE services, but it doesn't freeze up.

---

### Post by Krister Hallergard on 2013-05-20
Thanks, after giving the reply above, I tried starting in teminal.  No error output.  Am using command    gksudo "konqueror --profile filemanagement"    So I rebooted, tried starting in terminal, and it started ok - both konqueror and dolphin. Since then I have been trying to recreate the freezing, but not managed to.  Good - but the last three weeks it has been working off and on, and I have not managed to work out why.

---

### Post by lykwydchykyn on 2013-05-20
You might want to use kdesudo with konqueror.  Might not make a difference, but you never know.

---

### Post by Krister Hallergard on 2013-05-21
No difference with kdesudo, thanks

---

### Post by Krister Hallergard on 2013-05-21
Tried again this morning to get the Konqueror stalling back, but could not.  I had some idea that starting konqueror too soon after reboot would cause it.  Thought maybe using another system (Windows or another distros) on the same desktop before booting into Ubuntu could contribute.  Could not confirm either of those hypotheses.  Once the freezing starts it seems to continue, and it seems to me as some kind of memory problem.  Will leave it for now, and probably have to come back.  Thanks

---

### Post by Krister Hallergard on 2013-05-21
Happened again, but not straight away as before, but later when I have navigated and want to copy a file and right click for the context menu - the screen goes dark and I am stuck.  The same happens with Dolphin.  And no info in the terminal.

---

### Post by Krister Hallergard on 2013-05-24
Think I finally got it.  Chasing logfiles with error messages I kept finding some python2.7-things not working.  Comparing with my Kubuntu 13-04 partition there were two packages not installed: python-gobjects-2 and python-gi  Installed them and since then I have not had any problems with freezing or to get the context menu of konqueror to function.  Also dophine works fine.  thanks.

---

