---
title: "[SOLVED] I'm confused about 'trash' and /root/trash and my 'home' and places&amp;gt;home"
date: 2008-06-28
forum: General Help
---

### Post by sofasurfer on 2008-06-28
I have another hard drive mounted for storage of backup files. When I want to delete a backup file I right click and I see that I can chose 'trash' but I don't get a 'delete' option. Why is there no 'delete' option?

So, I click on 'trash' ( since there is no delete ) and the file disappears, but it is not in taskbar>trash. However, I did find it in /root/.local/share/Trash/files. I did not know this directory existed. I assume that this is the trashcan for the 'root' user. But my questions is this, why did my file NOT go into the ordinary trash? I have deleted other stuff under sudo and not had this happen. Is this something I can change?

Another similar situation occurs with 'home'.
I can browse to file:///home/daryl/Documents. In the process I click on/home, then daryl, then Documents. But when I click on places>home folder, the path immediately shows <daryl even though I clicked on 'home', not 'daryl'.

Why the confusion? Thanks.

---

### Post by fragos on 2008-06-28
You can configure the delete button in Nautilus for the current user. With 8.04 came the relocation of trashed files to the location you found. Root is also a user and has it's own trash folder as well as configuarion files Metacity, Gnome, Nautilus, Gedit and etc.

---

