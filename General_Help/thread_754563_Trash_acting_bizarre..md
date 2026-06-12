---
title: "Trash acting bizarre."
date: 2008-04-13
forum: General Help
---

### Post by Alucard-sama on 2008-04-13
For a while now my trash has been telling me it has 86 items in it.
When I click to see what they are trash: is completely empty (well not exactly, but I'll get to that), yet, the "Empty Garbage Bin" thing is still there.
When I click it it then says "Deleting file 0 of [a couple thousand and counting files]" and just keeps saying it's deleting everything in my Home folder, which -thankfully- it is not.
Ontop of this I have a folder in the Garbage Bin that I cannot delete it tells me that Permission is denied. I can move this file out of the Garbage Bin but I can't permanently delete it. :(
Anybody have any idea what's going on with the Trash?

---

### Post by ryanhaigh on 2008-04-14
Just a guess: it could be that you 'deleted' some files on a external drive or something which placed these item in a trash folder on that device. You have yet to empty these items and maybe that is why you are getting this strange behaviour. 

I had a really weird problem after trying to delete my Desktop folder (accidentally) I had to login as admin in the console and move the Desktop folder back.

You should be able to remove the item you are trying to using ```
sudo rm /path/to/file
``` alternately you could run a nautilus instance as admin/root by pressing alt-f2 then entering ```
gksudo nautilus
``` you should then be able to delete anything JUST BE CAREFUL!!!

---

### Post by Alucard-sama on 2008-04-17
Thanks I managed to delete the files, however I don't have an external drive and I'm pretty sure I've never deleted the Desktop :\

---

