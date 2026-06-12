---
title: "Unity doesn't start after login"
date: 2016-07-24
forum: General Help
---

### Post by hojjat on 2016-07-24
I updated my Ubuntu 16.04 and it required a reboot. After reboot when I log in, unity does not load (no menus on the top). If I do CTRL+ALT+F1 and run "setsid unity", however, unity launcher finally appears, but the top menu is still missing.

Any advice on how to fix this?

---

### Post by hojjat on 2016-07-24
On further investigation, I noted that when I created a new account and logged in there, it worked just fine. The conclusion being that my account's profile was messed up.

Therefore I renamed ~/.config and ~/.profile and rebooted. Things worked, but of course I lost my configs. I am in the process of recovering them now.

---

