---
title: "terminal won't open"
date: 2006-08-17
forum: General Help
---

### Post by Athanasius on 2006-08-17
Everything was working well this morning and I turn on my pc and now clicking on the terminal icon doesn't open the terminal.  What is the deal with that?

---

### Post by zitch on 2006-08-18
I'm having the same problem here too.  I'm running Quinnstorm's Compiz, and it upgraded my gnome-terminal and several libraries.  It was running fine for a while until I upgraded a few more libraries a few minutes ago.  Opening up xterm (Press Alt-F2 and enter in xterm to pull up the window) and running "gnome-terminal" gives the following error:

```
gnome-terminal: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
```

Doing a "whereis libvte.so.4" returns:
```
libvte.so: /usr/lib/libvte.so.9
```

Thanks in advance for any help.

**********************

UPDATE: Running the following in xterm: 
```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

seems to work for now.  gnome-terminal will now load up successfully.  I will test this some more, as running gnome-terminal from xterm will return the following warning:
```

** (gnome-terminal:8764): WARNING **: can not run /usr/lib/libvte4/gnome-pty-helper

```

Again, though, gnome-terminal will load.

Please advise of any side effects of doing this.

Small update:  I've looked up the libvte4 package in synaptic, and this is where it seems to install the libvte9 libraries.  There looks like a /usr/lib/libvte9 directory installed.  Would it hurt to create a soft link to it from /usr/lib/libvte4?  Is it even necessary?  I will be holding off on this unless I get further problems or if there's a good reason to go ahead and do this.

Thanks.

*****************

FINAL UPDATE: See posts below.

---

### Post by huwshimi on 2006-08-18
Another update just fixed this for me.

---

### Post by zitch on 2006-08-18
Affirmative.  Just removed the /usr/lib/libvte.so.4 softlink I created, ran apt-get upgrade, and gnome-terminal is running without the link.

---

### Post by nemesa on 2006-08-18
I have the same problem, but since yesterday morning I can't reach the Quinnstorm's Compiz repositories... So I can't upgrade...

Is there anybody, who has this problem?

---

### Post by nemesa on 2006-08-18
I've got it.

---

### Post by sumadartson on 2006-08-18
Would this help?

[http://ubuntuforums.org/showpost.php?p=1390817&postcount=13](http://ubuntuforums.org/showpost.php?p=1390817&postcount=13)

---

### Post by Athanasius on 2006-08-18
It is now fixed.  It seems like there was a problem with the beerorkid repository and everything is working fine right now.

---

