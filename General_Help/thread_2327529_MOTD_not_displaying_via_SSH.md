---
title: "MOTD not displaying via SSH"
date: 2016-06-11
forum: General Help
---

### Post by dmorand on 2016-06-11
I'm trying to get my MOTD to display when I SSH into my Ubuntu server (16.04) but I'm having issues.

**/etc/ssh/sshd_config**
```

...
PrintMotd no
UsePAM yes
...

```

**/etc/pam.d/sshd**
```
session    optional     pam_motd.so  motd=/run/motd.dynamic
session    optional     pam_motd.so
```

I've verified that I can see the MOTD when I run the following:
```
sudo run-parts /etc/update-motd.d/
```

I've also verified that I see the MOTD when I review the **/run/motd.dynamic**.  

Any help would be appreciated!

---

