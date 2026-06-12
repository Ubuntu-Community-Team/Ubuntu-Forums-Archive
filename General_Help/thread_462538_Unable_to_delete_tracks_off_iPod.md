---
title: "Unable to delete tracks off iPod"
date: 2007-06-02
forum: General Help
---

### Post by fooqwah on 2007-06-02
Background first: I'm on Feisty (Ubuntu), my iPod is a 5th gen 30 gig video (Windows formatted)

Some of my music was corrupted on my ipod, so I attempted to delete it.  It disappears from the listings, but the actual file does not come off the iPod, and the space used remains the same.

Example: I had 10 gigs of music, deleted it, had no music on the ipod, but still only had 17 gigs free.  I used gtkpod to search for lost music, it found it, restored it, and now I'm down to 7 gigs.

I've tried deleting the music with YamiPod, GTKPod, Rhythmbox, and even Amarok

All I want is the iPod empty, and the space back, without having to reinstall my old Windows hard drive just to reformat the iPod

---

### Post by DirtDawg on 2007-06-02
HAve you tried looking for a '.Trash' folder on your ipod? In Nautilus go to "View>Show Hidden Files" or CTRL+H, and if you see a .Trash folder, delete it.

Often when you throw things away from an external hard drive, nautilus creates a hidden ".Trash" folder that makes it appear like things are deleted, but they are actually not. 

You can create a "Delete" right-click menu in EDIT>PREFRENCES>BEHAVIOR click the option for  "create a delete command that bypasses the trash can" (or whatever its called).\

Hope this helps.

---

### Post by fooqwah on 2007-06-03
Brilliant, thanks for the help, worked perfectly.  Can't thank you enough.

---

