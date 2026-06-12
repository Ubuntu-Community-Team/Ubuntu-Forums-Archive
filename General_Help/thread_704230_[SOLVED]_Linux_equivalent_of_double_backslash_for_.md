---
title: "[SOLVED] Linux equivalent of double backslash for viewing other computers?"
date: 2008-02-22
forum: General Help
---

### Post by svivian on 2008-02-22
In Windows explorer you can do **\\name** in explorer to connect to another computer on the network...but this isn't working in Ubuntu (Nautilus). Is there a Linux/Ubuntu equivalent?

---

### Post by SpaceTeddy on 2008-02-22
in nautlis (your filebrowser) use smb:// for windows shares, ssh:// for ssh/sftp connection ftp:// for ftp dav:// for davfs and davs:// for secure dav

---

### Post by svivian on 2008-02-22
yep, smb:// did the trick, thanks!

---

