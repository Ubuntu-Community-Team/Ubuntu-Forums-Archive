---
title: "Connect to Server"
date: 2005-10-31
forum: General Help
---

### Post by sparty2809 on 2005-10-31
Ok, I go under the menu Places and then Connect to Server.  I connect fine, but it only lets root modify the files.  How can I mount this as a user?  Or do I have to use the command line to do it?

I can get it to mount like this in the /etc/fstab file

//server/share	/mnt/share  smbfs   credentials=/etc/samba/userinfo, dmask=777, fmask=777   0   0

but this mounts it everytime.  

I want to use Connect to Server option if possible.  Thanks.:confused:

---

### Post by sparty2809 on 2006-03-21
How can I changes the permissions?  When I use Connect to Server, it has root as the owner.  How can I make other users the owner or change the group?

---

