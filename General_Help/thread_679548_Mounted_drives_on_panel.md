---
title: "Mounted drives on panel"
date: 2008-01-27
forum: General Help
---

### Post by Elpants on 2008-01-27
Hello. I did a search for this and didn't find anything on what I am looking for.

I use a 500 gig external hard drive for all my media as well with having a 1gig thumb drive I use for ready boost in Vista, which I usually unmount. which brings me to my first question. Can I configure the thumb drives to not mount to the desktop when I start up Ubuntu?

Now my main question is, Can I have the 500 gig hard drive show an icon on the panel/taskbar instead of showing on the desktop?

---

### Post by LaRoza on 2008-01-27
```

gconf-editor

```

Apps->Nautilus->Desktop

Turn it off.

There are not mounted to the Desktop, GNOME is configured (by default in Ubuntu) to shore mounted drives in /media/ on the desktop.

You can use the Disk Mounter Applet. (Right click panel, add to it)

---

### Post by Elpants on 2008-01-27
Thanks for the quick reply, now to just get conky working:popcorn:

---

