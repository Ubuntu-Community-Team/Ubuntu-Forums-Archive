---
title: "OpenOffice.org2 in Debian start menu?"
date: 2005-05-13
forum: General Help
---

### Post by Krank on 2005-05-13
Hello everyone, my first post here.

Anyways, to the issue at hand:

I am not a Linux newbie, though not exacltly "Mr. Linux" either. I have worked with Debian on and off for a few years, learning enough to get by but not enough to actually make the darn thing do anything useful. Ubuntu, however, seems to change that - it's a real nice addition to my Linux collection.

The thing is, I dislike Gnome. I like Fluxbox. If you'd press me as to why this is, then i'd have to admit, grudgingly, that I am something of a minimalist, and Fluxbox/Blackbox always appealed, visually, to me. Also, they're really neat, function-wise.

When I installed Ubuntu, it came with OpenOffice.org 1.something. Since I've grown used to OpenOffice 2.0 in Windows (dual-boot. Duh.) I figured I should uninstall the old one, and install the new, shiny "2.0" I found on Universe. Said and done. I got OpenOffice 2.0, and I can even run it from Gnome's start menu. The problem is, that for some darn reason OOo2.0 does not appear in the Debian start menu used by Fluxbox. Tried reinstalling via Aptitude, tried reloading X-window, tried rebuilding the menu... Even tried rebooting the damn machine - nothing.

So, my questions are:

* Is this a common problem, or is my machine just messing with me?

* Is there anything I can do manually? I know I should learn to manually edit the menu files under /usr/lib/menu , but I just haven't gotten around to it just yet.

---

### Post by Krank on 2005-05-13
A small(ish) update:

I have now tried various solutions, to no avail.

I discovered the magic that is "custom menu files". I proceeded to read up a bit on the Debian menu system ([http://linux-cd.com.ar/manuales/debian-menu/index.html#contents)](http://linux-cd.com.ar/manuales/debian-menu/index.html#contents)). I wrote my own menu file, based on what I read and also what I found in the existing menu files in /etc/lib/menu ...

The resulting menu file was tried...

/usr/lib/menu - the icon showed up in the Debian menu of Gnome, but not the one in Black/Fluxbox.

/etc/menu - ditto.

/home/[username]/.menu - ditto.


So: I can make the item appear in the "Debian" section of Gnome - but NOT in the start menus of Blackbox/Fluxbox - how sick is that? Aren't they both supposed to be drawing their data from the same system - namely, the "menu" package?

BTW, here's my menufile:

```

?package(openoffice.org2-writer):\
    needs="x11"\
    section="Apps/Editors"\
    title="ooffice2 writer"\
    longtitle="OpenOffice.org 2.0 Writer"\
    icon="/usr/share/icons/gnome/32x32/apps/openofficeorg-19-writer.png"\
    command="/usr/bin/oowriter2"\

```

Oh, I've checked - the above file doesn't work, even when placed in the same dir as the default ones, with the same permissions as the other ones, and with the same owner/group as the other ones. I've tried removing the "icon" part, which changed nothing.

For reference, here's the file for Gedit, which works just fine:

```

?package(gedit):\
    needs="x11"\
    section="Apps/Editors"\
    title="Gedit"\
    longtitle="Light-weight GNOME text editor"\
    icon="/usr/share/pixmaps/gedit-icon.xpm"\
    command="/usr/bin/gedit"

```

The only thing - and I do mean the only thing - I can think of now is to see if I can duplicate this error with some other piece of software...


Am I going insane here?

---

### Post by Krank on 2005-05-14
Smallest-ish update: Just spotted that trailing "\" in my file, which doesn't exist in the other one. Didn't think it'd matter. Tried removing it, this making the two files structurally the same thing. I was right. It didn't matter. Or at least, it made no discernable difference.

I mean, come ON - why can't I get OO2 to display in Black/Fluxbox? This is just weird...

---

