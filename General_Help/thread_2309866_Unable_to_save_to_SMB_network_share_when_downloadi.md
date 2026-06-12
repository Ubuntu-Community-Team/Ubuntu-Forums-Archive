---
title: "Unable to save to SMB network share when downloading torrents (Deluge/Transmission)"
date: 2016-01-14
forum: General Help
---

### Post by jsalisburyme.com on 2016-01-14
i'm running Ubuntu 15.10 and trying to download to an SMB network share using torrent clients.

I can browse/mount my SMB network share using Nautilus fine and copy/paste data to it, but when I select it in my torrent client, the torrents download for around 1 minute and then fail with the error message 'operation not supported /run/usr/1000/gvfs smb:share <share name>'

i've done a lot of searching around to no avail - has anyone else had this issue?

---

### Post by SeijiSensei on 2016-01-14
You should mount the share at boot from /etc/fstab: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

