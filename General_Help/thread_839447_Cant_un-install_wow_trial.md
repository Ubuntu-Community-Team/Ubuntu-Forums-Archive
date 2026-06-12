---
title: "Cant un-install wow trial"
date: 2008-06-24
forum: General Help
---

### Post by Karnus115 on 2008-06-24
i have downloaded the wow trial client by mistake and it is currently in my wine menu as "world of warcraft trial". i have downloaded the full world of warcraft game and it is "world fo warcraft" in my wine menu.

now my problem is that i want to delete the wow trial, however when i go to wines remove programs menu, it only has "world of warcraft", how can i delete the trial and keep the full game.

i have searched these forums and looked around but i havent had much success.

i have only been using linux for 2 days now so be kind :) (using ubunto 8.04)

thanks in advance

---

### Post by bapoumba on 2008-06-24
> **Karnus115 said:**
> .. i have downloaded the full world of warcraft game..
Legally ?

---

### Post by LinuxRocks713 on 2008-08-18
cd ~/.wine/drive_c/Program\ Files
rm -r *WorldOfWolfcraft_Folder*
wine regedit
# ...and remove the offending entry with this guide: [http://support.microsoft.com/kb/314481](http://support.microsoft.com/kb/314481)

---

