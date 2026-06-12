---
title: "Back-ups Like Apple"
date: 2006-10-08
forum: General Help
---

### Post by simoncoul on 2006-10-08
Hey I watched the Apple video for leopard and same the Time Machine thing and thought it was very intresting.   I was thinking about it and do you guys think that there would be a way to do this in Ubuntu?

I was thinking, if you had a User folder, and created a link to another folder on a different drive/partition that had root premissions so that any changes made to the User folder would get reflected in the root folder.   Then if something was deleted from the User folder the same thing would happen to the root folder, but the root trash would not get emptied when you emptied the user trash.   Therefore if you deleted something you needed, you could go into the root folder trash and find it.   Let me know if you guys think something like this would be possible, and how to go about if you know.

Thanks

---

### Post by nix4me on 2006-10-08
rsync

---

### Post by bobbybobington on 2006-10-08
As long as it works well and has nice gui, i'm happy.

---

### Post by aysiu on 2006-10-08
Sounds like *rsync* to me.

I love *rsync* and use it every week.

If you need a GUI frontend, try *grsync*.

---

### Post by simoncoul on 2006-10-09
Can you explain how grsync works a bit please?

Thank you

---

### Post by aysiu on 2006-10-09
It syncs one directory to a backup directory.

You can have the option to have a full sync (delete from 1, deletes from 2 also) or just a positive sync (add or change from 1, adds or changes from 2, but a delete from 1 doesn't delete from 2).

There are a lot of options for how *rsync* will behave.

[http://www.opbyte.it/grsync/screenshot.html](http://www.opbyte.it/grsync/screenshot.html)

---

### Post by simoncoul on 2006-10-09
Alrite sounds good, I'm gonna give it a try in a few days when my new HDD comes in.

Thank you!

---

### Post by aysiu on 2006-10-09
P.S. *rsync* will not work on FAT32.

---

### Post by lemonsCC on 2006-10-09
Although this may accomplish the same thing, it will not have the eye candy that Time Machine will have.

P.S  I'm not sure I like the idea of time machine, it I delete something after it went to the Trash Can, I don't want it back...That's why it was deleted.  Hmmmm...

---

