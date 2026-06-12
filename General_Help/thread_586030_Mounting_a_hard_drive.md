---
title: "Mounting a hard drive"
date: 2007-10-21
forum: General Help
---

### Post by keeler1 on 2007-10-21
I have my /etc/fstab set to mount a partition in a folder on my desktop.

However ubuntu also creates another link to the drive on the desktop like before it knew where to mount itself.

How do I get this to go away.

To be a little more explanator I put a picture of what they are attached with this.  The folder External is where it is mounted and the other is the one I want to get rid of.

---

### Post by DagMan on 2007-10-21
I don't think it's mounting it twice but just putting up the normal desktop icon up that is showing there's a drive mounted, and you would use that icon by right clicking and selecting unmount or eject when you wanted to remove it.  If you really don't want the ubuntu icon there then you can disable it from displaying, but then you'de be unmounting it at the command line instead of being able to just use the gui.  I'd personally just change fstab to mount it somewhere other than the desktop but if you want want ubuntu to not display the icon then the setting is probably in gconf-editor but I don't know where.  I've seen it there quite a long time ago I think.
type in a terminal
gconf-editor
then hit edit and search.

---

