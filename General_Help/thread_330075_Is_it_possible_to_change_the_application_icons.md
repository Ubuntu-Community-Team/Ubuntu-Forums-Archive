---
title: "Is it possible to change the application icons?"
date: 2007-01-02
forum: General Help
---

### Post by Quillz on 2007-01-02
Attached is a screen shot of the menu bar of Mozilla Thunderbird (1.5.0.8). What I want to know is if it is possible to change the icon in the top-left corner, from the generic envelope to something else. And if so, how would I do it?

---

### Post by Quillz on 2007-01-02
On a similar note, is there a way to change the icons displayed in the drop-down menu?

---

### Post by jasutton on 2007-01-02
The icons for the title bar are in /usr/share/mozilla-thunderbird/chrome/icons/default.  I'm attaching the original icons from mozilla.org's tgz (messengerWindow.xpm and messengerWindow16.xpm, which I'll have to zip up to attach to this post).

The other artwork is actually stored in a file called messenger.jar.  I've unpacked that file and replaced it with the original artwork (and re-packed it), and I'm going to upload that to my website for you to download (since it's a little bigger).  I'll PM you the link.  You'll need to place that in /usr/share/mozilla-thunderbird/chrome (I would rename the old file just in case ;) ).

I've been meaning to do that myself for a while, but I just haven't thought of it when I had a chance :)

---

### Post by raul_ on 2007-01-02
[http://www.ubuntuforums.org/showthread.php?t=199193&highlight=restore+thunderbird+firefox+icons]("http://www.ubuntuforums.org/showthread.php?t=199193&highlight=restore+thunderbird+firefox+icons")

---

### Post by Quillz on 2007-01-03
> **jasutton said:**
> The icons for the title bar are in /usr/share/mozilla-thunderbird/chrome/icons/default.  I'm attaching the original icons from mozilla.org's tgz (messengerWindow.xpm and messengerWindow16.xpm, which I'll have to zip up to attach to this post).

The other artwork is actually stored in a file called messenger.jar.  I've unpacked that file and replaced it with the original artwork (and re-packed it), and I'm going to upload that to my website for you to download (since it's a little bigger).  I'll PM you the link.  You'll need to place that in /usr/share/mozilla-thunderbird/chrome (I would rename the old file just in case ;) ).

I've been meaning to do that myself for a while, but I just haven't thought of it when I had a chance :)Thanks for the attachment; it was quite useful. Does messenger.jar control all the application icons?

> **raul_ said:**
> [http://www.ubuntuforums.org/showthread.php?t=199193&highlight=restore+thunderbird+firefox+icons](http://www.ubuntuforums.org/showthread.php?t=199193&highlight=restore+thunderbird+firefox+icons)
Thank you for the link.

---

### Post by Quillz on 2007-01-03
> **jasutton said:**
> The icons for the title bar are in /usr/share/mozilla-thunderbird/chrome/icons/default.  I'm attaching the original icons from mozilla.org's tgz (messengerWindow.xpm and messengerWindow16.xpm, which I'll have to zip up to attach to this post).

The other artwork is actually stored in a file called messenger.jar.  I've unpacked that file and replaced it with the original artwork (and re-packed it), and I'm going to upload that to my website for you to download (since it's a little bigger).  I'll PM you the link.  You'll need to place that in /usr/share/mozilla-thunderbird/chrome (I would rename the old file just in case ;) ).

I've been meaning to do that myself for a while, but I just haven't thought of it when I had a chance :)
I don't have permission to write to the /default/ folder. How do I take control of the folder?

---

### Post by petersjm on 2007-01-03
> **Quillz said:**
> I don't have permission to write to the /default/ folder. How do I take control of the folder?

In a terminal, type:
gksudo nautilus /usr/share/mozilla-thunderbird/chrome/icons/default

---

### Post by Quillz on 2007-01-03
> **petersjm said:**
> In a terminal, type:
gksudo nautilus /usr/share/mozilla-thunderbird/chrome/icons/default
Thank you, that worked.

---

### Post by petersjm on 2007-01-03
> **Quillz said:**
> Thank you, that worked.

You're welcome :D

---

