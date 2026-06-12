---
title: "trash is gone"
date: 2008-05-09
forum: General Help
---

### Post by illbashu on 2008-05-09
My trash bin is gone :/ i needed to get a file back from trash and i realized it was gone :/

---

### Post by amohanty on 2008-05-09
If it simply disappeared from the desktop, then in a terminal type:
gconf-editor

Navigate to this key:
/apps/nautilus/desktop/

Then make sure that the trash_icon_visible key is checked in the right hand side.

Also in Hardy the trashcan is actually here:

~/.local/share/Trash/files

Fire up the file explorer Home, goto View and then check show hidden files.

navigate to the location mentioned above and your trashed file should be there.

HTH
AM

---

### Post by illbashu on 2008-05-09
trash didn't come back :/ and i clicked around on the bottem toolbar and i found it but its inversiable... and i checked off trash_icon_visible

edit i have it on my desktop but its not showing on the panel but its there :/

---

### Post by treehouse on 2008-05-09
Alternatively, you can right click one of the panels, and select 'add to panel'. Select 'Trash' in the Desktop & Windows section, and click '+Add'.

---

### Post by illbashu on 2008-05-09
its on the panel but its the same color as the panel so i cant see it :/ i tried removing it from the panel but it wont work...

---

### Post by amohanty on 2008-05-10
can you post a screenshot? I am not sure I understand how its the same color as the panel

---

### Post by illbashu on 2008-05-10
it came back after i restared my comp.

---

### Post by Francewhoa on 2009-08-23
The following worked for me [http://ubuntuforums.org/member.php?u=55317](http://ubuntuforums.org/member.php?u=55317)

---

