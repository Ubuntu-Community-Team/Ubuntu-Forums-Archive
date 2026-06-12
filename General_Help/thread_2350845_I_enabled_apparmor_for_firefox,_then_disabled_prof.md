---
title: "I enabled apparmor for firefox, then disabled profile, now firefox won't work"
date: 2017-01-28
forum: General Help
---

### Post by MechaMechanism on 2017-01-28
Fixed!  The Apparmor messes with the menus.  Putting profile into complain mode fixes it.


Following the guide here; [https://help.ubuntu.com/lts/serverguide/apparmor.html](https://help.ubuntu.com/lts/serverguide/apparmor.html)
I did ```
sudo aa-enforce /etc/apparmor.d/*
sudo aa-complain usr.bin.firefox
sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.firefox
sudo rm /etc/apparmor.d/disable/usr.bin.firefox
reboot
```

I disabled the Apparmor profile because Facebook video calling would not work.  Now Firefox opens and looks completely normal in every way.  Clicking on menus opens them up.  But any attempt to go to a web page fails.  Clicking does nothing.  I have uploaded a video to help you see.
Video of problem here; [https://blog.universal-mechanism.org/2017/01/28/firefox/](https://blog.universal-mechanism.org/2017/01/28/firefox/)

---

