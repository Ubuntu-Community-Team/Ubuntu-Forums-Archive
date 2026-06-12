---
title: "Firefox borked!"
date: 2008-07-08
forum: General Help
---

### Post by MST3Kakalina on 2008-07-08
Between some upgrades and downgrades between 2.0.0.x and 3.0, I seem to have lost the functionality of all of my add-ons (AdBlock, StumbleUpon, Greasemonkey), plugins (Java), and themes.  I think it has something to do with the plugins getting bumped up to 3.0 at the upgrade, but then not being compatible anymore when I switched back to 2.0.0.15, but I have nothing to back that up.  It would help if I could run FF 3.0.

As it stands, I'm using FF 2.0.0.15.  I have 3.0 installed, but trying to run it from the terminal as "firefox" tells me it's NOT installed, and trying to run it as "firefox-3.0" just freezes, feeding me this: 

```

Registering '@mozilla.org/module-loader/python;1' (libpyloader.so)
Registering '@mozilla.org/network/protocol/about;1?what=python' (pyabout.py)
Registering '@mozilla.org/module-loader/python;1' (libpyloader.so)
Registering '@mozilla.org/network/protocol/about;1?what=python' (pyabout.py)
Registering '@mozilla.org/module-loader/python;1' (libpyloader.so)
Registering '@mozilla.org/network/protocol/about;1?what=python' (pyabout.py)
```

Trying to install add-ons gives me this in the Error Console:

```

oldInstallLocation has no properties
file:///usr/lib/firefox/components/nsExtensionManager.js
```

GIGANTIC EDIT: It seems the trick from launchpad about renaming extensions.rdf in the .mozilla folder in the home directory did the trick, as far as the plugins in 2.0.0.15 go.

I've tried removing (and purging) everything and reinstalling, both from mozilla.com and from the repos.  I've changed the ownership of my Mozilla profile to me (as I've seen recommended).  Nothing's worked.  So basically, if you can help me find a way to get me running 3.0, I'll bake you cookies.  Delicious internet cookies.

---

### Post by anim on 2008-07-08
can you run
```
dpkg -s firefox
``` and ```
dpkg -s firefox-3.0
``` 

and tell me what it says

---

### Post by MST3Kakalina on 2008-07-08
Sure!

```
katherine@katherine-laptop:~$ sudo dpkg -s firefox
Package: firefox
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 120
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: all
Source: firefox-3.0
Version: 3.0+nobinonly-0ubuntu0.8.04.1
Depends: firefox-3.0
```

and 

```
katherine@katherine-laptop:~$ sudo dpkg -s firefox-3.0
Package: firefox-3.0
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 3552
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Version: 3.0+nobinonly-0ubuntu3~fta6~hardy
Replaces: firefox (<< 3), firefox-granparadiso, firefox-libthai, firefox-trunk
Provides: firefox-libthai, www-browser
Depends: debianutils (>= 1.16), fontconfig, libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.6.0), libgcc1 (>= 1:4.1.1-21), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.12.0), libnspr4-0d (>= 1.8.0.10), libpango1.0-0 (>= 1.20.1), libstdc++6 (>= 4.1.1-21), psmisc, xulrunner-1.9 (>= 1.9+nobinonly-0ubuntu3~)
Recommends: ubufox
Suggests: firefox-3.0-gnome-support (= 3.0+nobinonly-0ubuntu3~fta6~hardy), latex-xft-fonts, libthai0
Conflicts: firefox (<< 3), firefox-granparadiso (<< 3.0~alpha8-0), firefox-libthai, firefox-trunk (<< 3.0~a8~cvs20070914t1713-0)
Conffiles:
 /etc/firefox-3.0/pref/firefox.js 6f52c7983d5ecdc9d3b953863bbebca2
 /etc/firefox-3.0/profile/bookmarks.html 5268a062e398d7c991f16155159088a3
 /etc/firefox-3.0/profile/prefs.js 99940ecd258d83b3355ab06fca0ffddb
 /etc/firefox-3.0/profile/localstore.rdf ea03cc19c2a3f622fa557cd8ea9da6eb
 /etc/firefox-3.0/profile/mimeTypes.rdf 69cdcb7e0209f2e9d29000ee1c0ee2f0
 /etc/firefox-3.0/profile/chrome/userChrome-example.css 4788fdaa51b0a238cb21f5c2877ef06d
 /etc/firefox-3.0/profile/chrome/userContent-example.css d3765c7d2de5626529195007f4b7144a
```

---

### Post by anim on 2008-07-08
Well, it looks like the firefox meta-package is correctly pointing to 3.0 and firefox-3.0 is installed so I *think* this is a plugin problem.

Try running ```
firefox -ProfileManager
``` and start firefox with the new profile. (You may need to replace firefox with firefox-3.0).

If it doesn't start with a new profile let me know.

---

### Post by Bubba64 on 2008-07-09
If you get Firefox working and the add ons are there but not working you can install nightly tester tools from the Mozilla add on site, and this will force the add ons to work. Another trick to get Mozilla add ons installed that are blocked is to look for them via Google after the nightly tester tools is installed, and install them from a Mozilla site where it will ask you if you if you want the add ons forced to work.

---

### Post by MST3Kakalina on 2008-07-09
> **anim said:**
> Well, it looks like the firefox meta-package is correctly pointing to 3.0 and firefox-3.0 is installed so I *think* this is a plugin problem.

Try running ```
firefox -ProfileManager
``` and start firefox with the new profile. (You may need to replace firefox with firefox-3.0).

If it doesn't start with a new profile let me know.

Trying to run ```
firefox-3.0 -ProfileManager
``` hangs just as much as ever, with the same output in the terminal window.

But patience is a virtue, and since ps -A told me that firefox was still running, I waited it out.  A Firefox window is now open, but lagging like hell, even with a new profile (that I created with firefox-2 -ProfileManager).  This is what terminal spat out right when the window opened:

```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0xb7b15970: NP_GetMIMEDescription
GCJ PLUGIN: thread 0xb7b15970: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0xb7b15970: NP_GetValue
GCJ PLUGIN: thread 0xb7b15970: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0xb7b15970: NP_GetValue return
GCJ PLUGIN: thread 0xb7b15970: NP_GetValue
GCJ PLUGIN: thread 0xb7b15970: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0xb7b15970: NP_GetValue return
```

The Add-Ons window finally appeared.  I disabled xulrunner and hit restart, but it still really drags starting up.  When I say drags, I mean draaaaaaags.  It takes a few minutes for a window to even show up, and trying to do anything in it suffers from the same non-responsiveness.

I think it is a problem with the GCJ plugin (durr).  Has this been a confirmed issue with other users?

---

### Post by cao1 on 2008-08-25
have got exactly the same problems after downgrading from firefox3 to 2. additionally, it turns out songbird has the same issues of running extremely slow (also based on xulrunner).

have deleted all profile data, but no change.

anyone have any more ideas?

---

