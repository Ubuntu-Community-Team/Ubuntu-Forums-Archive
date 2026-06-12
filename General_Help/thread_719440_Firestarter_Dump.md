---
title: "Firestarter Dump"
date: 2008-03-09
forum: General Help
---

### Post by Salazar420 on 2008-03-09
For reasons unknown to me, firestarter randomly shuts down after random periods of time, and then I have to reinitialize it. This is happening to me when I have the gui enabled. I do not know if it is the typical "Segmented Fault (Core Dumped)" issue, but it seems to have similiar effect. I wonder, does anybody else have this problem? It happens even under clean installations of the OS (which, btw, is 7.10, in my case). Does anybody know if this is less likely via the daemon? And, if so, how might I check the active connections, hits from peers, etc., when the daemon is running? Is it possible? Any information would be greatly appreciated. If you guys need specs, test results, etc., for insight let me know.

---

### Post by julian67 on 2008-03-09
I've found firestarter gui crashes on Ubuntu and other distros too. But it's not important as long as the iptables rules are still in force. I have firestarter rules enforced at boot without the need for the gui. There's an excellent guide/howto for this [How-To: Firestarter on startup (better & safer way)]("http://ubuntuforums.org/showthread.php?t=542756") which will show you how to ensure the iptables rules are always enforced  at boot time and enforced gui or no gui.

---

### Post by Salazar420 on 2008-03-20
Right on. Will definitely check that out. Thanks for the reply.

---

