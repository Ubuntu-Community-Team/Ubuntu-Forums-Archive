---
title: "Compiz effects gone with 14.04 --- Gnome Fallback ... Negative, Window Switcher"
date: 2014-09-03
forum: General Help
---

### Post by raequin on 2014-09-03
I like the classic Gnome interface better than Unity, but what I like most of all is my Compiz effects that I was using in 12.04.  The ones I most cherished were Negative and Grid.  It seems that Negative is not available in CompizConfig Settings Manager in 14.04 and this is disturbing me.  Being able to invert colors in a window using keyboard shortcuts was very important to me.

Also, in 14.04 I'm not able to switch windows using Alt+Tab.  In fact, I don't see Window Switcher in CCSM (I think that's where the settings were).  What happened to all the effects in CompizConfig Settings Manager?  I'm using Fallback (Compiz).  Thanks.

---

### Post by deadflowr on 2014-09-03
Well, to that all I can say is I have Negative, Don't know what window switcher is, though.
(viewport switcher?)

I'm not sure, but is/are they part of the extras package, now known as compiz-plugins?
(Formerly known as compiz-plugins-extras)

---

### Post by grahammechanical on 2014-09-03
If you go to System Settings>Appearance>Behaviour tab and tick the box labelled "Enable workspaces" you will then be able to use Ctrl+Alt+arrow key to switch workspaces.

Another thing, in Ubuntu 14.04 we do not install fallback but gnome-session-flashback. Then we get two additional login screen options, Gnome Flashback (Compiz) and Gnome Flashback (Metacity). There is an important difference between fallback in 12.04 and gnome-session-flashback in 14.04. 

Some months ago the developer of many of the Compiz plugins stopped maintaining the plugins and they were removed from Compiz Configuration Settings Manager. A couple of other developers took up the task and the some of the plugins were put in a separate package. Other plugins are not being maintained.

Install compiz-plugins and many more effects will be available. compiz-plugins-extras is now a meta package. 

Take my advice do not upgrade to 16.04 when it comes out because 16.04 is when Ubuntu transitions on to Mir. When the Xserver is taken of Ubuntu so will Compiz and LightDM be removed as well. There is now an opportunity for some developers to produce a Mir settings manager with fancy effect plugins. We shall see. But such is the nature of Free and Open Source Software that we depend upon the willingness of developers to write the software we want.

Regards.

---

### Post by raequin on 2014-09-03
That did it.  Thank you both very much.  I knew I was butchering the terms --- the Alt+Tab functionality is Application Switcher or Static Application Switcher, one.  And grahammechanical thanks for the info about 16.04.  I still need to learn how to swap CapsLock and Ctrl then I'll be in business again.

---

