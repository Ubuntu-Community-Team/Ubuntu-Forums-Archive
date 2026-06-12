---
title: "Fluxbuntu"
date: 2007-06-11
forum: General Help
---

### Post by jamiehd on 2007-06-11
I'd like to install fluxbuntu on my laptop. I currently have ubuntu installed, with fluxbox, but is there any way to install over the top, without loosing programmes/settings etc?

---

### Post by MetalMusicAddict on 2007-06-11
No. Well, not unless you have a separate Home partition or backed up the settings.

---

### Post by jamiehd on 2007-06-11
Damn. That's annoying. Well, thanks for the help anyway!

---

### Post by RedSquirrel on 2007-06-11
> **jamiehd said:**
> I'd like to install fluxbuntu on my laptop. I currently have ubuntu installed, with fluxbox, but is there any way to install over the top, without loosing programmes/settings etc?

Just wanted to add:

You might consider backing up your ~/.fluxbox directory if you have customized your Fluxbox. Some of your settings may be of use when you install Fluxbuntu.

```
cd ~
tar czf fluxbox_backup.tar.gz .fluxbox

```The ~/.fluxbox directory is small in size but loaded with settings. ;)

---

