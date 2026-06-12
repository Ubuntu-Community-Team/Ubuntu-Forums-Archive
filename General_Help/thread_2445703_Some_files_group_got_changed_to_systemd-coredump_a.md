---
title: "Some files group got changed to systemd-coredump and now I cannot chage them"
date: 2020-06-18
forum: General Help
---

### Post by raccoonstrait on 2020-06-18
Hello everyone.
Xubuntu 20.04 running an rsync backup of one of my drives gave a bunch of errors on some files. In tracking down the error code, permissions was mentioned. I looked at the permissions and found that those files were user root and group root. I want them to be user nobody and group nogroup (both of which exist).

Somehow I managed to get the user changed to nobody, but the group name now comes up systemd-coredump. Try as I might, I cannot seem to change this:

```

[FONT=monospace][COLOR=#000000]sudo chown -R nobody:nogroup /mnt/mydrivename

[/COLOR][/FONT][FONT=monospace][COLOR=#000000]sudo chgrp -R nogroup /mnt/[/COLOR][/FONT][COLOR=#000000][FONT=monospace]mydrivename/[/FONT][/COLOR][FONT=monospace][COLOR=#000000] 

[/COLOR][/FONT][FONT=monospace][COLOR=#000000]sudo chown -R -H --from=:systemd-coredump :nogroup /mnt/[/COLOR][/FONT][COLOR=#000000][FONT=monospace]mydrivename[/FONT][/COLOR][FONT=monospace][COLOR=#000000]/[/COLOR]
[/FONT][FONT=monospace]
[/FONT][FONT=monospace][COLOR=#000000]sudo chown -R nobody:nogroup /mnt/[/COLOR][/FONT][COLOR=#000000][FONT=monospace]mydrivename[/FONT][/COLOR][FONT=monospace][COLOR=#000000]/

[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]

Have all been tried with no joy.

Any suggestions?

RaccoonStrait   [/COLOR]
[/FONT]

---

### Post by oldfred on 2020-06-18
What format is partition?
If NTFS or any Windows type format, it does not support ownership & permissions. You set those only as the mount.

---

### Post by raccoonstrait on 2020-06-18
Thanks for the reply oldfred. It is in fact an NTFS USB drive attached as part of a NAS setup for media files used by Samba. Here is the relevant part of FSTAB:

```

LABEL=mydrivename01-BU /mnt/mydrivename01-BU auto nosuid,nodev,nofail,x-gvfs-show, 0 0


LABEL=mydrivename02-BU /mnt/mydrivename02-BU auto nosuid,nodev,nofail,x-gvfs-show, 0 0


/mnt/mydrivename01   /home/public/users/mydrivename01   ntfs    bind,credentials=/etc/samba/.sambacreds,gid=999,uid=65534,auto,nofail,noatime,nolock,intr,tcp,actimeo=1800  0  0


/mnt/mydrivename02   /home/public/users/mydrivename02   ntfs    bind,credentials=/etc/samba/.sambacreds,gid=999,uid=65534,auto,nofail,noatime,nolock,intr,tcp,actimeo=1800  0  0


LABEL=mydrivename02 /mnt/mydrivename02 auto gid=999,uid=65534,nodev,nofail,x-gvfs-show 0 0


LABEL=mydrivename01 /mnt/mydrivename01 auto gid=999,uid=65534,nodev,nofail,x-gvfs-show 0 0





```

While I have been using this FSTAB for quite a while now, with no issues until the problem with rsync showed up I just noticed that I have two entries for the non BU of the drives. Hmmm. Should I remove one of those entries for each duplicated drive, and if so, which one (I could just comment them out I suppose). Note that both of those drives actually appear in both of the locals they are mounted on. I need them in the public folder more than I need them in the mount folder, and I may have gotten here when I was trying to make NSF work (I gave up on that, Samba was easier on the LibreElec system where they mostly get used). Or am I creating permission changes with those 'conflicting' entries?

Another thought, would 'gid=nogroup,uid=nobody' work?


RaccoonStrait

---

### Post by raccoonstrait on 2020-06-18
OK,

So I changed the gid to 65534 which is group nogroup and rebooted. That worked, and the permissions now show nogroup correctly. It did not however solve the rsync error (5) issue. So I will mark this one solved and open a new thread for that specific issue.

Thanks

Raccoon Strait

---

