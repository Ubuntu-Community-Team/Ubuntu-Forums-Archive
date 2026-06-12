---
title: "Does Compiz work with Ubuntu 13.10 GNOME?"
date: 2014-02-02
forum: General Help
---

### Post by Deucalion29710 on 2014-02-02
I am trying to configure Compiz on Ubuntu 13.10 GNOME (3.8) official release.  Let me start by saying I have never used Compiz before.  I installed CCSM and what I thought to be a GNOME patch and I cannot get it to work at all.  Would somebody please provide a step-by-step for me for configuring Compiz or tell me what I could be missing?  In my infinite searches on the topic I found somewhere where I should enable the 4 desktops under "Appearance" in my system settings, however Appearance settings do not seem to be there at all.  Any ideas?

---

### Post by egeezer on 2014-02-02
In Synaptic, you'll need to enable the following:
                        *compiz*
 *compiz-core*
 *compiz-gnome*
 *compiz-plugins*
 *compiz-plugins-default*
 *compiz-plugins-extra*
 *compiz-plugins-main*
 *compiz-plugins-main-default*
 *compizconfig-backend-gconf*
 *compizconfig-settings-manager*
 *libcompizconfig0*
 *libdecoration0*
 [I]python-compizconfig

You'll find some of them already enabled, since you have CCSM already.  The 4 desktops are under the General section of CCSM (the top one); click on the General Options, the Desktop Size tab; you'll want 4 horizontal, 1 vertical, number of desktops 4.

Sad to say, that's just the beginning. 
 [http://wiki.compiz.org/CCSM](http://wiki.compiz.org/CCSM)
has a lot more.  And this will only be effective for 3-D effects if you have proprietary drivers installed.

Yes, it's a long process, but the results (in my view) are well worth it.  I never set up an installation without Compiz, Sphere, Cylinder, and all!

Edited to add: 
I'll keep helping, if you have specific questions.
[/I]

---

### Post by grahammechanical on 2014-02-02
Can you please confirm that you are using either Ubuntu + Unity 13.10 or Ubuntu Gnome 13.10? It is important because Ubuntu Gnome does not use Compiz as the Compositor/window manager. And that is why you cannot configure Compiz. And why you do not have the ability to enable desktops in the Appearance utility.

The Ubuntu developers modify the Gnome utilities whereas the Ubuntu Gnome developers aim for a pure Gnome experience. Gnome shell 3 (in Ubuntu Gnome) uses Mutter as the compositor/window manage and clutter to provide visual effects. In fact Gnome 3 shell is a Mutter plugin.

You might find Gnome Extensions useful. Check out Workspace Indicator on page 2.

[https://extensions.gnome.org/](https://extensions.gnome.org/)

Regards.

---

### Post by Deucalion29710 on 2014-02-02
It is Ubuntu GNOME 13.10.  Is this why when I set the horizontal/vertical number of desktops I cannot save the setting?  Every time it simply reverts.  Also in GNOME I remember there being a hot corner on the right which enabled workspace switching.  Since I had to wipe and start fresh with a new installation I no longer see that or anywhere to make it an option.  As stated previously "appearance" is a MIA option now.

---

### Post by howefield on 2014-02-02
I think that gnome uses dynamic workspaces ie, when you open an application on a desktop the system will create an empty workspace, you might be able to use gnome-tweak-tool to override the dynamic workspace setting and set the number to whatever you want.

---

### Post by Deucalion29710 on 2014-02-02
I now have it set for 4 workspaces and I am able to switch using the switcher in Cairo Dock, but it's still not accepting the settings in compiz.  Is there a "save" button that has just escaped me?

---

### Post by stinkeye on 2014-02-02
> **Deucalion29710 said:**
> I now have it set for 4 workspaces and I am able to switch using the switcher in Cairo Dock, but it's still not accepting the settings in compiz.  Is there a "save" button that has just escaped me?
As **grahammechanical** said , compiz is not the window manager for the session you are in.
You cold replace your current window manager with...
```
compiz --replace 
```
I don't run Ubuntu Gnome but I suspect by doing this you will lose panels and  functionality that relies on the **mutter** window manager.
Isn't the whole point of installing **Ubuntu Gnome** for the gnome-shell interface and functionality with an ubuntu base?
Why specifically do you want to use compiz?

---

### Post by Deucalion29710 on 2014-02-02
I just wanted to check it out really, but it's alight.  I guess I'll just consider it another failed Linux effort.  I still don't know what Appearance settings have <poof> disappeared although it should be there when I go into my system settings.  An enigma I assume.

---

### Post by stinkeye on 2014-02-03
> **Deucalion29710 said:**
> I just wanted to check it out really, but it's alight.  I guess I'll just consider it another failed Linux effort.  I still don't know what Appearance settings have <poof> disappeared although it should be there when I go into my system settings.  An enigma I assume.

You can very easily check out compiz in the standard Ubuntu where compiz is part of the default install.
Don't like the unity interface... disable the unity plugin and add your own panel or cairo-dock.
....or install the gnome-panel for a fallback session that uses compiz and the old style gnome-panel.

---

