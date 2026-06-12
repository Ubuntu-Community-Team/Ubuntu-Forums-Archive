---
title: "Worked in Feisty, but not in Gutsy"
date: 2007-12-02
forum: General Help
---

### Post by merlinus on 2007-12-02
After finally having most everything working perfectly in Feisty, I installed Gutsy and now these are issues:

The linux driver for my Matrox P650 card offers nothing but garbled graphics and text, with words and menus overlapping, unreadable, and incapable of being selected.  The mouse pointer looks like a hypodermic needle.

Restoring the xorg.conf backup is useless, as it leaves me stuck in 800x600 resolution.  Same with going through the various terminal commands (e.g. sudo dpkg-reconfigure xserver-xorg) and guis.  The only way to fix things is a complete reinstall.  I have now done this four times.

The vesa driver works okay, but my monitor will no longer power off after 30 minutes.

Ctrl-Alt-F1, F2, etc. screens show up as weird colored lines and patterns, sometimes scrolling.  No CLI.  Various workarounds are useless.  Ctrl-Alt-F7 gets me back to gdm.

I can no longer access a network printer attached to another Ubuntu box.

My Plextor CD-Writer is not recognized.  

Help appreciated!

---

### Post by matthewcraig on 2007-12-02
Have you checked with the vendors' websites on Linux support?  Maybe they have a work around to these problems?  Also, you might try searching the support forums here for others with the same hardware as you, and also try the Launchpad answers section.

---

### Post by merlinus on 2007-12-02
Thanks for your suggestions.  I have, however, been there, done that, and none of these issues existed with Feisty after doing so.

For example, compiling and installing the P650 driver, and then editing xorg.conf to reflect this, worked perfectly.  No garbled icons, graphics, and text.  And my monitor automatically shut off after 30 minutes with the software.

The second Feisty kernel upgrade fixed the problem in detecting my cd burner.

Ctrl-Alt-Fx opened many CLIs, and I could run other guis at the same time as gdm via bodhi.zazen's virtualX script.

Printing worked with no hassles.

And I never had problems restoring backup copies of xorg.conf and getting back to 1280x1024 resolution.

In retrospect, I am left wondering if I would have been better off with an upgrade to Gutsy as opposed to a clean install.

---

