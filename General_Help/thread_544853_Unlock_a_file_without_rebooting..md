---
title: "Unlock a file without rebooting."
date: 2007-09-06
forum: General Help
---

### Post by lgrce on 2007-09-06
I have a file server running Ubuntu and server files off of it for several Windows clients using Samba. It works great except I have had a Windows client crash (surprise surprise) and the file that was open by the Windows machine is still locked and can't be open, copied, moved etc by any of the other machines. Is there a way to unlock the file so people can use it again with out rebooting the Ubuntu file server?

Thanks

---

### Post by yabbadabbadont on 2007-09-06
Try restarting samba.  I don't use it myself, so I'm not sure what the name of the script is in /etc/init.d that you need to run (with a parameter of "restart").  :(

---

