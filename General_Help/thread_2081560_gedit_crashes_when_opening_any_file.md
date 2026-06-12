---
title: "gedit crashes when opening any file"
date: 2012-11-07
forum: General Help
---

### Post by fruitz on 2012-11-07
hi all.

unfortunately my gedit is unusable, since every time i try to open a text file, it crashes.

here the terminal message 
```
TypeError: metaclass conflict: the metaclass of a derived class must be a (non-strict) subclass of the metaclasses of all its bases
**
ERROR:/build/buildd/pygobject-3.4.0/gi/_gobject/pygobject.c:946:pygobject_new_full: assertion failed: (tp != NULL)
Aborted (core dumped)

```the last thing i (regret) did before the problem appeared, was enabling the dialog of the source code browser plugin

[https://github.com/Quixotix/gedit-source-code-browser](https://github.com/Quixotix/gedit-source-code-browser)

any help would be very appreciated!! thanks!

---

### Post by SlugSlug on 2012-11-07
try moving out the files in
 ~/.gconf/apps/gedit-2 
or 
~/.config/gedit

---

### Post by fruitz on 2012-11-07
there is no folder named
~/.gconf/apps/gedit-2 
and even after removing the folder 
~/.config/gedit 	
and rebooting nothing is solved.

---

### Post by SlugSlug on 2012-11-07
check output from

```
find ~/ -iname gedit*
```
Have you tried a purge and reinstall?

```
sudo apt-get remove --purge gedit  
```
```
sudo apt-get autoremove
```
```
sudo apt-get install gedit
```

---

### Post by fruitz on 2012-11-07
```
francesco@francesco-wimdu:~$ find ~/ -iname gedit*
/home/francesco/Downloads/geditpycompletion-master.zip
/home/francesco/.local/share/gedit
/home/francesco/.local/share/Trash/files/gedit
/home/francesco/.local/share/Trash/files/gedit/plugins/gedit_classbrowser-0.2.1
/home/francesco/.local/share/Trash/files/gedit/plugins/geditpycompletion-master
/home/francesco/.local/share/Trash/files/gedit.2
/home/francesco/.local/share/Trash/files/plugins/gedit_classbrowser-0.2.1
/home/francesco/.local/share/Trash/files/plugins/geditpycompletion-master
/home/francesco/.local/share/Trash/info/gedit.2.trashinfo
/home/francesco/.local/share/Trash/info/gedit.trashinfo
/home/francesco/.config/gedit

```

purging and reinstalling didnt do the trick :(

---

### Post by SlugSlug on 2012-11-07
am not sure so wait for someone else to comment but the next step I'd take is

```
sudo mv /usr/share/glib-2.0/schemas/org.gnome.gedit.plugins.sourcecodebrowser.gschema.xml ~/Desktop/
```  ```
glib-compile-schemas /usr/share/glib-2.0/schemas/
```

---

### Post by fruitz on 2012-11-07
yes. tried it. same error when opening file 

```
ERROR:/build/buildd/pygobject-3.4.0/gi/_gobject/pygobject.c:946:pygobject_new_full: assertion failed: (tp != NULL)
Aborted (core dumped)

```

---

### Post by Habitual on 2012-11-07
Create a new user on the host and login as that user, then run/check gedit.
Same issue, or no issue?

---

### Post by fruitz on 2012-11-07
good point. the problem is only with my account apparently

---

### Post by sienile on 2012-11-07
Are you **_100% sure_** there's no **~/.gconf/apps/gedit-2** directory? It *should* exist.

One more place to look for rogue files is **~/.local/share/applications**. You might find some files named **gedit-#.desktop**. They should be harmless, but that's all I can think of for an issue only affecting 1 user.

Another very unlikely culprit is **~/.config/gnome-panel/launchers**, which might have another **gedit.desktop**, if you have a panel launcher for gedit. Again, I don't think this should pose a problem, but it's somewhat possible.

---

### Post by fruitz on 2012-11-07
[B]~/.local/share/gedit

[/B]found it. Thanks a lot!

---

### Post by sienile on 2012-11-07
I went looking around for info about your error and I'm leaning to the possibility that your python lib packages may be corrupt. Specificly, **python-gobject** and **python-gobject-2**.

Fire up Synaptic and mark both of those for reinstall. You may also want to reinstall **python-gtk2** and **python-gi**, which are related packages.

I would recommend trying the other suggestions above before doing this, as it seems you have a more recent version [3.4] than the one I'm running [3.2] (possibly needed for some other package?). If it doesn't work after reinstall, try purging the packages (if it will let you do it without uninstalling a ton of stuff you might need) before another reinstall.

If it works, let us know what you had to do so that if anyone else has this problem they can solve it. It seems PyGObject errors are more common in Rythmbox than gedit.

EDIT: Seems you found the problem while I was typing this monster up. Good job!

---

