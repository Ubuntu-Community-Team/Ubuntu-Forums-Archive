---
title: "Mythtv directory error"
date: 2006-11-19
forum: General Help
---

### Post by daveyiv on 2006-11-19
Hello, I just installed Mythtv on Edgy and am trying to run the backend and its giving this error:

/media/videos/mythtv/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/media/videos/mythtv' exists and that both 
the directory and that file are writeable by this user.

I have tried chmod the directory to 777 permission and it still does that, does anyone know what else to try?

---

### Post by superm1 on 2006-11-19
The permissions need to be set to mythtv:mythtv

sudo chown mythtv:mythtv /media/videos/mythtv

sudo chmod ug+rw /media/videos/mythtv

---

