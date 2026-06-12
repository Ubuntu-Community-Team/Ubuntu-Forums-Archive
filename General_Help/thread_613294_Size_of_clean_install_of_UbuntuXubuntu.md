---
title: "Size of clean install of Ubuntu/Xubuntu"
date: 2007-11-14
forum: General Help
---

### Post by paintandswim09 on 2007-11-14
Haven't been able to find this on the web, or in the search.

How much disk space does a clean install of Ubutnu take up? Xubuntu?

I am considering purchasing an Asus Eee PC, which right now is only available with a 4gb solid state hard drive. I am curious as to how much space Ubuntu would take up, compared to Xubuntu. With a 4gb hard, I won't have much wiggle room, but I think I would have a little more with Xubuntu. All that is really not much of a problem when I already always carry around a 4gb flash drive that has everything I need, but I have found out that disk space is an easy thing to fill up.

---

### Post by overdrank on 2007-11-14
> **paintandswim09 said:**
> Haven't been able to find this on the web, or in the search.

How much disk space does a clean install of Ubutnu take up? Xubuntu?

I am considering purchasing an Asus Eee PC, which right now is only available with a 4gb solid state hard drive. I am curious as to how much space Ubuntu would take up, compared to Xubuntu. With a 4gb hard, I won't have much wiggle room, but I think I would have a little more with Xubuntu. All that is really not much of a problem when I already always carry around a 4gb flash drive that has everything I need, but I have found out that disk space is an easy thing to fill up.

Hi I believe it is 1.5gigs for xubuntu and 4gigs for ubuntu.

---

### Post by dave61430 on 2007-11-14
I'm using 4gb with 6.06.1. Not enough, runs but not enough tmp storage for a full cd to cd copy. I'm going to put in a new hd. Need room to download apps etc.
Dave Cohen

---

### Post by orbish on 2007-11-15
there are also tutorials on building an X environment off of the ubuntu-server edition, which will give you command prompt... you would probably do a sudo apt-get install (20-30 packages) to get a working GUI environment... i remember installing gentoo with fluxbox and using something like 70mb of hard drive space

that was with base system, xorg, fluxbox (window manager, driven by menus) and and old conky clone

i just heard fluxbuntu is 1.3gb base install... it's also very lightweight... moreso than xfce

---

### Post by rsambuca on 2007-11-15
I would strongly suggest a minimal installation.  You install the base system to a working command line, and then add only the specific components that you need, like a Window manager, etc.  It is very easy to do, and there are [detailed instructions here]("https://help.ubuntu.com/community/Installation/LowMemorySystems").

---

### Post by jespdj on 2007-11-15
> **overdrank said:**
> Hi I believe it is 1.5gigs for xubuntu and 4gigs for ubuntu.

I recently installed Ubuntu 7.10 on my desktop computer and right after the installation it took up about 2.8 GB on the harddisk (so less than the 4 GB you mention here).

Have a look at the [Ubuntu system requirements](https://help.ubuntu.com/community/Installation/SystemRequirements).

---

### Post by jludeman on 2007-12-01
My command line system uses 362.6 MB. This will vary with hardware but should be under 400MB.

Command line install with nothing but xorg, midnight commander, emelfm, feh, openbox openbox-themes and obconf.

total hard drive space 496 MB

I don't see an alternative to Firefox. It's huge in terms of memory usage and disk space.
Once you commit to that you've pretty much lost your tiny footprint. Use the email program of your choice. I like Thunderbird.

Firefox and Thunderbird.

Installing Firefox adds a ton of libraries and other stuff. We've also installed a bunch of gnome libraries. There's not much reason not to go with gnome if you like gnome applications.
 
total hard drive space 794 MB

Gnome panel, nautilus and gedit. sudo aptitude install gnome-panel gets nautilus as well.
I use pcman file manager so I got rid of nautilus.
total hard drive space 908.5 MB 

This includes emelfm, midnight commander, pcman, rox-filer and feh.

I've added some tools and applications that I wanted since then and I'm at 1.3 GB.

All this can be pretty tedious but it will teach you a lot about your system.

If anybody is interested I can make a how to on a simple openbox command line install.

---

