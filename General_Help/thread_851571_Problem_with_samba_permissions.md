---
title: "Problem with samba permissions"
date: 2008-07-06
forum: General Help
---

### Post by Brando569 on 2008-07-06
i have (advanced) samba sharing set up and everything works fine as long as i own the folder that i am sharing. i am trying to share out all of the stuff that i have in my /media directory and the folders that i own are accessible but the folders that are owned by root i cant access. i tried changing the owner and group on the file itself, that didnt work, then i tried to change the uid in fstab, that didnt work either, then i tried adding "users" to the mount options but that didnt work either. 

how can i set up samba so that you only have to authenticate yourself once per session and how can i grant access for those root owned folders to the authenticated user?

---

