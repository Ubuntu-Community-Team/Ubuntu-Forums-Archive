---
title: "Edgy broke my graphics"
date: 2006-10-26
forum: General Help
---

### Post by Skia_42 on 2006-10-26
I was updating my laptop last night and my batterys died mid-isntallation. When I started it again the graphics were not working. I ran "sudo apt-get dist-upgrade", it installed updates but the graphics are still not working. I am suspectng my i810 graphics driver is not working properly. Does anyone know a solution or a way to see what hardware drivers are loaded?

---

### Post by magicfab on 2006-10-26
"lsmod" will tell you what modules are loaded.

i would suggest using a CDROM and choosing a rescue option.

---

### Post by Skia_42 on 2006-10-26
How do i telln it to display the output in sections rather than all at once? What whould i do in rescue mode?

---

### Post by magicfab on 2006-10-27
use "lsmod > filename.txt " to keep the output in a file, or "lsmode | more" to have a pager so you can read 1 page at a time.

A second thought, did you try apt-get update / apt-get upgrade again to see if it can recover from there ?

---

### Post by Skia_42 on 2006-10-27
I will check the drivers when i get home, thanks for the trick. I tried the update again after the crash. I will check both commands in a bit. thanks.

---

