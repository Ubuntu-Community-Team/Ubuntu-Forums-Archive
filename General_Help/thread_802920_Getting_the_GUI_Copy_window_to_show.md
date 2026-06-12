---
title: "Getting the GUI Copy window to show"
date: 2008-05-21
forum: General Help
---

### Post by Sleaka J on 2008-05-21
Ok, here's what I have and what I want.

I currently have a shell script that copies over my Team Fortress 2 GCF files from my Windows Steam install to my Linux/Wine Steam Install. This is working fine in terminal, but nothing shows in the terminal while it's copying over 6.5Gb of data.

I want to see the Nautilus copy window to show the progress, however I don't know the command. My understanding of Linux is growing (it was easy to figure out a script), but it's still fairly limited.

If it matters, I'm using Ubuntu 8.04.

Here's the script as it is currently:

```

#!/bin/sh
cp "/media/GAMES/Steam/SteamApps/source 2007 binaries.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/source 2007 shared materials.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/source 2007 shared models.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/source 2007 shared sounds.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/source materials.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/source models.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/source sounds.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/team fortress 2 client content.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/team fortress 2 content.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps
cp "/media/GAMES/Steam/SteamApps/team fortress 2 materials.gcf" /home/sleakaj/.wine/drive_c/Steam/steamapps

```

---

### Post by Sleaka J on 2008-05-22
Does anyone know what the command for bringing up the GUI copy progress bar from a terminal script is?

If I know what it is, I'll just substitute it for "cp" in my script.

---

### Post by Sleaka J on 2008-05-23
So, no-one knows?

---

### Post by sdennie on 2008-05-23
I don't think it's possible to do what you are asking.  However, something that's fairly close would be to replace all your "cp" commands with "cp -vu".  That will give you some feedback as to what is going on and will only copy files that are out of date.

---

### Post by Sleaka J on 2008-05-23
Ok, it doesn't actually NEED to be the GUI copy window. I just thought it might have a terminal command and that doing it that way would be easier. I did at least want some sort of feedback while copying the files.

I'll try your suggestion and we'll see how that goes.

---

