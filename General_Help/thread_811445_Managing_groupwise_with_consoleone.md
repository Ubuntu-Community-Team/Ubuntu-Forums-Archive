---
title: "Managing groupwise with consoleone"
date: 2008-05-29
forum: General Help
---

### Post by sjippy on 2008-05-29
I can't get consoleone to work with groupwise snapins.

After adding the groupwise snap-ins to /usr/ConsoleOne/snapins/GroupWise starting c1 will result in a non working c1 and the error: java.lang.exceptionininitializererror.

Did some searching but cant find anything on this subject it all revers to server related java problems and windows vista.
It looks to me that somehow the snapins will not work on a Linux platform.

I thought java based program's where platform independent so I'm somewhat confused at the moment.

Some insight would be grate.
Thanks
Stefan

---

### Post by sjippy on 2008-05-29
Ok found it out my self:
I downloaded gw701lnxe
Unpacked the novell-groupwise-admin-7.0.1-20060613.i386.rpm
Ran alien -i on that
Altered the /usr/ConsoleOne/bin/consoleone.sh by removing the:
LD_LIBRARY_PATH="/usr/lib:/opt/novell/lib:/opt/novell/eDirectory/lib:$LD_LIBRARY_PATH"
Replacing it with: LD_LIBRARY_PATH="/usr/lib:/usr/ConsoleOne/bin:$LD_LIBRARY_PATH"

Hope i helped someone.
stefan

---

### Post by tixetsal on 2009-02-13
Any suggestions on getting the Zenworks snap-ins to work with c1?  Thnx!

---

