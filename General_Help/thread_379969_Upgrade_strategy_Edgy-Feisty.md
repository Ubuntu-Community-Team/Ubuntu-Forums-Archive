---
title: "Upgrade strategy Edgy-Feisty"
date: 2007-03-09
forum: General Help
---

### Post by sarc on 2007-03-09
Sorry I could not find answer in the existing threads... if this has already been discussed please point me to the right thread.

What's the best way to make the transition?

Reformat drive and reinstall
Better performance and more stable I understand - but lose all desktop settings, program settings (esp. OpenOffice preferences!), have to redo all the stuff I had to do to get Edgy to work (&*%##@ Nvidia drivers!)

Upgrade via apt-get as per user manual
Lose on some features and maybe speed/stability.  Will STILL break some things (&*%##@ Nvidia drivers again!  Why won't the thing just WORK?).  I can't contemplate spending another weekend trying to get my loudspeakers to shut up and my earphones to work.

Is my understanding right?  Is there a third way?  Thanks!

---

### Post by Kateikyoushi on 2007-03-09
You can move /home to it's own partition so you keep your settings even if you do a freash install, nvidia drivers break with every kernel change but fairly easy to set up. Read this guide how to make a /home partition. [LINK]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by sarc on 2007-03-09
Thanks but my understanding from previous posts is that having a /home partition will not help as the real important settings are in the root partition (/dev, /etc/, /this and /that....)

---

### Post by Kateikyoushi on 2007-03-09
All your user settings are stored in /home from fonts to icons to your emails, browser bookmarks, toolbar settings etc. these can become fairly important.

---

