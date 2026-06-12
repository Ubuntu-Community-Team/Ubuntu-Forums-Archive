---
title: "Making Gnome look like Sabayon"
date: 2007-02-08
forum: General Help
---

### Post by krimson on 2007-02-08
For anyone that is familiar with the menu styles in sabayon...
it has the favorite apps menu, the big iconified menu, its almost like windows XP in a way...

i am curious how they reach that point?
is there a special program that allows them to do that, some special configuration, a different version of gnome or what?

thanks!

---

### Post by ser1alsn1per on 2007-02-08
yeah the gnome menu lacks a little i think and could certainly do with some work

---

### Post by yopnono on 2007-02-08
> **krimson said:**
> For anyone that is familiar with the menu styles in sabayon...
it has the favorite apps menu, the big iconified menu, its almost like windows XP in a way...

i am curious how they reach that point?
is there a special program that allows them to do that, some special configuration, a different version of gnome or what?

thanks!

Don't they use KDE?

---

### Post by krimson on 2007-02-08
no, its not kde, you get a choice between flux, kde, gnome, e16, and i think xfce... maybe others.

here are a couple screens
[http://shots.osdir.com/slideshows/slideshow.php?release=758&slide=73](http://shots.osdir.com/slideshows/slideshow.php?release=758&slide=73)

---

### Post by tbrminsanity on 2007-02-08
[http://www.gnome-look.org/](http://www.gnome-look.org/)

This is where I find all the icons, wallpapers, and mouse pointers for my computer.  You can even make your desktop look XP or Vista looking.

---

### Post by fflar on 2007-02-08
It's an applet:
sudo apt-get install gnome-main-menu

---

### Post by krimson on 2007-02-09
> **fflar said:**
> It's an applet:
sudo apt-get install gnome-main-menu

awesome! thanks!

---

### Post by krimson on 2007-02-10
yeah, it doesnt work.. maybe i need more repos or something

---

### Post by ardchoille42 on 2007-02-10
> **krimson said:**
> yeah, it doesnt work.. maybe i need more repos or something

No, I don't think repos are the problem. I have all the repos enabled and I can't find gnome-main-menu anywhere in the repos. I think the problem is that gnome-main-menu is the menu that has 'Applications Places System', the default menu applet in the gnome panel, and people are thinking that gnome-main-menu is a cool looking type of "slab" menu. I have added the gnome-main-menu applet to my panel and it's just the default 'Applications Places System' menu that ships with Ubuntu. I don't know what that menu is in [http://shots.osdir.com/slideshows/slideshow.php?release=758&slide=73](http://shots.osdir.com/slideshows/slideshow.php?release=758&slide=73) but it isn't gnome-main-menu.

---

### Post by imspecial on 2007-02-10
I just successfully downloaded and installed it. It is in the universe repository.


I just realized that is the similar to what is used in opensuse also, which I find extremely annoying, so i removed it before even figuring out how to enable it.

---

### Post by fflar on 2007-02-12
> **ardchoille42 said:**
> No, I don't think repos are the problem. I have all the repos enabled and I can't find gnome-main-menu anywhere in the repos. I think the problem is that gnome-main-menu is the menu that has 'Applications Places System', the default menu applet in the gnome panel, and people are thinking that gnome-main-menu is a cool looking type of "slab" menu. I have added the gnome-main-menu applet to my panel and it's just the default 'Applications Places System' menu that ships with Ubuntu. I don't know what that menu is in [http://shots.osdir.com/slideshows/slideshow.php?release=758&slide=73](http://shots.osdir.com/slideshows/slideshow.php?release=758&slide=73) but it isn't gnome-main-menu.

It's the same name but a different applet. In the universe repository.
Description:
GNOME start menu applet
This applet provides a "start menu" for the GNOME desktop.

It features a list of favorite applications, and recently used documents.

It also integrates with the Beagle search tool to provide search facilities
from the start menu. It provides shortcuts for common system
administration actions and integrates with network-manager for network
status reporting.

---

### Post by Scheater5 on 2007-02-12
Sabayon is kinda a KDE centric distro - almost any screenshot I've seen if using KDE, and the installs kinda make "gentoo-legacy" and fluxbox seems like options, while KDE is the default.  If you want Ubuntu to look like the screenshots you've seen of Sabayon, start with KDE, then make the taskbars transparent, and then take the clock and running applications out of the main taskbar and add another taskbar at the top with those things (Sabayon 3.26 has, by default the "show desktop" icon, the desktop switcher, running applications and the clock/calander).  And, then, of course, install beryl.  
You could do close with Gnome, but the icons would be a pain in the butt.

---

### Post by cmost on 2007-02-12
I don't know about others, but I think Chander's & Malac's "Ubuntu System Panel" blows Novell's SLAB menu (the one used in Sabayon) out of the water.  Currently, the next generation of USP is in heavy development (it can be downloaded for testing via a deb or via SVN from the 'Ubuntu System Panel' specific forum located elsewhere on this site.  Otherwise, the latest stable version is 0.41-1; also available as a deb for download.  This panel is highly customizable via plugins and looks simply amazing.  Give it a whirl.

---

