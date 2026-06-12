---
title: "Problem with missing characters and Samba"
date: 2007-07-03
forum: General Help
---

### Post by MCMcButtah on 2007-07-03
I download allot of files using Amule. Sometimes it seems the downloaded files are missing a character or something as in the file name there will be what looks like a box. I am assuming this is due to me not having a character set that is needed? The files work fine on the local machine, but shared over the network they are broken. For example if I have a file called funnyvi[]eo.avi when it is shared the remote machine sees it as funnyvi_eo.avi and it won't play. It will give me an error message that the file does not exist. If I rename the file and take the box out it plays fine. Is there any way for me to get the missing character set or to have samba work correctly when a character is missing?

Side question: When my files download they have the user as root. However Amule is running under the user 'candymountain', and not as a root account. The files need to have 'candymountain' permissions in order for the remote samba user to access the file or permission is denied. Is there anyway I can make Amule assign user level permissions to the download file? It is annoying that I have to remote desktop into my server just to set permissions to access my file.

Any insight is appreciated, thanks!

---

