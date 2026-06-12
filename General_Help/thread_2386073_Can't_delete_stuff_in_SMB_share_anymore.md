---
title: "Can't delete stuff in SMB share anymore"
date: 2018-02-28
forum: General Help
---

### Post by Evil Wayz on 2018-02-28
I have a small raspi acting as a media center.  The os, Libreelec recently changed the samba policy from smb1 to smb2.  So I changed my smb.conf file to accept nothing below smb2 as well.  Now I can add the share with no password, I can move files around within the shares, I can create new files.  I can even rename stuff.  But nothing I delete stays deleted.  For instance, if I go into the downloads folder and delete the folder download1, it will appear to be deleted, if i go back to root and then back into the downloads folder , the download1 folder will be back.  But, if i move it from say one smb share to another, or to the computer I am on,. it works. 

Weirdest problem ever.  My comp is running 17.10, xubuntu desktop.

---

