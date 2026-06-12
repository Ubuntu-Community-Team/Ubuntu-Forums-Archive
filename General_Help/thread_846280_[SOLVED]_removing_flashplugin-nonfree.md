---
title: "[SOLVED] removing flashplugin-nonfree?"
date: 2008-07-01
forum: General Help
---

### Post by sci-fi guy on 2008-07-01
Will removing the flashplugin-nonfree package remove the flash plugin from FF? I am curious because I am not sure it knows to remove Adobe's files downloaded by the package.

---

### Post by llama320 on 2008-07-01
if you purge the file

```
sudo apt-get purge flashplugin-nonfree
```

and then

```
sudo apt-get autoremove
sudo apt-get autoclean 
```

that should remove the plugin and everything that was associated with it

apologies if you already knew all of that :)

---

### Post by sci-fi guy on 2008-07-01
I knew autoremove, but not 'purge' or 'autoclean'. Thanks!

---

