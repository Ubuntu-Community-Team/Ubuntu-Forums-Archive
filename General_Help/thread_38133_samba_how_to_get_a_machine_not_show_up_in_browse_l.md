---
title: "samba: how to get a machine not show up in browse list?"
date: 2005-05-30
forum: General Help
---

### Post by dierre on 2005-05-30
Hello!

I have a machine running samba in order to share some directories, but I'd like it not to show up in  the network browse list: i.e. only those which already now the netbios name should be allowed to access it.

I am sure that it *must* be there, but I can't find it in the samba documentation... 
I tried both browse list = no and disable netbios = yes  but they don't work.

Thanks in advance!

Have a nice day,

Francesco

---

### Post by grim42 on 2005-05-30
I'm fairly sure you can do this. I've seen it somewhere.

Try "browsable = no" or "browseable = no" in global of smb.conf.

EDIT: no actually I think that only applies to shares. I'll keep looking.

I read somewhere that if you kill the nmbd daemon (and leave the smbd daemon running) it will achieve the desired effect.

---

