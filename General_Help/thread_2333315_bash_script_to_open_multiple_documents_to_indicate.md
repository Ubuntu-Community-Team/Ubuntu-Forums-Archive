---
title: "bash script to open multiple documents to indicated Compiz Desktop Cube viewports"
date: 2016-08-09
forum: General Help
---

### Post by chaopoch on 2016-08-09
With the help from LibreOfficeForum, I write a bash script to open multiple .ods documents as follows.

Now,I need more helps to modify the script to open these documents to indicated Compiz Desktop Cube viewports,
such as a.ods in [COLOR=#000000]workspace[/COLOR]1,  b.ods in [COLOR=#000000]workspace[/COLOR]2, c.ods in [COLOR=#000000]workspace[/COLOR]3,

Any comments? thanks a lot.

===============================================
#!/bin/bash
libreoffice /media/sda2/a.ods /media/sda2/b.ods /media/sda2/c.ods

---

### Post by chaopoch on 2016-08-10
Please help, thanks!

---

### Post by CatKiller on 2016-08-10
devilspie can probably be incorporated into your script to do what you want. The different faces of the cube are workspaces.

---

### Post by chaopoch on 2016-08-10
> **CatKiller said:**
> devilspie can probably be incorporated into your script to do what you want. The different faces of the cube are workspaces.

Thanks for reply, I have modified my original thread.

I have read the devilspie document ([https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)), that is not what I want, however, thank you .

---

### Post by CatKiller on 2016-08-11
> **chaopoch said:**
> Thanks for reply, I have modified my original thread.

I have read the devilspie document ([https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)), that is not what I want, however, thank you .

Fair enough, although placing specified windows on particular workspaces is exactly what devilspie does.

As an alternative, Compiz has its own window placement plugin. I always found it less reliable than devilspie, though.

---

