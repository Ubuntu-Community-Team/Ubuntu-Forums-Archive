---
title: "Domain Users is new file's group not the one set on the top level folder"
date: 2014-10-31
forum: General Help
---

### Post by wood0966 on 2014-10-31
So I have set up Ubuntu Server 14.04 and joined it to our AD domain.  I am using Samba to create file shares for people and I have changed the owner of the top level share folder for the user /shares/username/ and when I create a new file in this folder from Windows the group of the file is domain users instead of the one set on the share folder. How can I make it so this group on all new files is set to staff instead of domain users.  I am assuming it is grabbing the primary group from the domain and using that for the group on the file. 

I did chown -R user /shares/user
and chgrp -R Staff /shares/user
I have also chmod -R 4770 /shares/user
and tried chmod -R 6770 /shares/user
as well as looking at the new file I create before I did any of the above chmod commands


Help! Thanks!

Edit --- Nevermind I figured it out. I added force group = staff in the smb.conf and now everything is working peachy.

---

