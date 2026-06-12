---
title: "missing toolbar.."
date: 2008-04-30
forum: General Help
---

### Post by mkquist on 2008-04-30
Hey all, just today logged on and found the upper tool bar that has the maximize/minimize/close button to be missing.  Cant drag items around the desktop either.  Only happens when the desktop effects is turned on.  Any help would be appreciated...

---

### Post by warbread on 2008-04-30
First, try pressing ALT+F2 and the typing 

```
:-$ metacity --replace
```

If that doesn't work, you need to make sure you have the 'Windows Decorations' option enabled in your Compiz settings manager.

---

### Post by mkquist on 2008-04-30
Well thank you, that seems to have done it.  What did it do actually?
I thought it did, but no, upon checking the effects, no go.
and the 'windows decorations' is enabled... =( so sad, everything worked before.

---

### Post by warbread on 2008-04-30
The problem is that your windows decorator isn't running.  Go to System -> Preferences -> Sessions and add 

```
metacity --replace
```

If you want to use emerald, make sure you have it installed and add:

```
emerald --replace
```

to your sessions list.

---

### Post by mkquist on 2008-05-01
Ok, seem to have it solved with help from this thread 
[http://ubuntuforums.org/showthread.php?t=372966](http://ubuntuforums.org/showthread.php?t=372966)

in particular the commands:

sudo apt-get install nvidia-glx
sudo nvidia-xconfig --add-argb-glx-visuals
sudo reboot

Woot, do like the cube and all....

---

