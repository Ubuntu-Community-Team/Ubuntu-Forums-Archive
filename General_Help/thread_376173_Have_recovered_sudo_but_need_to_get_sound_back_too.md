---
title: "Have recovered sudo but need to get sound back too"
date: 2007-03-04
forum: General Help
---

### Post by _asc_ on 2007-03-04
Hello!

I have the same problem. Thank's to the link aysiu posted, I have the sudo privileges back, but my sound still does not work. When I click on the volume control I get the following error message:

> 
No volume control GStreamer plugins and/or devices found.


Can anybody help?

---

### Post by _asc_ on 2007-03-04
I just found the solution, I had to add my user to the audio group.

Could anybody please list all the groups, that the default user is a member of?

Background:
I installed VirtualBox and added myself to the vboxusers group using the 'usermod -G' command.  As a result my user is in the vboxusers group, but not in any other groups. Thus I lost my sudo privileges and my sound. I was able to fix that by adding my user to the admin and the audio group. Now I just want to know if I have to add myself to any other group to make sure that everything really is back to normal.

---

### Post by jocko on 2007-03-04
These are the groups my user is part of:
```
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
``` plus one group with my username

---

### Post by _asc_ on 2007-03-05
Thank's !

---

