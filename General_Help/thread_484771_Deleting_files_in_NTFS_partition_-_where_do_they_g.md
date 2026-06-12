---
title: "Deleting files in NTFS partition - where do they go?"
date: 2007-06-26
forum: General Help
---

### Post by floke on 2007-06-26
Just deleted some large iso's in my NTFS partition from ubuntu, which, I assumed would be moved to the deleted items folder as indicated by the menu. But they are not there, are not in root trash, and can't be found by Windows.

Anyone know where they have gone? (just want to make sure they have, really).

---

### Post by Qu4k3R on 2007-06-26
in the terminal (or nautilus)
go to
/media/<your_windows_partition>

then just go to the folder named:

/.Trash-<your_username>/

example:

> 
cd /media/windowsXP/.Trash-quake/


---

### Post by floke on 2007-06-26
Aha!
Cheers.

---

