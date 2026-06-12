---
title: "Burning: two seconds worth, then fixating"
date: 2005-05-21
forum: General Help
---

### Post by Nick Post on 2005-05-21
Holy hell, will I ever get this thing 100%.  Here's my latest bit.

I've installed Gnome-baker.  Also, there's the Nautilus burner, and this exact thing happens with both.

Once it starts burning, it does so for maybe, at most, 8 seconds, usually less, and then says it's fixating.  The percent done jumps to 100% and it spits out my CD.

The cd is crap.  It looks like everything is on it, and the correct size, so obviously some kind of FAT table is being burned, but the files aren't really there.

Anyone?  Much thanks in advance.  Tell me what would be useful to paste here for help in helping.

---

### Post by jeremy on 2005-05-21
I had exactly the same problem with Hoary 5.04, have since changed to kubuntu, and all is now well.
To be hanest, I can't remember what I did to fix it (with gnome), but, as a first step I suggest that you check if DMA is on for your burner;
sudo hdparm /dev/hdc <- where hdc is your burner.

---

