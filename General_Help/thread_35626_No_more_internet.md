---
title: "No more internet"
date: 2005-05-19
forum: General Help
---

### Post by VincentP on 2005-05-19
Well.. everything was working fine yesterday, I booted up into Windows for the first time after installing Ubuntu, Windows still worked fine.  Tried to reboot back into Ubuntu, the boot sequence freezes at Checking Network Configuration, or something like that, I don't remember the exact wording.  Anyways, after 2-3 minutes it skips this part, gives me an error that goes by too fast to read, though I saw the word "Failed", then boots the system with no internet connection.

---

### Post by smb2004 on 2005-05-19
assuming you are on dhcp , the command :

```
sudo dhclient
```

will reset the internet.  unfortaonly for me i have to do that everytime i reboot.  anyone know how to totaly reset internet?

---

### Post by VincentP on 2005-05-20
Ok, I tried this, it didn't work.  However, I changed my ethernet cable from one jack to the other (I'm using my onboard LAN) and it worked.  However, this jack doesn't work in windows... I cannot figure that one out.  Also, when I have it plugged into the working internet jack, I get a net error when trying to run world of warcraft with cedega.  Previously, it was working perfectly, never had an error, now I can't play it at all.

---

