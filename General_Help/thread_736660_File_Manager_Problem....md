---
title: "File Manager Problem..."
date: 2008-03-26
forum: General Help
---

### Post by CreativeName5 on 2008-03-26
I don't know how it happened but whenever I open up a File Manager window in GNOME it automatically goes full screen and covers over everything (panels, etc.) and there is no window bar at the top to do anything, It's really annoying and I would like to get it back to how it was before, any help would be greatly appreciated, thanks!

-Sean

---

### Post by jken146 on 2008-03-26
Alt+left click and drag will allow you to move the window.

---

### Post by lemonlaw95 on 2008-03-26
I have no idea what's wrong with it. :confused:
But you could try this: (You will have to reboot or ctrl+alt+backspace after this.  More likely the latter.)
```
sudo apt-get purge nautilus
``` (It will automatically get rid of nautilus-cd-burner)
To remove it, and then:
```
sudo apt-get install nautilus
``` (Which will automatically reinstall nautilus-cd-burner)
To reinstall it.  And as far as I know, that should cut it.  If not, (and that may very well be so. :) you could try only removing nautilus, but you might have to use synaptic, I don't know the command to ignore dependant packages. :(
And downloading and installing this package:  (I am assuming you are on Gutsy i386)
[http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.22.0-0ubuntu3_i386.deb]("http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.22.0-0ubuntu3_i386.deb")
And if that doesn't work, I am truly out of ideas.

---

### Post by lemonlaw95 on 2008-03-26
> **jken146 said:**
> Alt+left click and drag will allow you to move the window.
I didn't think of that... :) Did that fix your problem?

---

