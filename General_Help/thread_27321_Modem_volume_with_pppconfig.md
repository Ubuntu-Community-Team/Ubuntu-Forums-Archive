---
title: "Modem volume with pppconfig?"
date: 2005-04-15
forum: General Help
---

### Post by Mytos on 2005-04-15
Isn't there some line or something i can add to turn off the dial up modem sound when using pppconfig?


 :???:

---

### Post by dataw0lf on 2005-04-15
open up /etc/chatscripts/provider. Locate the line marked OK-AT-OK. Change ATDT to
ATL3DT.  Save.  Exit.
Or you could've googled and found : [http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)
which explains it.  Please, guys, google, check the wiki, and search the forums.  I don't mind helping out, but it saves us both time if you do this before posting a question.

---

