---
title: "can't login after installing samba(?)"
date: 2013-02-10
forum: General Help
---

### Post by Lifman on 2013-02-10
hi,
i was trying to share folders between my ubuntu 12.10 and a winxp. tried to install samba and got an error (package name was samba4, btw), and a suggestion to remove a certain file (which i shouldn't have,but did...). during the same session i also changed my workgroup from WORKGROUP to HOME.

after restarting my ubuntu i can't login to any user account! :-(

when entering the correctp password i get "invalid password" instantly. (when i enter wrong passwords ubuntu takes some time to think about it and then rejects them.)

i tried doing passwd username in recovery mode, but this line does nothing. i tried passwd -d username and then switching to username - but ubuntu still asks for the current password (which i don't know). anyway, i think i'm looking in the wrong direction and this isn't a passwords problem but something else (workgroup??).

any suggestions, please?

---

### Post by Lifman on 2013-02-10
i kinda solved it:
the file i removed was /etc/samba/smb.conf.
luckily, i had a backup copy at /etc/samba/smb.conf~ (gedit autosave, i guess). i replaced the new file with the old, and now i can login.
only question left is, why did the installation of samba4 suggest that i delete this file (and allow another program to "generate" a new one)?

---

