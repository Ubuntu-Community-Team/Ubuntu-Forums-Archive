---
title: "How to reinstall Firefox?"
date: 2008-03-08
forum: General Help
---

### Post by Zdravko on 2008-03-08
I want to completely reinstall Firefox, and have the bookmarks restored to their initial values. How?

---

### Post by ahaslam on 2008-03-08
Reinstall by whatever means you prefer & rm -r ~/.mozilla/firefox ;)

---

### Post by matty_b_1000 on 2008-03-08
Why do you need to reinstall Firefox? If you messed something like an extension or theme up and it crashes Firefox, you can use Safe Mode:
```
firefox -safe-mode
```
which disables all Addons to uninstall the problematic extension.

---

### Post by nvteighen on 2008-03-08
But, if you still insist on reinstalling (but try Safe Mode first), do this:

```

sudo apt-get remove firefox --purge && rm -r ~/.mozilla/firefox
sudo apt-get install firefox

```

---

