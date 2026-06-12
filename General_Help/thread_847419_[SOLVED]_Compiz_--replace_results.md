---
title: "[SOLVED] Compiz --replace results"
date: 2008-07-02
forum: General Help
---

### Post by gettinoriginal on 2008-07-02
I cannot get all the effects from compiz to work properly.  The results of Compiz --replace are:
gettin@gettinscomputer:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
inotify_add_watch: No such file or directory
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

How do I find the value and what to remove ???

---

### Post by ajgreeny on 2008-07-02
If you've got ccsm open it with **System>>Preferences>>Advanced Desktop Effect Settings** in the menu and make sure the scale plugin is not enabled.  That may help, though I used to get quite a few of those error messages in .xsession-errors in my home folder, but it never stopped compiz running, so there may be another problem unrelated to that.  It could be worth getting compiz-check from forlong's site which can fix some problems, or at least tell you how to do so.  Go [here]("http://forlong.blogage.de/article/pages/Compiz-Check") to get it.

---

### Post by prshah on 2008-07-02
> **gettinoriginal said:**
> 

gettin@gettinscomputer:~$ compiz --replace
Checking for Xgl: not present. 



It's likely that your system is not properly optimised for Compiz. Most likely you do not have direct rendering; check with ```
glxinfo | grep -i direct
``` If it shows "No" to direct rendering, install the following package, then check again:

```
sudo apt-get install xserver-xgl
```

---

### Post by gettinoriginal on 2008-07-02
Went to forlongs site, but the file will not load, says "failed".  And yes, I do have direct rendering.  But thank you all for your help, it's appreciated.

---

### Post by psyopper on 2008-07-03
Try running it in the "Flatfile" backend....

Open CCSM and click on the Preferences button (lower left). On the Profile & Backend tab select Backend: Flatfile Configuration Backend.

---

### Post by gettinoriginal on 2008-07-03
Thanks for your response, but flatfile reset all my compiz settings to default, and then froze my computer so I couldn't change anything. :confused:

---

### Post by psyopper on 2008-07-03
Did it freeze the computer? Or did it just not have the "move windows" plugin enabled?

I forgot that the flatfile would reset all of your configuration options. It used to "migrate" them from the gconf backend IIRC. Or maybe it was the other way around, going from flatfile to gconf migrated your settings into gconf.

The nice thing about the flatfile is that CCSM never chokes on duplicate bindings and the CCSM bindings wind up taking precedence over the Gconf bindings. 

The downside is that Compiz isn't as well integrated into Gnome in that it doesn't present as much of a universal installation for Distro makers - IE Ubuntu's "Desktop Effects" and the integrated method in which they are set up.

---

### Post by gettinoriginal on 2008-07-03
Sorry, had to go to work.  No, it froze the page, no launchers would work.  It took me from 4 workspaces to 2, and wouldn't go to the other one.  Anyway, I will just be satisfied with the options I have working, and consider this solved ):P

---

### Post by prshah on 2008-07-04
> **gettinoriginal said:**
> Sorry, had to go to work.  No, it froze the page, no launchers would work.  It took me from 4 workspaces to 2, and wouldn't go to the other one.  Anyway, I will just be satisfied with the options I have working, and consider this solved ):P

As a last attempt, install the xserver-xgl package as in my previous post; if that doesn't work, then you can walk away with the satisfaction of leaving no stone unturned...

---

