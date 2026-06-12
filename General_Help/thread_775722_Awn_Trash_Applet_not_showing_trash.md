---
title: "Awn Trash Applet not showing trash"
date: 2008-04-30
forum: General Help
---

### Post by bossa on 2008-04-30
Hi All
Been using Hardy since release  .My problem is the Trash applet and Stacks Trasher in AWN show no items when you hover the cursor over the Icon. Also the actual Trash icon shows empty.
I thought it might be because I was using the Mac for Lin icons but the same happens for all icon themes.
Any ideas?
Thanks

---

### Post by moonbeam on 2008-04-30
It's a known bug with awn on Hardy:

[https://bugs.launchpad.net/awn-extras/+bug/194431](https://bugs.launchpad.net/awn-extras/+bug/194431)

There are some workarounds posted in the bug.  Use at your own risk.

---

### Post by bossa on 2008-04-30
Cheers moonbeam ,Thanks for the link see how I go ;)

---

### Post by dirtblack on 2008-04-30
I have come across that myself, Last night I put trash in the can that's in awn. It works that way, If I go from a menu and delete nothing. Thought I'd let everyone know the buggy way it works.

---

### Post by cszikszoy on 2008-05-06
Don't think they are using GIO / the new gvfs code.  And putting things in awn's trash just puts it in the old trash location ~/.Trash.  Deleting won't work because it's trying to use the code that was there before gvfs.  Hopefully they'll fix this soon!

There was a solution in the AWN forums about creating a symbolic link from /.local/share/trash to ~/.Trash.  Not really sure if that's a good idea or not.  Think i'll just remove it and wait until they fix it.,

---

### Post by RAOF on 2008-05-06
> **cszikszoy said:**
> ...
There was a solution in the AWN forums about creating a symbolic link from /.local/share/trash to ~/.Trash.  Not really sure if that's a good idea or not.  Think i'll just remove it and wait until they fix it.,

That's probably not such a good idea; the ~/.local/share/Trash directory contains more than just the stuff you deleted.  It also contains enough metadata about the stuff you deleted to allow you to later restore them - hence the files/ and info/ subdirectories.

Just flat out deleting files/ and info/ *should* work to empty the whole trash, but trying to selectively delete stuff from files/ without removing the associated metadata in info/ is likely to confuse GNOME.

---

