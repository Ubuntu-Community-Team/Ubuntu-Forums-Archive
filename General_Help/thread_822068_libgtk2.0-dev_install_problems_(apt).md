---
title: "libgtk2.0-dev install problems (apt)"
date: 2008-06-07
forum: General Help
---

### Post by FFighter on 2008-06-07
I'm trying to install libgtk2.0-dev in order to compile google gadgets, but a strange error is preventing me from doing that:

> 
The following packages have broken dependencies:
libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.12.9-3ubuntu4) but 2.12.9-4ubuntu3 will be installed
E: Broken Packages


Sorry if this isn't exactly what the en-us locale strings show, I just translated from my locale to english.

When I try to apt-get install libgtk-dev which seems to be a meta-pacakge (?) apt then tries to install the 1.2 version of the package, which installs fine but is not compatible with google gadgets.

I'm on Hardy.

Could someone give me a light here?

Thanks,

Marcelo.

---

### Post by wolfen69 on 2008-06-07
try [THIS]("http://packages.ubuntu.com/hardy/i386/libgtk2.0-0/download")

---

### Post by FFighter on 2008-06-07
Hi wolfen69, thanks for the reply.

The package manager throws the following error when I try to install the libgtk2.0-o deb:

"Error: A newer version is already installed."

I also tried downloading the libgtk2.0-dev deb and another error is thrown when I try to install it:

"Error: Dependency is not satisfiable: libgtk2.0-0"

It seems the version of libgtk2.0-0 I have installed is somewhat a not compatible one. I don't really understant the "3ubuntu4" and "4ubuntu3" prefix, they look like greek to me. 

I thought on uninstalling libgtk2.0-0 and re-installing it, however, when I tried to do it via apt-get, the amount of software that apt told me would get uninstalled in effect to the libgtk2.0-0 unistall would surely break my system - is it safe to unistall and install it again? Could that solve the problem?

---

### Post by mc4man on 2008-06-07
Did you install gnome-globalmenu ?

---

### Post by FFighter on 2008-06-08
Hello, mc4man, thanks for replying,

As a matter of fact, yes. Thanks for pointing this out, I haven't remembered earlier.

How could I solve this situation?

---

### Post by mc4man on 2008-06-08
From what i see there's a group of 6 packages, did you install all of them?

---

### Post by FFighter on 2008-06-08
Yes, I guess so.

---

### Post by mc4man on 2008-06-08
Here's the packages

gtk2-engines-pixbuf
libgtk2.0-bin
gnome2-globalmenu-applet
libgtk2.0-common
gtk2.0-example
..................
libgtk2.0
.............
I could only approach this logically (no direct knowledge here)
What I'd do is go through the the list _in synaptic _(the top 5) and see if I could remove the first 5 packages without removing anything else other than itself and any of the other packages in the group of 5.(unless it was an odd non critical package) The order may or may not matter. If that could be done then _I would think_ about trying to _force the version_ of libgtk2.0 back to the hardy version
You mat want to wait for someone a bit more knowledgeable.
Or I could try it out tomorrow on a test box

Edit: the order I listed them in is best guess of order to remove

---

### Post by Unix_Slayer on 2008-06-08
libgtk2 and list of dependencies <=== [http://packages.debian.org/unstable/libs/libgtk2.0-0]("http://packages.debian.org/unstable/libs/libgtk2.0-0")

And check this one. <==== [http://packages.debian.org/etch/libgtk2.0-dev]("http://packages.debian.org/etch/libgtk2.0-dev")

Also check this thread. <=== [http://ubuntuforums.org/showthread.php?t=270959]("http://ubuntuforums.org/showthread.php?t=270959")


I think I had the same problems yesterday when I installed Google Gadgets. I've got it up and running. I think it might be a variant of pango or pycairo. I figured out from the top two links. Good Luck.

P.S. throw these links in as a good measure.

[http:/http://www.icewalkers.com/Linux/Software/515970/GTK2.html]("http:/http://www.icewalkers.com/Linux/Software/515970/GTK2.html")
[http://www.gtk.org/]("http://www.gtk.org/")
[http://gtk2-perl.sourceforge.net/]("http://gtk2-perl.sourceforge.net/")

Oh yeah.... install glade from adept manager/synaptic manager.

---

### Post by FFighter on 2008-06-08
> Here's the packages

gtk2-engines-pixbuf
libgtk2.0-bin
gnome2-globalmenu-applet
libgtk2.0-common
gtk2.0-example
..................
libgtk2.0
.............
I could only approach this logically (no direct knowledge here)
What I'd do is go through the the list in synaptic (the top 5) and see if I could remove the first 5 packages without removing anything else other than itself and any of the other packages in the group of 5.(unless it was an odd non critical package) The order may or may not matter. If that could be done then I would think about trying to force the version of libgtk2.0 back to the hardy version
You mat want to wait for someone a bit more knowledgeable.
Or I could try it out tomorrow on a test box

Edit: the order I listed them in is best guess of order to remove

Forcing the hardy version for libgtk2.0-0 solved the problem. 

After doing this, I just installed libgtk2.0-dev successfully (which I couldn't install earlier, when I had the global menu hacked libgtk2.0-0) and then Google Gadgets could compile the GTK host. Success!

So, the problem turned out to be how to uninstall the Global Menu hacked libgtk2.0-0. Your instructions were fine, **forcing the hardy version of libgtk2.0-0 solved my problem** (as the dependencies were also updated to the hardy version). 

More details on uninstalling Global Menu can be found in the following link, if anyone is interested: [https://wiki.ubuntu.com/global_menu#uninstall](https://wiki.ubuntu.com/global_menu#uninstall).

Thanks for helping!

---

### Post by lumix700i on 2008-07-17
I tried to follow the instructions, but as I tried forcing the hardy version, I've got warning messages that some of other packages were also going to be removed, such as audacious, gnome themes, and also ubuntu-desktop. I'm not sure about this so I cancelled it.. What do you think?

---

