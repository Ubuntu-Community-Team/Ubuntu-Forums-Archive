---
title: "Update manager problem!"
date: 2006-07-14
forum: General Help
---

### Post by Honeybee on 2006-07-14
Hello everyone!

First post here... I have been using Ubuntu at work now for most of this year and I am loving it. I have one small problem that I have not been able to solve and I am wondering if any of you kind folks can help.

This problem cropped up after I upgraded from Breezy to Dapper. It's not so much a problem, just an annoyance. Whenever I run Synaptic or the update manager, I get a window pop up which says:

> Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.
The following updates will be skipped:

gdk-imlib1

I've tried using the Mark All Upgrades function, and the console command and neither of them solve the problem.  Can I manualy uninstall the package and install the later version, or will this break things?

Thanks people!

J

---

### Post by mlind on 2006-07-14
By looking at the package description it's probably one you don't need. Install application called **deborphan** and consider removing packages it suggests (except if list contains gstreamer packages). You can also try just removing it with aptitude and see if it would break some dependencies.

I reckon it's a leftover from Breezy upgrade or something?

---

### Post by OpsVentus on 2006-07-14
What does synaptic/apt-get tell you when you try to install 'gdk-imlib1'?
Normally then synaptic will tell you which other package is giving the trouble.
If not you can have a look at the dependencies of the package.

Cheers,
Bart.

---

### Post by Honeybee on 2006-07-14
Hi thanks for the help.

The package is already installed, but the version I have is 1.9.14-16.2ubuntu4, and the newer version (which I assume it wants to install but something is stopping it) is 1.9.14-29ubuntu1.  There are a lot of things that depend on this package, they all have names beginning with lib such as libjpeg62 and libgtk1.2 etc.  There are a lot of them.

Can I force it to upgrade to the latest version of gdk-imlib1? Or might that be a bad plan? :)

Thanks for the help, I really appreciate it!

---

### Post by OpsVentus on 2006-07-14
Yes, try to upgrade this package. Most likelly it will give an error. But one which leads us closer to the problem.

Cheers,
Bart.

---

### Post by Honeybee on 2006-07-14
Hello,

Trying to force the version change will do the following, it will remove libpng10-0

> PNG library, older version - runtime
libpng is a library implementing an interface for reading and writing
PNG (Portable Network Graphics) format files.

This package contains legacy runtime libraries needed by programs
accessing PNG files.

URL: [http://www.libpng.org/pub/png/libpng.html](http://www.libpng.org/pub/png/libpng.html)

I am not sure anyone will know for certain, but will it be ok to remove that package? or will I lose the ability to view PNG files! :)

Thanks

J

---

### Post by mlind on 2006-07-14
If you look the output of aptitude show gdk-imlib1, especially the Conflicts line - you'll notice that those two packages cannot be installed at same time.

Did you try removing the gdk-imlib1 package using aptitude and see what resolution it offers?

---

