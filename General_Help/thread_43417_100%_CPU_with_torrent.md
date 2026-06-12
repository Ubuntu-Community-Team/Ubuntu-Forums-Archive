---
title: "100% CPU with torrent"
date: 2005-06-21
forum: General Help
---

### Post by chz on 2005-06-21
i first tried using the Gnome Bittorrent that came with hoary. I noticed after maybe 5 minutes of use, the computer shutdown. So i ran it again, it shutdown again but much faster this time...so i ran it once more and then ran as well the System Monitor. There i noticed the CPU line at 100%...i shut down Gnome Bittorrent and...it went straight back down to almost 0. 

I figure maybe its the application...so i download Azureus. Pretty much the same thing but it takes azureus longer for it to build up to 100 and it spikes high in intervals, kind of like a dead heartbeat slowly pumping itself bak up until its just a straight line again up at the top. 

I do notice that i when i stop the torrent file from downloading, it goes back to normal so i dont think its an application issue, but a torrent issue.

Does anybody have suggestions on what i could do?

---

### Post by qd989 on 2005-06-21
renice the process to a lower priority?

---

### Post by chz on 2005-06-21
i thought about that, but i have no idea how i would go about doing that..?

---

### Post by chz on 2005-06-21
ahh..i figured out how to renice...i'll update to see if it works...

---

### Post by chz on 2005-06-21
i think i figured out what the problem was..

since i had saved the file to the desktop, gnome/nautilus was updating the thumbnail as well as the info of the file along side with what was being downloaded...causing these oddly high cpu peaks. i then changed the final destination of the download to within the home directory, and from there i had not noticed any intense increase on the cpu. i tried with both a high and low 'nice' value...so priority was not the issue.

moral of this story...dont save files to the desktop....best if you save elsewhere and then copy to the desktop.

---

### Post by bored2k on 2005-06-21
[QUOTE=chz]i think i figured out what the problem was..

since i had saved the file to the desktop, gnome/nautilus was updating the thumbnail as well as the info of the file along side with what was being downloaded...causing these oddly high cpu peaks. i then changed the final destination of the download to within the home directory, and from there i had not noticed any intense increase on the cpu. i tried with both a high and low 'nice' value...so priority was not the issue.

moral of this story...dont save files to the desktop....best if you save elsewhere and then copy to the desktop.[/QUOTE]
 I'll keep that in mind.. no desktop :).

Tip: If I were you I would use the official Bittorrent. It is miles away better than gnome-bt, and its latest updates are great. [http://www.bittorrent.com/](http://www.bittorrent.com/) (download the source file, then run btdownloadgui.py). Or you could switch to the hogger Azureus (wich oddly, is running great and fast now).

---

