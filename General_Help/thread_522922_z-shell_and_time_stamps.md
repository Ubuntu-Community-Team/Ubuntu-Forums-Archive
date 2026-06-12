---
title: "z-shell and time stamps"
date: 2007-08-11
forum: General Help
---

### Post by Hakimio on 2007-08-11
I've used [this](http://stuff.mit.edu/~jdong/misc/zshrc) z-shell config file and everything seems to be working just fine, except that the time stamps (hours and minutes) are completely incorrect. Is there a way to fix this?

---

### Post by aJayRoo on 2007-08-11
Make sure to set the TZ variable (about 40 lines into the .zshrc file) to your timezone. For instance I have mine set to:
```
TZ="Europe/London"
```
What you need to set this to will depend on your location. You can determine what is appropriate by looking for your region (Europe) in '/usr/local/zoneinfo' and then find the city closest to you in that folder (eg. I look inside the folder '/usr/share/zoneinfo/Europe' and find the city closest to me is London... hence my TZ variable should be set to Europe/London). Hope that helps.

---

### Post by Hakimio on 2007-08-12
Thanks, it worked :)

---

