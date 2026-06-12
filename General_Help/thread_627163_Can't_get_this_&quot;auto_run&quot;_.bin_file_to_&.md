---
title: "Can't get this &quot;auto run&quot; .bin file to &quot;auto run&quot;"
date: 2007-11-29
forum: General Help
---

### Post by Lacent on 2007-11-29
I'm trying to install a poker game client, and it made me download a .bin file. It said it would run on its own, but when I double-click on it, it brings up gedit, and wants to open it as a text file, but cant. So then I tried opening it in terminal, but that didnt work (even though I did the chmod command) Thanks for the help

---

### Post by PmDematagoda on 2007-11-29
If the file is made for Windows then you cannot just run it on Linux, you will need some software like Wine which will run such applications on a Windows compatibility layer, in any case I don't know if Wine runs .bin files.

---

### Post by callan79 on 2007-11-29
> **Lacent said:**
> I'm trying to install a poker game client, and it made me download a .bin file. It said it would run on its own, but when I double-click on it, it brings up gedit, and wants to open it as a text file, but cant. So then I tried opening it in terminal, but that didnt work (even though I did the chmod command) Thanks for the help

Hi,

The only time I've used a .bin (so far) is to install Google Earth.

I put it on my desktop, then did this in terminal :

```

cd /home/callan/Desktop
sudo sh ./filename.bin   *note you might not actually need sudo*

```

Good luck!

Regards,
Callan

---

