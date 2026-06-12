---
title: "X Server, my error!"
date: 2008-02-08
forum: General Help
---

### Post by Connelley on 2008-02-08
I was looking around the desktop for Gnome - 7.10 Gutsy.  I went to System > Administration > Login Window > Security.  I clicked on Configure X, and then foolishly wondered, what Greeter vs. Chooser was all about.  I selected Chooser, and restarted the computer.  I now get a window to choose a Server, and since I don't know what to add, I can't get logged in!
How do I get out of this mess?  Thanks for any help!

Connelley

---

### Post by taurus on 2008-02-08
You can try logging in into a console, <Ctrl><Alt>F2, and then stop GUI login screen and start Gnome by hand with

```
sudo /etc/init.d/gdm stop
startx
```
Now, go back and undo whatever you did before.  Then, exit Gnome and restart GUI login screen again with

```
sudo /etc/init.d/gdm start
```

---

### Post by Connelley on 2008-02-08
> **taurus said:**
> You can try logging in into a console, <Ctrl><Alt>F2, and then stop GUI login screen and start Gnome by hand with

```
sudo /etc/init.d/gdm stop
startx
```
Now, go back and undo whatever you did before.  Then, exit Gnome and restart GUI login screen again with

```
sudo /etc/init.d/gdm start
```

Thanks for your prompt reply.
However, after following your instructions, when I get to the desktop, and select System > Administration, the' Login Window' choice has disappeared!  Therefore, I can't simply correct my error.
Sorry I'm so ignorant.  I think I'm learning a valuable lesson. "Don't tread on what you don't understand!"

Connelley

---

### Post by forrestcupp on 2008-02-08
I don't know if this would apply, but you could boot to recovery and do a ```
sudo dpkg-reconfigure xserver-xorg
```

Maybe if you reconfigure it, it will reset that, too.

---

### Post by Connelley on 2008-02-08
> **forrestcupp said:**
> I don't know if this would apply, but you could boot to recovery and do a ```
sudo dpkg-reconfigure xserver-xorg
```

Maybe if you reconfigure it, it will reset that, too.

I did a reconfigure as per your suggestion, but I am still presented with the screen asking for hostname of the X server rather than the "Greeter option".  If I could get back to the Login Window where I originally screwed up, I think I could get out of the hole!
Thanks to all who have tried to help.

Connelley

---

### Post by Connelley on 2008-02-11
Being unable to resolve the problem, I did a fresh install.

Connelley

---

