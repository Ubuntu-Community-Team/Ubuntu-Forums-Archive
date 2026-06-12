---
title: "[SOLVED] Setting GDM back as  login manager"
date: 2007-11-14
forum: General Help
---

### Post by warnec on 2007-11-14
Hello. I've recently installed SLiM and wanted to see if it would be a nicer login manager than GDM. Afer installing I've chosen that slim should be default login manager, and rebooted. After that (next login into the system) I've got a login screen with a theme with debian logo and of course a place to write my login. On bottom it was written "xfce4" or something like that. I didn't want my WM to be xfce, cause i've only got gnome installed (Ubuntu 7,10) There was said "click F10 to change session" or something like that. I clicked it a few times, and i remembered there were fxce4 and icewm (or something like that) and a few others, but no gnome, or even KDE! I finally chose xfce and there was and error that wm wasn't found and loading  default one. Then i got my gnome desktop, but in english (i've installed polish language before and it worked) and in bad resolution. My normal resolution wasn't available. I didn't like it, so i decided to remove it (slim package). Everything should be ok, but now i've got text  login.I  type my login and pass, then type "startx" and have my linux desktop, and it's a little bit annoying. I can of course login in text, then type "sudo gdm" and login graphically, but that's still annoying. How can i set gdm to load automatically with booting of the system?

---

### Post by por100pre1 on 2007-11-14
Try this:

```
sudo dpkg-reconfigure gdm
```

```
sudo /etc/init.d/gdm start
```

---

### Post by jetsam on 2007-11-14
It's kind of a kludge, but if you install kdm and already have gdm installed, a curses interface comes up which asks  you which display manager you want as default, so maybe try:

```
sudo apt-get install kdm
```

And then pick gdm as your default display manager...

If it works, you can  [FONT="Fixedsys"]**sudo apt-get remove kdm**[/FONT] afterwards and gdm should still be set as the default display manager.  

I'm sure there's a more direct way to do this, but I don't know Ubuntu well enough to know what it is...

Be careful not to remove gdm, as ubuntu desktop will be removed as well...  That would be bad.

---

### Post by bodhi.zazen on 2007-11-14
You can either edit /etc/X11/default-display-manager

(to find the path you can use locate or which kdm or locate or which gdm)

Or you can sudo dpkg-reconfigure gdm

Which will bring up a menu where you can select.

To use the menu use the keyboard (not the mouse) using the up/down arrow keys, tab key, and enter.

[img]http://www.howtogeek.com/wp-content/uploads/2006/12/WindowsLiveWriter/HowtoSwitchBetweenGDMandKDMonUbuntu_6751/configgdm.png[/img]

---

### Post by por100pre1 on 2007-11-14
> **bodhi.zazen said:**
> You can either edit /etc/X11/default-display-manager

(to find the path you can use locate or which kdm or locate or which gdm)

I didn't know that one, thanks. That's why I love these forums! :)

---

### Post by warnec on 2007-11-15
Thank you people for help!
```

maciek@maciek-ubuntu:~$ sudo dpkg-reconfigure gdm
[sudo] password for maciek:
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
maciek@maciek-ubuntu:~$ 

```

After reboot will see if it worked. That's why i love these forums: fast reply and helpful users. On polish forum nobody could help me ;)

---

### Post by warnec on 2007-11-15
Ok, problem fully solved, thank you.

Topic ready to be closed.

---

