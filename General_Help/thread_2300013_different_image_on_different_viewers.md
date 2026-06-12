---
title: "different image on different viewers"
date: 2015-10-23
forum: General Help
---

### Post by jeevansai2 on 2015-10-23
I was trying to use an [image]("http://www.aspose.com/java/imaging-component.aspx")  in a gui but i observed that the image looks different on different  viewers .Can someone tell why, screenshots in  viewers are attached.

---

### Post by ajgreeny on 2015-10-23
The grid effect in your first screenshot is how many viewers show a transparent background.

Gthumb does not show the background in that way; it just shows the real image shape with no transparent background at all, but gimp, for example, allows you to change how transparency is shown on screen in the Edit->Preferences->Display->Transparency settings.

I don't know what viewer your first shot is showing but it may be possible to change the way transparency shows in that in some way by finding its config files.

---

