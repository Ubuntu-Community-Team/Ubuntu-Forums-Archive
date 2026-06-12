---
title: "USB memory stick opens wrong program"
date: 2007-10-17
forum: General Help
---

### Post by geovino on 2007-10-17
When I plug in my USB memory stick, RhythmBox music player opens instead of Nautilus file manager. How do I change that?

---

### Post by DagMan on 2007-10-17
I'm only guessing at the following but it sounds sane even though I haven't tried.

system->preferences->prefered applications

and then in multimedia change to custom and put in
nautilus /path/to/mount/point
I'm sort of just guessing the above though.  Just nautilus by itself with no path might work just fine but if not and a path is needed you would also have to define a mount point in fstab and create the directory and chown it so your user has priveleges for it if you aren't set up like that now.  Try it just using nautilus by itself though and see if that works.   The downside here also to this method is that nautilus will open when you insert an mp3 player and not rhythmbox, which you can launch from the menu though.

Post again if you need help with defining a mount point and making an fstab entry to use it every time.  Or if this just plain does't work so others can stay away from advice that I haven't tested.

---

### Post by geovino on 2007-10-18
The only options I have in Preferred Applications are for the browser, email and terminal, I don't have a multimedia option to change. Could it be somewhere else?

---

### Post by DagMan on 2007-10-18
Okay I'm not sure this doesn't just merely do the same thing that clicking the checkboxes does, but there's values, if you type
**gconf-editor **
then go to 
Desktop->Gnome->Volume Manager->Prompts

Mine are all set to zero and I get prompted when it wants to do things like import photos, to which I say no, and I don't really insert devices with music to know if it's the same shabang, but maybe you selected yes once for music files with a tick box overlooked and now it's set itself to open Rhythmbox everytime it sees them from a gnome-volume-manager mounted device.  Hopefully that's the reason anyway so it gets sorted more quiclky.

---

### Post by geovino on 2007-10-18
I went to the gconf-editor and all prompts were 0s.

Maybe it's somewhere else to control what opens when you plug in a memory stick.

---

### Post by chrisccoulson on 2007-10-18
Try running gnome-volume-properties from a terminal. It's in the preferences menu as Removable Drives and Media.

Although, I'm not sure it'll help you to change this behaviour though.

---

### Post by geovino on 2007-10-18
I did that. There is no preference menu for Removable Drives and Media.Everything is checked with no mention of a music program to open.

---

