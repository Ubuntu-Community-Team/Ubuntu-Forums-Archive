---
title: "fstab for different users with different permissions"
date: 2016-08-10
forum: General Help
---

### Post by NotQuiteSU on 2016-08-10
How do I go about creating access to the same share, but different permissions for different users? This is what my current fstab looks like

```

# Samba
//192.168.10.134/media /media/files/ cifs credentials=/root/.creds,uid=1000,gid=120,iocharset=utf8,file_mode=0777,dir_mode=0777


```

---

