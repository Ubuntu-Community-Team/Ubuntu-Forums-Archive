---
title: "Nautilus file browser window-- how to get column sizes to stick??"
date: 2007-08-29
forum: General Help
---

### Post by herbster on 2007-08-29
First pic is how the columns are everytime I open a file browser window. Second is how I'd prefer it to be. I can't find any way to make it "default" or have it open this way each time.

[IMG]http://www.bobgill.net/columnsdefault.jpg[/IMG]

[IMG]http://www.bobgill.net/columns.jpg[/IMG]

TIA for any help! :)

---

### Post by praet on 2007-08-30
This seems to be a bug. See the following:
[https://bugs.launchpad.net/nautilus/+bug/93381](https://bugs.launchpad.net/nautilus/+bug/93381)

You may be interested in applying some workaround patches to nautilus in the meantime (bottom):
[http://bugzilla.gnome.org/show_bug.cgi?id=410361#c6](http://bugzilla.gnome.org/show_bug.cgi?id=410361#c6)

---

### Post by notwen on 2007-08-30
Nautilus and defaults are not meant to be, I've installed [PCManFM]("http://pcmanfm.sourceforge.net/").  It tends to maintain visual settings better for me plus it offers tabs.  I like to think of it similar to Thunar+Tabs.

---

### Post by herbster on 2007-08-30
Okay, I see the patch in that thread, when I click it the text shows up. Where do I paste that? I have no idea what to do with it, how to "apply" the patch.

---

### Post by praet on 2007-08-30
To apply a patch you need to download the complete sources, in this case "nautilus-2.18.0.1"
and apply the patch to the source, then compile the changed program.

Into to patching:
[http://www.cpqlinux.com/patch.html](http://www.cpqlinux.com/patch.html)

Get the sources:
```
sudo apt-get source nautilus
```

make the changes to the file:
"nautilus-2.18.0.1/src/file-manager/fm-list-view.c"

```
patch -p1 patchfile
```
-b  : backup changed files
--dry-run :  add this if you want to test the patch and not apply it just yet.

Then recompile based on the readme (sudo checkinstall / [sudo]  make && make install).

---

### Post by herbster on 2007-09-01
praet,

Thank you so much, your help is greatly appreciated! This will do until a real solution is integrated into nautilus [if ever?].

---

### Post by oomingmak on 2007-09-01
> **herbster said:**
> This will do until a real solution is integrated into nautilus [**if ever**?].

:lolflag:

---

### Post by NJC on 2008-01-23
> **praet said:**
> This seems to be a bug. See the following:
[https://bugs.launchpad.net/nautilus/+bug/93381](https://bugs.launchpad.net/nautilus/+bug/93381)

 
And Nautilus still doesn't remember column width changes after window is closed, as per bug filed in above link. Oh well, maybe in 8.04 the fix will be implemented as I'm sure they're doing the best they can.

---

