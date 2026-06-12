---
title: "Problems with xinitrc and Xresources"
date: 2008-01-30
forum: General Help
---

### Post by smehmood on 2008-01-30
Hey all,

I'm a recent convert from openSUSE 10.2 and KDE 3.5 to Ubuntu 7.10 and GNOME. Loving Ubuntu so far, not so sure about GNOME yet, but it's a lot better than I thought it'd be.

I am having a few issues getting some of the settings I used to have on my openSUSE install to work on Ubuntu, however.

I have two goals:

1) To get the command "syndaemon -i 1 -d" executed whenever X is started
2) To have yeahconsole running when X is started/I log into GNOME, with the toggleKey X resource set to "F12"

After some googling and reading of the man pages

I created a .xinitrc file and an .Xresources file in my home directory and put both commands in the .xinitrc file and the appropriate line to set the toggleKey resource in the .Xresources file, though it doesn't seem to work.

Neither syndaemon or yeahconsole are running at startup, and if I run yeahconsole manually, the default toggle key is the only one that works (ControlAlt+y).

I also tried putting the lines directly in the files found in the /etc/X11 folder. Ideally, I'd like syndaemon command to be run for all users, and the yeahconsole command to only be run for my account.

I also tried to use the GNOME Session manager to make the command "yeahconsole" run on log-in, but that doesn't appear to work either.

Is there something I need to do with Xsession?

At the end of the post, I'll append the text of all relevant files.

I really appreciate any help, I've heard the Ubuntu community is the best when it comes to support.

--- Text of relevant files ---

/home/smehmood/.xinitrc:
--- start of file---
#!/bin/sh

syndaemon -i 1 -d &
--end of file---

/home/smehmood/.Xresources:
---start of file---
yeahconsole*toggleKey:ControlAlt+x
---end of file---

Note: I tried ControlAlt+x for the value since the yeahconsole man pages list ControlAlt+y as the default value. This way I was sure that my syntax for the value was correct.

Also the output for yeahconsole -h contains this:
you can configure me via xresources:
yeahconsole*foo:value
foo can be any standard xterm/urxvt xresource or:
...
toggleKey: ControlAlt+y
...

/etc/X11/xinit/xinitrc:
--start of file---
#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
syndaemon -i 1 -d
. /etc/X11/Xsession
--end of file---


/etc/X11/Xresources/x11-common
---start of file---
! $Id$

! load color-specific resources for clients that have them
#ifdef COLOR
*customization: -color
#endif

! make Xaw (Athena widget set) clients understand the delete key
! this causes problems with some non-Xaw apps, use with care
! *Text.translations: #override ~Shift ~Meta <Key>Delete: delete-next-character()
---end of file---

Note: I tried the same "yeahconsole*toggleKey:ControlAlt+x" line here, under the #endif line with no success

---

### Post by peterff on 2008-02-01
Hi,

As far as I know, GDM doesn't read .xinitrc (I assume you're using GDM to log in). I don't use GDM, so I can't help you there, but it looks like there might be an option in the GDM Sessions menu to load the .xinitrc script. Also make sure .xinitrc is executable by you.

I've always had trouble with .Xresources, too. One thought is that it might not be getting read. I doubt this is the case, since you've restarted since modifying it, but I know that if you don't restart you need to use xrdb to read .Xresources before any changes you've made in it will take effect.

---

