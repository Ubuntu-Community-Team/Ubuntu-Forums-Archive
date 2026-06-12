---
title: "Software Updater issue"
date: 2015-09-03
forum: General Help
---

### Post by entropy1 on 2015-09-03
The Software Updater ran this morning, 9/3/2015, in Ubuntu 14.04.3. It showed a security update for Ubuntu base, 62.3 MB of kernels and headers. I clicked "Install Now". The process started, but after about a second or two, the window disappeared and nothing more happened.

I ran the updater again and the same thing happened.

Is this due to a problem with the update package that the people who make the updates need to change, or is there a problem with my system?

---

### Post by ian-weisser on 2015-09-03
> **entropy1 said:**
> I clicked "Install Now". The process started, but after about a second or two, the window disappeared and nothing more happened.

Give it 24 hours and see if the issue recurs.
If the problem recurs, then try updating manually.
```
sudo apt-get update
sudo apt-get dist-upgrade         ## Since we know a kernel update is in there
sudo apt-get autoremove
```

If you get error messages, then post the entire terminal output here.
If you don't get error messages, but Software Updater continues to fail (the next updates a few days later) then reinstall SU.

---

### Post by entropy1 on 2015-09-04
The Software Updater ran this morning, 9/4/2015, in Ubuntu 14.04.3. Everything updated normally. Waiting solved the problem. Thank you!

---

