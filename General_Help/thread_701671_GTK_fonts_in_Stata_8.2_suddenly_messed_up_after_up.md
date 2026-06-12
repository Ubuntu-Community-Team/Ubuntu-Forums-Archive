---
title: "GTK fonts in Stata 8.2 suddenly messed up after update"
date: 2008-02-19
forum: General Help
---

### Post by whakim on 2008-02-19
Hi,

After the recent updates this weekend, a number of things seem to have gone wrong with my Compaq Presario C751NR laptop running Gutsy. First, Firefox was messed up ([http://ubuntuforums.org/showthread.php?t=700846](http://ubuntuforums.org/showthread.php?t=700846)) & now, the fonts on a GTK application seem shrunken and illegible. 

The application in question is Stata 8.2, which was working perfectly up until 2 days ago. If I'm not mistaken Stata 8.2 uses GTK 1.0. Now, if I try to change the font or font size to make it legible, it sometimes crashes & sometimes allows a few changes (to the results pane, command window, variable view, & do-file editor) but then crashes if I try to change the viewer font. 

I ran the following set of commands as recommended to fix Firefox:

```
sudo dpkg-reconfigure libcairo2 libpango1.0-common
sudo fc-cache -fs
sudo update-pangox-aliases
```

Might this have caused the problem? I don't think I have any other pure GTK apps or I would have tested it on them. Gnome & KDE apps are fine. 

Thanks!

---

