---
title: "Desktop Issues-&gt; cannot click icons"
date: 2008-04-13
forum: General Help
---

### Post by jwnorma on 2008-04-13
I am having issues with my desktop.  Occasionally something will crash, and I can't click on the icons(left or right click), and when I try to drag them they don't render correctly (just get a distorted black image instead of the icon).  I also can't open the file explorer, but all other programs open correctly.

I am running compiz, but the visual effects seem fine still.  

I can't associate the crash with any particular event.  But here is my environment:

Dell XPS420 with Intel Duel Core 
4GB mem (not using all of it since its a 32 bit proc)
fakeRaid 
I do have a ntfs partition mounted using ntfs-3g
firefox
compiz enabled

Logging out and then back in fixes the problem.  And I can usually run for a couple hours until the problem emerges again

I appologize if this issue has been addressed in another thread, but I searched and couldn't find anything that matched the problems that I am seeing.


I appreciate any help, this is real frustrating.

Thanks

---

### Post by ryanhaigh on 2008-04-14
Seems like an issue with nautilus (or maybe nautilus+compiz), perhaps try using Alt-F2 then ```
nautilus -q
``` to shutdown nautilus then open your home directory (or anywhere else from the places menu) to restart nautilus.

---

