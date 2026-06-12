---
title: "restoring terminal colors to default"
date: 2014-12-11
forum: General Help
---

### Post by kamhagh on 2014-12-11
Hi, i was changing terminal colors too see how they look and chose one, i only pressed apply, now i see the default themes have changed to my setting even after i pressed cancel ! i hate this look i want to go back to default, but the default theme has my colors in profile! how can i change it do default !?

edit: i have konsole not gnome-terminal i could make gnome terminal the default one i love them both!

---

### Post by ajgreeny on 2014-12-11
I think that somewhere in the hidden .kde folder in your home (maybe  ~/.kde/share/config/) there will be a configuration file for the terminal theme you have now made and do not like, possibly called **konsolerc**.
If you send that file to trash, or rename it as a backup with a right click, then restart konsole it may return to the default for your system.

I do not use kde, nor do I have konsole on my system, so I admit this is a stab in the dark, but if you keep the original file you trashed or renamed it is an easy job to restore it.

Good luck!

---

### Post by vasa1 on 2014-12-11
I find files which have changed in my home folder by means of```
alias 5m='find ~/ ! -path "*mozilla*" ! -path "*google-chrome*" ! -path "*cache*" ! -path "*dropbox*" -mmin -5 -type f -ls'

```I've excluded certain folders to speed things up a bit.

So the way I'd now find the file which was changed is to repeat the whole thing, just like the man of Gotham whose cheese rolled downhill, and then immediately run the find code. Then, as ajgreeny said, just trash that file. You may need to log out and back in to see the change.

---

### Post by kamhagh on 2014-12-11
thanks ! you're a life saver :D

---

