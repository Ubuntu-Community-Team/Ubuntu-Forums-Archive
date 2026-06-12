---
title: "Help with creating a launcher"
date: 2007-02-22
forum: General Help
---

### Post by mariposa on 2007-02-22
I have just installed jEdit using the generic Java based installer.  The thread in these forums that described the method talked about creating a new launcher.

The installation process, which did not go through the Synaptic package manager, produced a shell script containing the equivalent operational text that was described for the "new launcher."  I am unclear how to turn a shell script into a launcher, given its common usage.  That would be something that I can click to invoke the executable and which can be added to menus on the Ubuntu descktop.

Searching various sources for "launch" and "launcher" does not produce that information.  Any thoughts?

Thanks.

---

### Post by Maestro23 on 2007-02-22
Open termial, type:

> which jedit

What does it return? Should give you the path to the .bin(executable).

Use this path in creating a launcher/menu item.

Should be able to right-click on desktop and get option to create a launcher.

---

### Post by mariposa on 2007-02-22
Thanks, that's it.  I'm not venturesome enough, never tried right-clicking on the desktop.

---

### Post by Maestro23 on 2007-02-22
> **mariposa said:**
> Thanks, that's it.  I'm not venturesome enough, never tried right-clicking on the desktop.

Glad to help.:)

---

