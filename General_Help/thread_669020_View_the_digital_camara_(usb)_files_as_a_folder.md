---
title: "View the digital camara (usb) files as a folder"
date: 2008-01-16
forum: General Help
---

### Post by tiptip on 2008-01-16
Hello,

I have a digital camera and when i connect it with the usb cable the build-in
tool of ubuntu pop-up and let me download the pictures.
How can i browse the pictures as in a folder ? (same as in windows)
I don't cannot find where ubuntu auto-mount it.

Thanks ahead (:

---

### Post by DagMan on 2008-01-16
Usually there's an icon on the desktop, but if you don't have that or it won't let you browse, things get automounted in the /media directory.
If it creates the folder when it mounts it then the name might change depending on what you mounted, but if you have a look it should be straght forward, so you'de just navigate to media in the file browser or type
nautilus /media
in a terminal and see what folders are there.

If you're using GNOME and the problem is that an icon is not appearing when it's mounted, then there's probably just a setting box to be ticked in the configuration editor. If you always want to view it using a folder view then the behaviour can be changed with that either with the configuration editor or through prefered applications or somewhere in the menu like that.  I'm not sure right now and don't have Ubuntu in front of me.

---

### Post by kostkon on 2008-01-16
> **tiptip said:**
> Hello,

I have a digital camera and when i connect it with the usb cable the build-in
tool of ubuntu pop-up and let me download the pictures.
How can i browse the pictures as in a folder ? (same as in windows)
I don't cannot find where ubuntu auto-mount it.

Thanks ahead (:

Most cameras have an option in their configuration menu where you can select the way that they connect to the PC.

You have *gthumb* popping up and asking you to import your photos because your camera is set to use the [*PTP protocol*]("http://en.wikipedia.org/wiki/Picture_Transfer_Protocol") to communicate with the PC.

In order to make the camera to mount as a drive in Ubuntu you have to set it to work as a mass storage device. Check the configuration of your camera to see if you have such an option.

---

### Post by tiptip on 2008-01-16
*"set it to work as a mass storage device"*

Thanks guys that sort the things.
i <3 ubuntuforums

---

