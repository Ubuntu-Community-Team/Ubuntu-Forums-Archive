---
title: "how does .cache/thumbnails get populated"
date: 2017-10-04
forum: General Help
---

### Post by JamButty on 2017-10-04
Curious how Home/.cache/thumbnails gets populated. Due to recurring problems, I have to wipe and reload not infrequently. I do not backup any system files afaik, do not backup all of Home, only basic user directories (downloads-documents-music-pictures-video), yet I note the same photos, with small variations, keep showing up in thumbnails. If I wipe these dirs, they regenerate, which is understandable within an OS lifetime, but their reincarnation is spooky.  I hate icons and rarely if ever have any need for previews, so thumbnails are pretty useless anyway.
Whence this plague? Avast! 

running 16.04 Xerus

---

### Post by ajgreeny on 2017-10-04
It is done by **tumbler** which you could remove but it will take with it the meta-package *ubuntu-desktop for whichever DE version you use.
That does not affect daily use of the system in any way and is only of any real consequence when you upgrade from one OS version to the next.

The easier way however, is to edit **/etc/xdg/tumbler/tumbler.rc** (after backing it up, just in case) and set all the instances at the bottom to **Disabled=false** or you can simply do so for whichever file-types you wish.

---

### Post by vasa1 on 2017-10-04
I've given up trying to figure out how thumbnails are generated or whether there's a limit that can be set regarding their numbers or longevity.```
find -type d -iname thumbnails
```will show you where they hide and you can deal with them as you see fit.

Firefox could be set to turn off storing thumbnails in the not-to-distant past. I haven't checked if it still works.

Make a **new** `about:config` entry of type `boolean` called `browser.pagethumbnails.capturing_disabled`. Set it to `true`.

Re. tumbler, isn't that primarily an XFCE thing?

---

### Post by ajgreeny on 2017-10-04
> **vasa1 said:**
> Re, tumbler, isn't that primarily an XFCE thing?
You may be right but I admit to not actually knowing if that is so as I have now been using Xubuntu for so long that I have no knowledge of whether or not it's installed in the other DE versions of *ubuntu.

Worth checking, and if using nautilus, is there some config file or settings dialogue that lets you turn off thumbnails? There certainly used to be some time ago but I'm aware that the configuration of nautilus is not so easy to deal with as it used to be according to many users.

---

### Post by vasa1 on 2017-10-04
```
apt show tumbler
```has this:```
...
Homepage: http://www.xfce.org/
Task: xubuntu-core, xubuntu-desktop, mythbuntu-desktop, ubuntustudio-desktop-core, ubuntustudio-desktop
Supported: 3y
```So it does seem to be the default in XFCE-based systems.

---

### Post by vasa1 on 2017-10-04
Here's what I get using *find*:```
$ find -type d -iname thumbnails
./.cache/mozilla/firefox/hco83scq.default/thumbnails
./.cache/thumbnails
./.config/google-chrome/Default/Thumbnails
./.config/google-chrome/Profile 1/Thumbnails
./.config/google-chrome/Profile 2/Thumbnails
./.config/qupzilla/profiles/default/thumbnails
$ 
```And creating a new *about:config* setting as I described in post #3 seems to work in Firefox 57.

---

### Post by JamButty on 2017-10-04
I don't seem to have a tumbler dir under /etc/xdg

[COLOR=#000000][FONT=&quot]find -type d -iname thumbnails

[/FONT][/COLOR]did not turn up the thumbnails dir that is recurring. Tried straight and with Sudo. I rarely use firefox, so that is not an issue for me. I generally use it once after a reload to get Opera and go from there. It could be setting up the file selection list for regeneration on that one use, so will need to look more closely at that.

There are one or two places in the basic system settings (the launchbar gui) that reference using thumbnails, but I thought I had everything I could find set to off.
I will keep digging.

Thanks!

---

