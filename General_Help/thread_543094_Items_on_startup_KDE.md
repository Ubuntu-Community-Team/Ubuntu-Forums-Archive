---
title: "Items on startup KDE"
date: 2007-09-04
forum: General Help
---

### Post by markk1994 on 2007-09-04
Hey its me once agian Im having an issue with the programs that start on startup
Programs like Amarok the music player and stuff like that always start Is there a way i could disable them?

---

### Post by somedamfool on 2007-09-04
If you exit the programs before you shut down, they shouldn't start again at startup. If they do, open the control center and go into kde components/session manager and make sure 'restore previous session' isn't checked. If it is check 'start with empty session', then kill the apps you don't want, reboot, and if they are gone, you can re-enable 'restore previous session' if you want to. Anything running when you enable restore previous session will start each time.

You might also check in ~.kde/autostart and see if there are .desktop files for the unwanted apps in there. If so delete the ones you don't want.
Mike

---

