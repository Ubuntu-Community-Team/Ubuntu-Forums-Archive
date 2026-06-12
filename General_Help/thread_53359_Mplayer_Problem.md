---
title: "Mplayer Problem"
date: 2005-07-31
forum: General Help
---

### Post by Juneau on 2005-07-31
Hey everyone I have this problem with Mplayer, the fonts in the right click menu and the Preferences window are squashed together (see screenshot), just wondering if anyone here had any insight in to what might be causing it.

I've installed Mplayer from the repos and used the Ubuntu starter guide. I've tried reinstalling the package but it does'nt work. 

It was fine to begin with but then started doing this for some reason.

Thanks in Advance!

[[IMG]http://img71.imageshack.us/img71/3329/mplayer7mm.jpg[/IMG]](http://imageshack.us)

---

### Post by kassetra on 2005-08-03
[QUOTE=Juneau]Hey everyone I have this problem with Mplayer, the fonts in the right click menu and the Preferences window are squashed together (see screenshot), just wondering if anyone here had any insight in to what might be causing it.

I've installed Mplayer from the repos and used the Ubuntu starter guide. I've tried reinstalling the package but it does'nt work. 

It was fine to begin with but then started doing this for some reason.

Thanks in Advance!

[/QUOTE]
Couple of quick questions here for you: 
What gtk2 theme are you using?  Is there a gtk1 theme in the same directory as the gtk2 theme?  The reason I'm asking this is because the mplayer gui uses gtk1 to do the interface rendering for things like the right click menu.  So if you do not have a gtk1 theme setup with a font, colors, etc. it can look kinda yucky.  You might want to install a gtk1 theme in your /usr/share/themes/YOUR_THEME folder to make sure that the gtk1 components of mplayer look nicer.  :)

---

