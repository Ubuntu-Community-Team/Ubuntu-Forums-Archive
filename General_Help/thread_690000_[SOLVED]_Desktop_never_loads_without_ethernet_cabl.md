---
title: "[SOLVED] Desktop never loads without ethernet cable pluged in."
date: 2008-02-07
forum: General Help
---

### Post by dante00001 on 2008-02-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/189488](https://bugs.launchpad.net/ubuntu/+bug/189488) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,
      I have a Dell M1210 laptop running 7.10. When I turn the laptop on with the Ethernet cable plugged in I can log in and the desktop takes about 10 seconds to load. When I turn it on without the Ethernet cable plugged in I can enter my user name and password but the GNOME desktop never loads. I get the same problem if I turn it on with the wireless switch in the ON position. I have tried creating a fresh user account and when logging into that account the desktop will sometimes load after 3-5 minutes. Being a laptop this can be very annoying. Any help with this would be greatly appreciated. Please feel free to request more information if needed.

                Dante,

---

### Post by kesman on 2008-02-07
Maybe ask here before posting a bug report :F
Seems like dhcp's timeout is way too long to me, no idea how to fix it though...

---

### Post by dante00001 on 2008-02-07
Replacing Network-manager, with  WiCD from here [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/") seems to resolve the issue. However this is just a work around and I think there is a bug that needs to be fixed in the Network-manager package.

                   Dante,

---

