---
title: "Removing panel sliders?"
date: 2007-02-28
forum: General Help
---

### Post by ~LoKe on 2007-02-28
I'm trying to get rid of (or hide) those little panel sliders on the taskbar.

Reference:
[img]http://img207.imageshack.us/img207/240/sliderwh2.jpg[/img]

Any ideas?

---

### Post by threethirty on 2007-03-01
right click on the panel-> Properties -> Show hide buttons

but I dont think thats your problem that is the edge of the window list, and I don't think that can be changed.

---

### Post by mcduck on 2007-03-01
First, download the picture attached (yes, it's there, it's 10x10px fully transparent pic) and save it in your home directory. Then create a file called '.gtkrc-2.0' inside your home dir, and paste the following code into that file and save:
```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= ".pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= ".pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
```

Last, check that you have 'gtk2-engines-pixbuf'-package installed.

Log out & back in and now the handles for window list and notification area applets are invisible.

(both files have a dot in front of their filename so they are considered hidden files. press Ctrl-h in nautilus if you need to see them)

edit: It was quite hard to click the invisible small attached pic so I put it in a zip file for you :)

---

### Post by adam.tropics on 2007-03-01
> **threethirty said:**
> right click on the panel-> Properties -> Show hide buttons

but I dont think thats your problem that is the edge of the window list, and I don't think that can be changed.

You can't get rid of them (grippies) but they are themeable. If you play with your  themes a bit, and adjust transparency, they can be just about invisible.

---

### Post by ~LoKe on 2007-03-01
> **mcduck said:**
> First, download the picture attached (yes, it's there, it's 10x10px fully transparent pic) and save it in your home directory. Then create a file called '.gtkrc-2.0' inside your home dir, and paste the following code into that file and save:
Last, check that you have 'gtk2-engines-pixbuf'-package installed.

Log out & back in and now the handles for window list and notification area applets are invisible.

(both files have a dot in front of their filename so they are considered hidden files. press Ctrl-h in nautilus if you need to see them)

edit: It was quite hard to click the invisible small attached pic so I put it in a zip file for you :)

That worked perfectly.

Thank you!!

---

### Post by Bagboy23 on 2007-03-01
Mcduck, do you have any more tricks? That was great and worked on my laptop too. :)

---

### Post by mcduck on 2007-03-02
> **Bagboy23 said:**
> Mcduck, do you have any more tricks? That was great and worked on my laptop too. :)

Sure, lots of. What do you want to do? ;)

Edit: Fix ugly buttons and text fields in Firefox? look here: [http://www.ubuntuforums.org/showthread.php?p=2227625#post2227625]("http://www.ubuntuforums.org/showthread.php?p=2227625#post2227625")
Disable those ugly wireframe animations when minimizing windows in Gnome/Metacity: [http://www.ubuntuforums.org/showpost.php?p=1979239&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=1979239&postcount=2")
Get nice transparent glassy panels: [http://www.ubuntuforums.org/showpost.php?p=2194660&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=2194660&postcount=4")

---

### Post by adam.tropics on 2007-03-02
> **mcduck said:**
> Sure, lots of. What do you want to do? ;)

Liked that solution...just had to do the same thing to my phone to get rid of a ridiculous operator logo!

Do you happen to know if you can force the issue where the resizing of scalable icons is concerned, in the panel...and notification area? As it stands, they resize to the size of my panel. I would like 2 pixels less than that!

---

### Post by mcduck on 2007-03-02
> **adam.tropics said:**
> Liked that solution...just had to do the same thing to my phone to get rid of a ridiculous operator logo!

Do you happen to know if you can force the issue where the resizing of scalable icons is concerned, in the panel...and notification area? As it stands, they resize to the size of my panel. I would like 2 pixels less than that!
As far as I know the only way would be to add 2 pixels of empty space in your icon files. Which might be quite a job to do..

---

### Post by adam.tropics on 2007-03-02
> **mcduck said:**
> As far as I know the only way would be to add 2 pixels of empty space in your icon files. Which might be quite a job to do..

That's what I figured, although I had hoped there would be a better way, since they are resized anyway...I just want them resized more! Thanks anyway.

---

