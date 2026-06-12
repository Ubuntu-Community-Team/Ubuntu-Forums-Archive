---
title: "Any way possible to get Gnomenu 2.9.1 to work with 13.04 or 13.10?"
date: 2013-11-17
forum: General Help
---

### Post by electricrider on 2013-11-17
I'd like to get Gnomenu ([https://launchpad.net/gnomenu](https://launchpad.net/gnomenu)) working in 13.04 or 13.10. I know they do not have any recent packages or source for either version.

I do know another distro did get it working in 13.04 because I can look at the menu's credits and see it's a renamed Gnomenu.

Gnomenu will install in these versions but it will not show up as an option to add to your gnome panel as stated in the readme doc. I have checked with Synaptic to be sure I had all the dependencies including the Recomends and I do have them all installed.  Here is an excerpt from the Readme file.

> 2.1 Dependencies:-----------------


* Depends:


python
python-xdg
python-cairo
python-gtk2 - that includes pygtk and python-pango
python-gnomeapplet *** necessary only when running on gnome-panel *** - or in some distros "python gnome desktop"
python-xml - may be needed in older distributions (eg: ubuntu before karmic)


* Recomends:


gmenu - will use this instead of xdg if it is installed
python-numpy - for gtk theme colors and some tab effects
python-gconf - or in some distros "python gnome"
python-keybinder or python-xlib - for keybinding
gettext - for translations
zeitgeist


WARNING - In some distribution the packages names may not be the same.(this is the Ubuntu example)


------------
2.2 Install:
------------


extract the contents of the tar.gz
cd "path of where you extracted the tar.gz"


sudo make install


(depending on the distribution the "sudo" command my change)


Then go to your gnome-panel , right click, add to panel, and select GnoMenu


I know I have to Super+Alt right click to see the Add Panel option but Gnomenu is still not showing in the list.

There is a .deb package for 2.9.1 floating around the net (don't remember where I found it) but that doesn't work either.

If no one knows how to get this working (though I'm sure it can be made to work because other distros are doing it) 

Do you know of another tool like Gnomenu that has as much flexibility?

Thanks.

---

### Post by electricrider on 2013-11-18
No one seems to know.. 

what about this, what are my alternnatives?

 [B]Do you know of another tool like Gnomenu that has as much flexibility?


[/B]Also, answer me this.. I know it works in 12.04. What is the posibility that I get it working in 12.04 then upgrade to the latest kernel version and have it not break the Gnomenu appp? ( I'd then upgrade all repos and install all new updates and software to get the apps from the later versions) Is this possible? I could still get the app working and the upgrades I want.. Possible? - or will only the act of upgrading the kerner break the app in itself?

---

### Post by stinkeye on 2013-11-18
What are the features that makes you want to use Gnomenu?

---

### Post by electricrider on 2013-11-19
I want to be able to use AWN (avant windows navigator) in conjunction with an good app that lets me make a custom start button/orb and start menu. Everything must be highly configurable and I must be able to use my own custom graphics where needed.

---

