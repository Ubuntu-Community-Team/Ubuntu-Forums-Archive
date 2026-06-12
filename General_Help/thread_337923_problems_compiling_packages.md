---
title: "problems compiling packages"
date: 2007-01-13
forum: General Help
---

### Post by Pollywoggy on 2007-01-13
I have used Debian for approx 8 years, so I am familiar with how to compile kernels and packages and such, just so you know I am not a total newbie.  I have used Linux for almost 10 years.

I just installed Kubuntu Edgy Eft two days ago and I have some problems with compiling packages.

In the Ubuntu Wiki, I found some instructions for getting rt2500 wifi to work, and the wiki gives this command:

gksudo file-roller

When I execute that command I get this:

(gksudo:5997): Gtk-WARNING **: cannot open display:

Is this related to Xauthority?  How can I fix that?

I also found that I need to be root to download deb-src packages, very strange but okay.

Once I get a deb-src package downloaded and I cd to the directory, I do:

dpkg-buildpackage -rfakeroot 
    but the compile gives me permissions errors.  Once I su to root I do not have trouble compiling the package.

Can anyone give me a clue as to this fakeroot problem?

---

### Post by ajmorris on 2007-01-13
> **Pollywoggy said:**
> 
I also found that I need to be root to download deb-src packages, very strange but okay.

Once I get a deb-src package downloaded and I cd to the directory, I do:

dpkg-buildpackage -rfakeroot 
    but the compile gives me permissions errors.  Once I su to root I do not have trouble compiling the package.

Can anyone give me a clue as to this fakeroot problem?

Does -rfakeroot work in Ubuntu? It is probably easier to use the "sudo command" (i.e. sudo dpkg-buildpackage)

---

### Post by ajmorris on 2007-01-13
> **Pollywoggy said:**
> 

gksudo file-roller

When I execute that command I get this:

(gksudo:5997): Gtk-WARNING **: cannot open display:

Is this related to Xauthority?  How can I fix that?


When i get a gtk error i use dbus-launch. so maybe try "dbus-launch gksudo file-roller"

Hope that helps.

---

### Post by Pollywoggy on 2007-01-13
> **ajmorris said:**
> Does -rfakeroot work in Ubuntu? It is probably easier to use the "sudo command" (i.e. sudo dpkg-buildpackage)

It didn't work for me.  I will use sudo instead.

thanks

---

### Post by Pollywoggy on 2007-01-13
> **ajmorris said:**
> When i get a gtk error i use dbus-launch. so maybe try "dbus-launch gksudo file-roller"

Hope that helps.


dbus-launch gksudo file-roller

(gksudo:30055): Gtk-WARNING **: cannot open display:

I asked about this on IRC and someone asked if I had configured xorg.  I am not sure what that means I never had to configure it before except when using an Nvidia card.

---

### Post by Pollywoggy on 2007-01-13
> **Pollywoggy said:**
> dbus-launch gksudo file-roller

(gksudo:30055): Gtk-WARNING **: cannot open display:

I asked about this on IRC and someone asked if I had configured xorg.  I am not sure what that means I never had to configure it before except when using an Nvidia card.


I think I found the problem.  I am using kubuntu, so I should not use gksudo, I should use kdesu.

---

