---
title: "mount ISO and share in samba with fuseiso"
date: 2008-05-16
forum: General Help
---

### Post by jdroflet on 2008-05-16
With mythbuntu also as my smb NAS I wish to mount an ISO so it is available to the WINXP systems.

using fuseiso I can mount the ISO in a directory under the smb share but the directory disappears from the windows folder view, and returns when fusermount -u is run. When fuseiso is run the user changes to root

steps so far:
From thread [http://ubuntuforums.org/showthread.php?t=435711&highlight=fuseiso](http://ubuntuforums.org/showthread.php?t=435711&highlight=fuseiso)

sudo chmod u+s `which fuseiso`
sudo usermod -Gfuse `whoami`

1 - empty directory appears in windows shares
torrent@nas:~$ ls -l share
drwxrws--- 2 torrent  torrent    4096 2008-05-15 17:17 CD

2 - mount the iso, owner changes and folder is gone from windows side.
torrent@nas:~$ fuseiso  share/completed/file.iso share/CD/
torrent@nas:~$ ls -l share
dr-xr-xr-x 1 root     root       2048 2007-02-21 10:51 CD

3 - Files are accessable by the local user but not via smb:
torrent@nas:~$ ls -l share/CD/
dr-xr-xr-x 1 root root    2048 2007-02-21 08:39 Documents

4 - fusermount -u /home/torrent/share/CD and the empty folder is visible as a samba share again.

config:
Mythbuntu 8.04 RC
fuseiso Version: 20070708
smbd Version 3.0.28a
smb.conf details (this share is in addidtion to  the standard mythtv shares)
security = user

[pub]
path = /home/torrent/share
available = yes
browsable = yes
public = yes
writable = yes
force user = torrent
force group = torrent
create mask = 0660
directory mask = 0770

Thanks, John.

---

