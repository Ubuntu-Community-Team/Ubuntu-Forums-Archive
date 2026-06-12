---
title: "Changed Service, now no network"
date: 2008-04-10
forum: General Help
---

### Post by personjerry on 2008-04-10
I use gutsy ubuntu (7.10). I went into (System->Adminstration->Services) and modified some services. After this, when I try to modify my services it states "You do not have permission to open this" even if I sudo it. Also, my network will not work anymore (but under windows it works fine; i dual-boot). I think that the DBUS option is one I changed which may have caused all this, due to the fact that upon logging in, there will be a message saying "HAL failed to initialize", thus also linking it with the HAL daemon. Is there some configuration file I can modify to solve this?

---

### Post by personjerry on 2008-04-16
bump...
this is still unsolved...

---

### Post by lederman on 2008-04-19
The same thing happened to me yesterday.  I have tried upgrading to 7.10 and re-installing hal but I still have the same problem.

My network connection still works, but I can no longer modify it - same permission issue as services.

-Matt

---

### Post by lederman on 2008-04-21
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=289654](http://ubuntuforums.org/showthread.php?t=289654) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				A smarter guy than me found this:

1) Run the following command at the terminal:-

Code:

 sudo /etc/init.d/dbus start
2) Then run services-admin and enable the System Communication Bus
(dbus).

[http://ubuntuforums.org/showthread.php?t=289654](http://ubuntuforums.org/showthread.php?t=289654)

---

