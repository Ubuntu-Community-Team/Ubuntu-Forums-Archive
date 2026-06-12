---
title: "gnome, firefox, and a fat32 partition"
date: 2007-02-01
forum: General Help
---

### Post by Absurd on 2007-02-01
Based on my experience, this problem seems to be specific to gnome or regular Ubuntu (but not Kubuntu). If I download a file using firefox into a directory on my fat32 partition, the file is saved as a NULL file (meaning, there's nothing in it--0B of data). 

Is there a way to fix this?

---

### Post by natedawg on 2007-02-02
Well I can confirm that this problem is not specific to gnome / firefox / fat32
I save files to my fat32 partition all the time without a problem (Edgy Eft). 
Perhaps you should try to reinstall Firefox?

Sorry I can't be be anymore of a help.

---

### Post by muguwmp67 on 2007-02-02
Could it be a permissions problem?

---

### Post by Absurd on 2007-02-02
[quote=natedawg]Well I can confirm that this problem is not specific to gnome / firefox / fat32
I save files to my fat32 partition all the time without a problem (Edgy Eft).
Perhaps you should try to reinstall Firefox?

Sorry I can't be be anymore of a help.[/quote]

No, I've tried that already. 

[quote=muguwmp67]Could it be a permissions problem?[/quote]

Maybe. I've already tried "$chmod 777 directory" and that didn't work (in coming files from firefox are still null). For some reason, chown doesn't seem to work either.

---

