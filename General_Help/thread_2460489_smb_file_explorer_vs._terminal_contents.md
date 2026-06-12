---
title: "smb file explorer vs. terminal contents"
date: 2021-04-11
forum: General Help
---

### Post by sniper8752 on 2021-04-11
I am using Dolphin file explorer to view files on my smb/cifs share on my linux server.  I view them in my directory on the command line, and the file is there.  When I view it in the file explorer, it does not show up.  I make a test directory via the command line, and it shows up in the file explorer.  What would cause new files to show up via command line listing, but not via the dolphin file explorer?  Some kind of permissions issue?  I am using syncthing to sync files, and I was logged in as root to create the directory as a test.

---

### Post by TheFu on 2021-04-11
permissions?

---

### Post by HermanAB on 2021-04-12
Dolphin runs as the logged in user, while you mentioned you created the new directory as root.

---

