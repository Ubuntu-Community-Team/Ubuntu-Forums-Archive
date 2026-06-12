---
title: "How to restore epiphany default settings ?"
date: 2007-10-24
forum: General Help
---

### Post by ennoreys on 2007-10-24
The question is in the title. I'd like to restore default settings on epiphany. I know a workaround which is to use about:config URL and to reset all lines in bold but it's quite long because we cannot select multiple lines.

---

### Post by commonlyUNIQU3 on 2007-10-24
have you tried to delete the epiphany config directory?

It is located in ~/.gnome2/epiphany

You could also try to run the following in a terminal:

```
rm -rf ~/.gnome2/epiphany
```

If that doesn't work you could try to remove/purge the epiphany install, and reinstall (fairly quick, and a better chance of working the way you want)...

First do:

```
sudo apt-get autoremove --purge epiphany-browser epiphany-extensions
```

Then:

```
sudo apt-get install epiphany-browser
```

Let me know if that works or not...

---

