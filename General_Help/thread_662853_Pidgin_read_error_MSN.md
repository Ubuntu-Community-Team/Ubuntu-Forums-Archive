---
title: "Pidgin read error MSN"
date: 2008-01-09
forum: General Help
---

### Post by Maikelv on 2008-01-09
Today , suddenly after I added a new contact. Pidgin crashed & it won't log me in anymore.

It says "read error". I tried turning on http , and reïnstalling pidgin, no gain.

Strange thing is, it has been working for a week without any problems.

---

### Post by ajgreeny on 2008-01-09
Try renaming the ~/.purple folder to ~/.purple.bak and open pidgin again to see if it will at least open.  If it will open the blist.xml file from your backup .purple.bak folder in gedit and remove the new buddy you added.  Now restore the backup folder to .purple again and see if all works; it should unless something else went wrong other than the new buddy.

---

