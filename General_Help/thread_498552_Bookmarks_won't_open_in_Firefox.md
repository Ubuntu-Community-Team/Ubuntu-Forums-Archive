---
title: "Bookmarks won't open in Firefox"
date: 2007-07-11
forum: General Help
---

### Post by CrankyFilipino on 2007-07-11
As usual I don't know when it happened.. but about an hour ago I noticed that no bookmarks would be opened by Firefox at all. I've tried all sorts of combinations of exporting/importing in other browsers after deleting them, hoping that a fresh start would make them work. Yet nothing works, they just seem to not want to open. Now I've already spent numerous times tweaking firefox to work great. I've installed Ubuntu FF 7.04 twice.. and Now Ultimate Ubuntu 1.4 twice.. and I FINALLY got it all set up to working smoothly.. and now I get this quirk.. is it just one more little quirk of Firefox? Has anyone had this problem?

---

### Post by TheExplorer on 2007-07-12
Haven't you checked "Block pop-ups" or something? Play with "Open links in new tabs" and stuff like that.
Could be kinda incompatibility issue between the browser and third party extensions. Have you got any? Try deleting them or just reinstall Firefox.

P.S. Try not to tweak a lot the browser with third party tools or things like that since they only reduce the functionality of it.

---

### Post by kngunn on 2007-07-12
I would try exporting your bookmarks, then deleting them from the disk, then importing from the exported copy. I suspect the bookmarks.html file is corrupt.

In your home folder there is a hidden folder called ".mozilla" (notice the period:  that's what makes it hidden).  Inside that there is a folder called firefox.  Inside THAT is a folder that looks like a long string of garbage which ends in ".default".  Inside THAT you'll find "bookmarks.html".  That's the file to delete.

Hope that works!

---

### Post by CrankyFilipino on 2007-07-12
Well I've actually tried the exporting and deleting and everything.. I was hoping to be able to do it without reinstalling firefox, because I have it tweak in the about:config real well.. and just plain old tired of reinstalling anything right now.. as this is the second time in a few days I've installed UU 1.4.. the only way that the bookmarks open, which I forgot to mention.. is when I open all of them in tabs at once.. so right now I use epiphany for my bookmarks on this machine.. unfortunately I can't export those to firefox.. which is weird.. but oh well.. thanks guys.. I guess I'll keep trying..

---

