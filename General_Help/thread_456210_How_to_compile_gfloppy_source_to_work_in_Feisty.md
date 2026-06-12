---
title: "How to compile gfloppy source to work in Feisty"
date: 2007-05-27
forum: General Help
---

### Post by fable on 2007-05-27
I found out that gfloppy is missing in Feisty.  Since I don't like to use command mode, I want to get the gfloppy gui compile from source.

If I download the gfloppy source from gnome, how do I compile the source to binary for use in Feisty?

---

### Post by MoLE on 2007-06-02
On my install of Feisty, it appears that gfloppy in included in the gnome-desktop-utils package.  What are you trying to do with it that won't work through the GUI?

---

### Post by click4851 on 2007-06-04
I have to agree with fable, after installing gnome-desktop-utils  and anything even remotely related to gnome-utils. Gfloppy is a none starter, I chickened out and loaded up kfloppy.

---

### Post by fable on 2007-06-05
I installed gnome-desktop-utils the normal way, i.e., using Synpatic.  Nothing special.  Installation seems to be fine.  Just gfloppy is missing.  I don't mind learning to compile gfloppy from source if someone tells me how.

---

### Post by MoLE on 2007-06-05
My apologies.
On closer inspection, it appears that the gnome-utils package for ubuntu feisty is built without gfloppy enabled.  Have a look at /usr/share/doc/gnome-utils/README.

I'm not sure if there's a reason why gfloppy isn't included by default.  My suggestion would be to lodge a bug report for the gnome-utils package.

If you want to have a go at building a debian package from source, there is a fairly clear howto at [http://doc.gwos.org/index.php/Deb_Guide](http://doc.gwos.org/index.php/Deb_Guide)

There may be a simpler way to do it, though - as the debianised source is already in the repositories (gnome-utils is a core package, after all).  My guess is that the package can be rebuilt simply, but with the gfloppy code enabled.

I'm not skilled enough in this area to be able to guide you, however.  Hopefully someone else here can help out.

I'm still wondering what functionality you want that nautilus doesn't provide by default for floppy disks?  What are you wanting to do with gfloppy that you can't already do?

---

### Post by Juno on 2007-06-15
Check this: [http://forum.ubuntuusers.de/topic/89257/next/](http://forum.ubuntuusers.de/topic/89257/next/)

Gnome utils, include gfloppy >> [http://home.arcor.de/binaerspuele/debian/feisty/gnome-utils_2.18.0-0ubuntu3_i386.deb](http://home.arcor.de/binaerspuele/debian/feisty/gnome-utils_2.18.0-0ubuntu3_i386.deb)

---

### Post by i M@N on 2008-01-01
Hello.

Many thnxX Juno ... i've been searching for this for months !

Ubuntu should include gfloppy in the next version as it's really an awesome GUi tool.

@+...

---

