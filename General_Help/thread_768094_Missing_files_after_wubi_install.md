---
title: "Missing files after wubi install"
date: 2008-04-26
forum: General Help
---

### Post by charistas on 2008-04-26
Yesterday i installed Ubuntu 8.04 LTS with the help of Wubi. From what i've read i should be able to access my windows files (e.g. Music, Photos, Documents etc) from Ubuntu without problems. Unfortunately, when i open the "host" or "media" folder i don't see my files. Can i get some help with that ?

---

### Post by ago on 2008-04-26
/host is the same drive where you installed Wubi. If you installed Wubi in D:, /host will be D:.

for /media you have to drill inside the subfolders, there is one folder for each partition.

---

### Post by charistas on 2008-04-26
> **ago said:**
> /host is the same drive where you installed Wubi. If you installed Wubi in D:, /host will be D:.

for /media you have to drill inside the subfolders, there is one folder for each partition.

Maybe i wasn't clear enough, but i know where host folder is. I've installed Wubi in C: drive so it's in C and i can see it. 

The problem is that i cannot access the files inside the host folder (neither in media). 

For example when i open media folder and then Music i don't see any of my .mp3 files in it. Same for a .txt file inside the Documents of my personal folders in windows (/users/account_name/ etc etc), which i can't see.

---

### Post by ago on 2008-04-26
You cannot see any file at all or only certain files?

Do such files have special chars in the name or directory maybe?

---

