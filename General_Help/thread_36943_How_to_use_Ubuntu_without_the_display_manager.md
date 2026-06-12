---
title: "How to use Ubuntu without the display manager?"
date: 2005-05-25
forum: General Help
---

### Post by Sleeper Service on 2005-05-25
Hi - another poser...

I'd quite like the option of using Ubuntu *without* the display manager - i.e. before I log-in and after I log-out of a window manager/desktop environment, I'd like just a plain text terminal / log-in prompt.

One of the reasons for this is that I regularly swap between Gnome and very slimmed down window managers like TWM and Ratpoison.

I've worked out how to prevent the display manager (gdm) from starting automatically, but I'm not sure how to start up the various window managers.

When I was running Mandrake, I used "[FONT=Courier New]startx gnome-session[/FONT]", "[FONT=Courier New]startx twm[/FONT]", and so on.  But that's not working in Ubuntu.  X is starting, but it seems my "gnome-session" or "ratpoison" is not being understood...

Any thoughts?

---

### Post by tread on 2005-05-25
Stop gdm, and create a .xinitrc file in your home directory. In that file, just put whatever windowmanager you want, for example:

#exec twm
#exec gnome-session
#exec wmaker
exec enlightenment

Since enlightenment is the uncommented one, that will load. If you want to switch windowmanagers just comment the existing one and uncomment the required one.

You just need to type startx to start.

---

### Post by Sleeper Service on 2005-05-25
Thanks, tread.

That kind of does the thing.  Except that I'm used to being able to add an option to startx which sets the window manager type.  Easier than editing a file.  But I can't find the right way to do this, if it's even possible in Ubuntu.

I suppose I could write a small script that writes .xinitrc and then executes startx, but that seems a tad clumsy...

--

[edit]  I guess another option would be for me to try and add twm and ratpoison to the list of session options in gdm - does anyone know how to hack this?

---

### Post by tread on 2005-05-25
I think thats in /usr/X11/sessions .. I'm not sure. Try searching for gnome.session, or gnome.xsession .. and then create a ratpoison session file around it.

Edit: Did a quick search, its /usr/share/xsessions

---

### Post by Sleeper Service on 2005-05-25
Lovely - thanks, tread.

I created twm.desktop and ratpoison.desktop in /usr/share/xsessions/ with the following contents, and everything works beautifully:

_twm.desktop:_ [FONT=Courier New]
[Desktop Entry]
Encoding=UTF-8
Name=twm Session
Comment=Use this session to run twm: a no-frills, high-speed window manager
Exec=/usr/bin/X11/twm
Icon=
Type=Application
[/FONT]
_twm.desktop:_[FONT=Courier New]
[Desktop Entry]
Encoding=UTF-8
Name=ratpoison Session
Comment=Use this session to run ratpoison - and KILL THE RODENT!!! Mwoah ha ha!!!
Exec=/usr/bin/ratpoison
Icon=
Type=Application
[/FONT]

---

