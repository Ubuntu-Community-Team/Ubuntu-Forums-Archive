---
title: "Can I increase the size of the mouse grab area?"
date: 2017-11-14
forum: General Help
---

### Post by sterator on 2017-11-14
It's very tedious to resize windows because it seems like you're only given about 1 or 2 pixels' worth of room to grab and if you miss you're stuck trying over and over.

I don't think it's realistic to make the mouse/grab area so teensie. we aren't all gifted neurosurgeons with perfect dexterity..is there User control over how large the grab area is?

thank you!

---

### Post by vasa1 on 2017-11-14
> **sterator said:**
> It's very tedious to resize windows because it seems like you're only given about 1 or 2 pixels' worth of room to grab and if you miss you're stuck trying over and over.

I don't think it's realistic to make the mouse/grab area so teensie. we aren't all gifted neurosurgeons with perfect dexterity..is there User control over how large the grab area is?

thank you!Again, it may depend on which DE you're on because each DE has its own window manager.

---

### Post by amanchesterman on 2017-11-15
I'm currently using Xubuntu. One of its many handy features is that at the top left corner of each window -- in the title bar -- there is a small downward pointing arrow. Click on that and a menu of window options appears. One of those is 'Resize'. If it's greyed out, that's because the window is maximised: you need to click 'Unmaximise' first.
If you choose the Resize option, it immediately 'grabs' the bottom right corner of the window with the cursor pointer: all you have to do is to move the mouse/pointer across the screen to where you want the corner to be, and then click to 'ungrab' the window and leave it resized with its new dimensions. It's simple, quick and easy, and overcomes all the fiddling involved in trying to find the grab area.
I don't know which distro you are using but I believe that some others have this feature, or something like it. See if it's available in yours.

---

### Post by sterator on 2017-11-16
That sounds pretty handy...are those features available to Ubuntu?

I think that during my exploration of LXDE, I did encounter a tool..a palette...which may have offered control over sensitivity, but I don't recall it's name.

As I use Linux and the various so-called "desktop environments" more and more, I'm struck by the way system settings are spattered across perhaps a dozen doo-dads which can be thought of as handling user-configurable preferences.

I greatly appreciate the granularity, but it's going to take awhile until I memorize the names of them all, and which domain falls under which doo-dad.

---

### Post by sterator on 2017-11-16
One thing I noticed just now:  I have much better luck trying to grab the corner of a window or application window than the side of the same windows.

at the side, the "zone" seems to be just about a pixel or two, and as I press the stylus to the tablet, I lose the resize cursor! The corners are a little bit more forgiving, offering perhaps 4 pixels of "zone."

---

### Post by Holger_Gehrke on 2017-11-16
Another tip for xfce / XUbuntu: Alt Right-Drag (press and hold alt, drag with the right mouse button pressed instead of the left) resizes a (non maximized) window without having the mouse cursor on the border. The existence of this is basically the excuse XFCE-developers have for not giving the users a tool to set the width of the grab-able area. Similar to alt-drag to move a window (which seems to work on many DEs). 

Holger

---

### Post by again? on 2017-11-16
As it's not clear what desktop you're using, in gnome-shell (which ubuntu now uses) the
window manager, mutter has a border width setting.
You can access via dconf-editor > /org/gnome/mutter/draggable-border-width

or 

via commandline.
Default value is 10.
Can be set anywhere between 0-64.
eg
```
dconf write /org/gnome/mutter/draggable-border-width 20
```

To reset to default
```
dconf reset /org/gnome/mutter/draggable-border-width
```

---

### Post by sterator on 2017-11-17
guber2 -

Thank you. I've been back and forth between Cinnamon and LXDE. Cinnamon seems much better for me, and it has the larger grab-able mouse area, but I'd always like the option of altering it.

I have very good coordination but I need more than a pixel or two!

---

### Post by Impavidus on 2017-11-18
It may also depend on your theme. At least with Xubuntu, different themes provide a different grab area, depending on the thickness of the window decorations.

---

