---
title: "Auto-Samba?"
date: 2008-04-04
forum: General Help
---

### Post by Roasted on 2008-04-04
I have Samba set up with 3 computers in the house. They log in with their username, password, etc... and they can read/write to their shared folder. It's basically a remote way to drop items to my computer so they are backed up.

At work, we use an Exchange Server, and everything is on real-time synchronizing. When I delete a folder on my machine as a node user, it is deleted off of the server in 5 seconds.

Is there any way I can set up some kind of auto-syncing thing like that, except with my desktop pc/samba?

---

### Post by ryanhaigh on 2008-04-04
scripting rsync may help but might not be the best solution for this situation.

---

### Post by Roasted on 2008-04-04
How can I script rsync when the XP users on the other 3 machines need to log in to my server first?

---

### Post by ryanhaigh on 2008-04-04
Maybe you can parse smbstatus? although I would think that this needs to be initiated client side for this sort of setup. Im pretty sure rsync is cross platform and although I have no experience scripting anything on windows I imagine it would not be to difficult to run a command every few minutes. It may also be easier if you have the shares mounted as a network drive under windows. If you do that you could use any sync package (Synctoy is a windows powertoy that may be useful here) to keep the share up to date.

---

