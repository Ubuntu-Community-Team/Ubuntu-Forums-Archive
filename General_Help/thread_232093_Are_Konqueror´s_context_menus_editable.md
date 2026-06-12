---
title: "Are Konqueror´s context menus editable?"
date: 2006-08-08
forum: General Help
---

### Post by André on 2006-08-08
Hi everybody,

i just noticed that for me a right click on a file in Konqueror often gives me many options that i do not need.

I like my menu small and without too many entries. So i would like to know: Is it possible to edit the context menus (menus i get when i right-click on a file)??

Do you think my changes will be gone when i update to a new version of konqueror?

Any help is appreciated.

Greetings
André

---

### Post by Jucato on 2006-08-08
These context menus in Konqueror are called "service menus". Almost each entry (almost) has a config file that you can either edit or delete.

They are found in 3 different places:
/usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror/servicemenus - has the Kubuntu's specialized service menus (not much here)

/usr/share/apps/konqueror/servicemenus/ - has the system-wide service menus

~/.kde/share/apps/konqueror/servicemenus/ - has the local (user only) service menus.

Just browse around to see which you don't need/want. My advice, don't delete them. Put them in a separate folder for safe keeping. You never know when you might want them back. :D

---

### Post by André on 2006-08-08
Hey,

thanks for the answer. I will check it out asap.

Sounds like i can get KDE the way i want :-)

Do you think these will be killed after the next update?

Greetings and thanks again
André

---

