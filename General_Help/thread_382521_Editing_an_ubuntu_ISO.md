---
title: "Editing an ubuntu ISO"
date: 2007-03-12
forum: General Help
---

### Post by Tadhg on 2007-03-12
I am trying to figure out how I could go about editing an ISO of ubuntu, so as when I install from the CD, certain custom things get installed with it. 

Nothing complicated, just for example, have a certain image as the background by default, and have a preloaded folder and its contents extracted to the desktop. Is it possible/difficult to get this done? 

I've mounted and looked through the ISO, and it doesn't seem to fall under and recognizable structure.

---

### Post by Tadhg on 2007-03-12
ok, i have mounted the initrd.img of the ISO, and had a look through that. As it's only the initial state of install, it's sparse on content.

For example, if i wanted to have a custom wallpaper loaded up on install (found usually in /usr/share/wallpaper/) is it enough to create /usr/share/wallpaper/nameofwallpaper.jpeg (as the folder wallpaper doesnt exist).

---

### Post by 23meg on 2007-03-12
Check out [Reconstructor]("http://reconstructor.aperantis.com/").

---

### Post by Tadhg on 2007-03-12
I checked out reconstructor and while it sorts out the wallpaper issue, i don't think you can load random files (i.e. non apt packages) onto the CD. It seems to be geared more toward live CD's than install images.Or am i overlooking it?

EDIT//

So it looks like the way to do it is:
make a ./configure file to extract the tarball of the folder i want to extract to the desktop
make this into a .deb
add this .deb as a package to the install cd under pool and configure it?

This looks a lot like what reconstructor does for you. Sure it's only fun if you do it your self i suppose though!

---

