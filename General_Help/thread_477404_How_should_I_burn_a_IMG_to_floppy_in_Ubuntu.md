---
title: "How should I burn a IMG to floppy in Ubuntu?"
date: 2007-06-18
forum: General Help
---

### Post by Altarbo on 2007-06-18
I want to put a .IMG file directly onto a floppy disk.  How does this work in Ubuntu?  I can't find an app to do this, so I'm assuming there's something I should use on the command line? 

I've tried:
sudo dd if=~/burn/M64-063.IMG of=/media/floppy0
but it spat out this error message: 
`/media/floppy0': Is a directory

---

### Post by anaconda on 2007-06-18
> **Altarbo said:**
> I've tried:
sudo dd if=~/burn/M64-063.IMG of=/media/floppy0
but it spat out this error message: 
`/media/floppy0': Is a directory

I would try with:
sudo dd if=~/burn/M64-063.IMG of=/dev/fd0

Dont know if the "~" works, but you can always substitute it with the actual path.

And there must be easier ways also, but dd is good for many things like this.

---

