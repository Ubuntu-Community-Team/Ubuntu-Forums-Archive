---
title: "compiling nethack for gnome (question about config.h)"
date: 2006-10-27
forum: General Help
---

### Post by TeeAhr1 on 2006-10-27
I don't know if anyone else has noticed that the new nethack-gnome package is broken (crashes after character select).  Anyway, I must have my fix, so I'm attempting to compile the source.  Here's my question.

I'm editing the config.h file, and here's the part where I'm confused:
```
/*
 * Define the default window system.  This should be one that is compiled
 * into your system (see defines above).  Known window systems are:
 *
 *	tty, X11, mac, amii, BeOS, Qt, Gem, Gnome
 */

/* MAC also means MAC windows */
#ifdef MAC
# ifndef	AUX
#  define DEFAULT_WINDOW_SYS "mac"
# endif
#endif

/* Amiga supports AMII_GRAPHICS and/or TTY_GRAPHICS */
#ifdef AMIGA
# define AMII_GRAPHICS			/* (optional) */
# define DEFAULT_WINDOW_SYS "amii"	/* "amii", "amitile" or "tty" */
#endif
```

Followed by several more definitions, one of which is gnome.  How do I choose that as the default?  Do I delete all the other defs from the config file?  Plz advise, anyone who's done this...

best,
p.

---

### Post by ~LoKe on 2006-10-27
```
sudo apt-get install nethack-gnome
```
Downloaded, installed and ran.  Chose my character, class, etc, and started.  Works just fine.

---

### Post by TeeAhr1 on 2006-10-27
Not for me.  I choose my gender, it comes up with the map for a split-second and crashes out.

---

### Post by RoddyVR on 2006-11-06
> **TeeAhr1 said:**
> Not for me.  I choose my gender, it comes up with the map for a split-second and crashes out.

same exact thing for me.

up till yesterday i was playing the X11 version, it worked ok, except i couldnt see the bottom of the window, and any window it opened (help files and so on) closed if i tried to scroll or click on them.

so today i noticed the gnome version in the packages, installed that, ran it, picked my char, race, gender, and crashed.

after much swearing and trying again (including 3 reinstalls, though i suspect it never redownloaded anything), i came here.

running it the normal way, it just closes after the char selections.
running it as
```
sudo nethack-gnome
```
i get this:
```
roddy@Roddy-Ub:~$ sudo /usr/games/nethack-gnome
Password:
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 28235 error_code 8 request_code 62 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 28241 error_code 8 request_code 62 minor_code 0
roddy@Roddy-Ub:~$ 

```
the errors come up after i pick the char, race, gender.  i have no clue how to fix this, but would realy like someone to tell me how to get it to work.  is there like some older version i could get from somewhere maybe.

after some more experimenting, i realized i get the same errors when i run it as with SH same as with Sudo

---

