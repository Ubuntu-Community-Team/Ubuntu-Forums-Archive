---
title: "KDE System sounds are not working"
date: 2007-04-15
forum: General Help
---

### Post by wersdaluv on 2007-04-15
Sounds for all KDE apps are not working.

For example, kopete sound notifications are properly configured, but whenever I play the sound in the configure notifications menu, they do not play. They do not also play whenever I receive instant messages or whatever event  that should notify me with a sound, but the sound files exist and do play in Amarok.

All the other KDE sounds do not work too even if I have aRts insalled. 

How can I fix this?

---

### Post by berserker on 2007-04-19
This worked for me:

```
sudo rm /var/tmp/kdecache-yourloginname/ksycoca*
```
```
rm ~/.DCOPserver*
```

Then Ctrl-Alt-F1 and 

```
sudo /etc/init.d/kdm restart
```

---

### Post by martin_legion on 2007-04-29
Same problem here.
I tried those commands but no change.
The first file wasn't found. Neither kdm because I use gdm and Gnome as default.
Any ideas?

---

