---
title: "Really Puzzled..."
date: 2008-03-23
forum: General Help
---

### Post by Comhra on 2008-03-23
Just today, while browsing the file-system in Root ( sudo nautilus) I found a huge cache of stuff in my  /home/user/hidden files.   Leftovers from programs that I had deleted, they amounted to several hundreds of Mbs.

Grasping the nettle,  I sent these to Trash but when I looked in Trash just a few minutes later there was nothing there.  

Where did these files go?

Did Ubuntu erase them?

Furthermore, I  suspect that Ubuntu made a back up of these unwanted items because my Filesystem usage increased significantly.

I'm really puzzled as to what happens to unwanted items such as these; could some one please explain.

I've searched the net but couldn't find an explanation.

---

### Post by Oldsoldier2003 on 2008-03-23
> **Comhra said:**
> Just today, while browsing the file-system in[COLOR="Red"] Root ( sudo nautilus[/COLOR]) I found a huge cache of stuff in my  /home/user/hidden files.   Leftovers from programs that I had deleted, they amounted to several hundreds of Mbs.

Grasping the nettle,  I sent these to Trash but when I looked in Trash just a few minutes later there was nothing there.  

Where did these files go?

Did Ubuntu erase them?

Furthermore, I  suspect that Ubuntu made a back up of these unwanted items because my Filesystem usage increased significantly.

I'm really puzzled as to what happens to unwanted items such as these; could some one please explain.

I've searched the net but couldn't find an explanation.
empty root's trash. if you sudo nautilus and delete files they end up in root's trash bin, whereas sudo rm foo  deletes files completely.

---

### Post by Comhra on 2008-03-23
Thanks for that Old soldier, it makes sense now.

Btw, where do I find Root's Trash?

---

### Post by Comhra on 2008-03-23
Got it.

The command: gksudo nautilus '/root/.Trash/' brings it up.

Wow, I had a load of stuff in there.

Thanks for the help again Old Soldier.

---

