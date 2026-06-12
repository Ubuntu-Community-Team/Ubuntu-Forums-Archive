---
title: "Need help installing Gnome Iconset Builder"
date: 2005-04-17
forum: General Help
---

### Post by MetalMusicAddict on 2005-04-17
Im running Hoary and believe I have the dependencies installed.

I have the .tar from [HERE](http://forge.novell.com/modules/xfmod/project/?gib) and its sitting on my desktop but I cant find install instructions.

Any help?

Or... If anyone knows a complete iconset in .png format I can manually edit that would work also.

---

### Post by tread on 2005-04-17
I can't connect to it, so I cannot confirm this but: gnome-look.org is where you should find loads of icon sets, and maybe even some documents on how to create them.

Hope that helps.

---

### Post by bvc on 2005-04-17
> Installation:
- just unpack the archive and execute the mono binary with 'mono gib.exe [path_to_icon_theme]'
ex. 'mono gib.exe /home/herrera/.icons/suede/'
if no argument given, than the default is /usr/share/icons/gnome/
- dependancies (mono, gtk-sharp, imagemagick) 

[http://gnomesupport.org/forums/viewtopic.php?t=7397&highlight=gib](http://gnomesupport.org/forums/viewtopic.php?t=7397&highlight=gib)

---

### Post by MetalMusicAddict on 2005-04-17
Looks like all I have is .cs files in a "scr" and a "resources" folder. Along with "Install" "Makefile" and a "README. No .exe's to run with arguments.

---

