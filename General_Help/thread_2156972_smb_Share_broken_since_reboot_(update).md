---
title: "smb Share broken since reboot (update)"
date: 2013-06-23
forum: General Help
---

### Post by jamesisin on 2013-06-23
I have a server with a share.  I have several machines which auto-mount that share.  I recently conceded to reboot that machine.

All of the Ubuntu machines (10.04, 12.04, 13.04, and maybe a 12.10) on my network are no longer able to mount that share using this mount command (fstab):

```
//server/music    /media/music        cifs    guest,iocharset=utf8 0 0
```

I am also unable to mount it manually:

```
$ sudo mount -t cifs --verbose server/music /media/music -o guest

mount.cifs kernel mount options: unc=//server\music,user=,ver=1,rw,guest,ip=****
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

I have also tried using sec=none which results in the same error (and sec=ntlm and nounix).  (I get the same error if I use smbfs instead.)

Here is the smbconf info for the above share:

```
[music]
   comment =
   path = /srv/samba/music
;   writeable = no
   browseable = yes
   guest ok = yes
   read only = guest
;   valid users = [me]
   write list = [me]
```

There is another (several actually) share on that same server:

```
[words]
   comment =
   path = /srv/samba/words
   writeable = no
   browseable = yes
   guest ok = yes
   read only = yes
   valid users = [me]
   write list = [me]
```

This share is also not working since the reboot.  However, it gives slightly different behavior.

```
$ sudo mount -t cifs --verbose //server/words /media/words -o guest

mount.cifs kernel mount options: unc=//server\words,user=,ver=1,rw,guest,ip=****
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Regardless, something has changed with some update somewhere (on that server).  Can anyone help me sort this out?  I haven't been having much luck with what I've found out there.

By the way, my one Windows machine has no trouble accessing this share and if I try to mount as my own user (and supply credentials) I am able to mount in Ubuntu.  Something appears to have changed on the server directly relating to samba shares and guest access.

---

### Post by jamesisin on 2013-06-23
Fork!

Ok, it was (somewhere) a permissions issue.  I saw that a recent addition within the share was permitted only to my user.  The share folder itself seemed permitted correctly, however.  Nonetheless I ran a permissions update:

```
sudo chmod -R 755 /media/mountpoint/share/
```

... and we're back in business.

(What a useless error code.)

---

