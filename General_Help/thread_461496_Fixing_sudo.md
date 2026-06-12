---
title: "Fixing sudo"
date: 2007-06-01
forum: General Help
---

### Post by Blazeix on 2007-06-01
Hi, I recently had to add my user account so a certain group, and by mistake ended up wiping out my group information. I used to be a member of these groups:
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
now I am only a member of one group: 'fuse'
The problem is, in order to fix it, I believe I have to be root. 'sudo' does not work (because of the messed up groups). My root account is disabled, since that is the default in Ubuntu. Whenever I try to use sudo, it does nothing and returns no output. Is there any way to fix it? I suppose I could boot a live cd and edit /etc/sudoers from the live cd, but is there anyway to do it from 'within' Linux? Thanks.

---

### Post by dreadlord_chris on 2007-06-01
Boot into Recovery Mode, then from the command line:
```

usermod --append --groups  adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,scanner,admin USERNAME

```

replace USERNAME with your login name
make sure when you enter this command that each group is seperated **ONLY** by a comma - no spaces...

reboot - you should be good to go now....

---

### Post by aysiu on 2007-06-01
Alternatively, boot into recovery mode and ```
adduser *username* admin
reboot
``` Then Alt-F2 ```
gksudo users-admin
``` and then just click-add all the rest of the groups or choose your profile as being administrator.

---

