---
title: "LibreOffice no longer using distro's dialogues"
date: 2021-09-25
forum: General Help
---

### Post by Tom_ZeCat on 2021-09-25
Distro: Kubuntu 20.04 LTS
application: LibreOffice 7.2.1.2

I had to fix up LibreOffice.  It had gotten buggy.  I couldn't figure out why, but it wouldn't let me choose the font I wanted from the drop-down toolbar (standard toolbar interface).  It gave me the same problems with the page number plug-in.  When I chose Insert ==> Page Numbering, the plugin menu would come up fine, but whatever drop-down menu choices I made would not keep.  

I did figure out if I dropped down the font menu and then actually typed the name of the font, it would let me choose it.  But it was a major annoyance not to be able to just pick a font from the menu.  

For the first time ever, I tried a Flatpak-based install of LibreOffice.  Turns out, everything ran fine for the most part, but the interface was weird.  I have a French characters toolbar that I use for writing in French with my American keyboard that lacks so many of the French characters.  It normally looks like this: 

[img]https://i.postimg.cc/g2hwg0fz/French-Toolbar.png[/img]

In the Flatpak install, it looks like this: 

[img]https://i.postimg.cc/QMrFw33p/French-Toolbar-flatpak.png[/img]

It looks awful in the Flatpak install.  It's also harder to move around with the mouse.  It does some funky thinks where it suddenly zips to the other side of the screen.  

I didn't want to stick with a Flatpak install for LibreOffice anyway, so I decided to purge uninstall and re-install my regular LibreOffice.  Here's how I did it:  

Uninstall it: 
```
sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove
```

Then to reinstall it: 
```
sudo apt install libreoffice-plasma libreoffice
```

I chose the plasma install because I'm using Kubuntu, which is the KDE version of Ubuntu.  There was a Gnome choice available as well.  

Anyway, this fixed it!  No more funky weird stuff with the fonts drop-down menu or with the Page Number Plugin.  Unlike the Flatpak install, my French language toolbar looks perfect in this install.  

Thus everything is now exactly how I want it to be with one minor exception: The open file dialogue box now looks funky and is not as useful.  It looks like it may be one that's built-in for LibreOffice rather than the one from the Kubuntu distro.  It now looks like this: 

[img]https://i.postimg.cc/J4n42hBw/LODialogs.png[/img]

Before the re-installation, it looked like it was using a KDE/Kubuntu dialogue box that had my folder libraries in it.  The Flatpak install uses the distro one and so it looks like this: 

[img]https://i.postimg.cc/0yK59Hfc/LODialogue-flatpak.png[/img]

However, I don't intend to keep the Flatpak install of LibreOffice.  The regular one just runs better.  It boots up more quickly, and the interface is overall much more desirable.  

However, how do I tell the LibreOffice regular install to use KDE/Kubuntu dialogues rather than the in-house LibreOffice ones?  I've been searching through Tools ==> Options for a couple hours now, and I'm not finding it.  

I would really appreciate some help.  I've solved all my problems with LibreOffice, except for this one thing.  I also would not recommended using a Flatpak-based install of LibreOffice, since it seems to make its interface funky, and it boots up more slowly.  (This is not a Flatpak bash, as I've had really good luck with it for other installs.)  

If someone knows how to make this new, non-Flatpak install of LibreOffice use the Kubuntu distro's dialogues, I would be grateful for your info.

=====================================

An update: I've solved the problem.  In the Muon Package Manager, I installed the following: 
libreoffice-kde, libreoffice-kde4, libreoffice-kde5
After doing that, the KDE dialogues then became available.  In fact, in LO Writer, if you go to Tools ==> Options General after installing those, you then have the choice between using the KDE or the LibreOffice Dialogues.  

So I'm good.  Problem solved.  However, I'll leave this post here in the event that it might help others.

=========================

Second update: 
Installing the KDE integration made LibreOffice Writer revert to the previous same problems.  The font selection menu became buggy again.  I uninstalled the KDE integration and the problem went away.  I therefore have purged the following via the Muon Package Manager: 
libreoffice-kde
libreoffice-kde4
libreoffice-kde5
libreoffice-kf5

I got rid of those and the font selection problem went away.  However, it also means I no longer have access to the KDE dialogues.  I've decided to live with the LibreOffice dialogues.  It turns out they're customizable.  

Should I report this to KDE or to Kubuntu as a bug?

---

### Post by vanadium on 2021-09-26
Tools - Options, "General" under "LibreOffice" has the setting "Use LibreOffice dialogs". If checked, LS uses its internal dialog. If unchecked, it uses the system provided one. If it is unchecked for you and still shows its own dialog, then no integration with the Plasma dialog may be available. The flatpak (and libreoffice-gnome) use the GTK3 dialogs.

---

