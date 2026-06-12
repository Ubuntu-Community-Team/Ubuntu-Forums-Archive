---
title: "Title Bar Scroll Wheel Bug in kwin?"
date: 2006-07-04
forum: General Help
---

### Post by detyabozhye on 2006-07-04
For some reason, no matter what I set "System Setting->Desktop->Window Behavior->Titlebar wheel event" to, it will only raise and lower windows (default behavior). I had it working to shade and unshade windows at one point but it doesn't work anymore. Is this a bug in kwin? How can I make it work correctly?

---

### Post by xtacocorex on 2006-07-04
I just logged into a nested KDE session to try what you had set and it doesn't work for me either. 

I'm not used to the new version of KDE, so I don't know what changed, but that feature does seem to be broken.

---

### Post by kebes on 2006-12-14
I've also noticed this bug and it really annoys me, since I find the "titlebar wheel event" to be a remarkably useful shortcut.

I have found the solution, however!

If you're using the default Kubuntu window decoration theme ([Crystal]("http://www.kde-look.org/content/show.php?content=13969")), then do this:
Control Panel > Appearance > Window Decoration > Window Decoration

Uncheck the box that says "Cycle tasks with mouse wheel".

Now the "titlebar wheel event" setting (selected under Configure Window Behavior > Actions > Titlebar wheel event) will actually work!



If you're using some other theme, switch to a theme that works! Control Panel > Appearance > Window Decoration > Window Decoration. Set the Theme to "Plastik", or "Crystal" (and make the fix as described above) or one of the other supported ones (see below).



Some extra information, for anyone who cares:

This bug has been noted in the KDE database:
[http://bugs.kde.org/show_bug.cgi?id=117769](http://bugs.kde.org/show_bug.cgi?id=117769)

Apparently the bug only exists in some of the Window Decoration themes. So if you change your Window Decoration theme to one of the supported ones, the "titlebar wheel event" will start to work.

If you look at the bug report comment #10:
[http://bugs.kde.org/show_bug.cgi?id=117769#c10](http://bugs.kde.org/show_bug.cgi?id=117769#c10)

It says which themes will work and which will not. The themes that should be working in a standard KDE install are:

KDE 2
Laptop
Modern System
Plastik
Quarz
Redmond
Web 


The bug has been fixed for all official KDE themes, but of course it will take some time before the bugfixes make their way into the Ubuntu repositories. So if you're using a theme that doesn't currently work, you'll either have to wait for the fix to become official, install the fixed version of the theme, or switch themes.



I hope this is of some help to others... this has been driving me crazy for months now!

---

