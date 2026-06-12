---
title: "chgrp command destroyed group ownerships - how do I get it back?"
date: 2008-01-26
forum: General Help
---

### Post by akerman on 2008-01-26
Hi,
I managed to type the following command when trying to follow instructions in "chgrp --help"

sudo chgrp -hR www-data /*

All I wanted to accomplish was a way to change multiple sublibraries/files groups.

I tried from within Nautilus (w gksudo of course) and I tried with:
"sudo find www/ -type d -exec chmod a+rx {} \;"   which went just fine a couple of days ago...

Then I tried this from console and voilá - ALL files from top down changed group to *www-data*.
Anyone seeing the oncoming catastrophy? :)

I managed to stay in the system, editing *etc/groups* so I could retype the command with *root* instead, from the same position "var/www/sudo chgrp -hR root /*"
Hoping of course this would set everything straight... well kind of.

Now the system is running (haven't dared to restart) but I can't seem to access deeper functions in the System folder like User Admin, Time and so forth.

What do I do? Am I toatally toast, set for a reinstallation or...? Grateful for any input other than "thou shall not missuse thy sudo". 
Thanx  (still happy but crying on the inside...)


2008-01-27 Managed to get SUDO rights back, but system is messed up since all group ownerships belongs to root. Have tried to find some kind of list of system and/or application ownership on the net, but without success. Maybe there are lists, but I think that is a bit strange since the ownership of each file/system/applic is such an essential part of the setup/functionality - shouldn't such a list be included in each OS/applic - package?

Anyhow - System is being reinstalled from scratch. Lesson learnt...sigh...

---

