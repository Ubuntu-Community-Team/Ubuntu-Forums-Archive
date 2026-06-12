---
title: "Preparing for SAMBA in an XP environment"
date: 2007-07-01
forum: General Help
---

### Post by jconnett on 2007-07-01
I am using a workgroup network setup right now with Samba doing a GREAT job managing file and printer services, but would like to convert to a domain set up in the near future.  I know what I need to do in the smb.conf file to move to a domain...that's not a problem at all.

My question revolves around "pre-setup".  I already have accounts for all the users under Samba, but I know I need to add the machine accounts.  Can these be added, yet still run in a workgroup setup without freaking out Samba?  I suspect since the machine accounts are hidden, that Samba doesn't really care about them until I add the code to transition Samba from a workgroup to a domain.

Does anyone see an issue with this?

--Jim

PS...and a Windows question...when I add each XP system to the new domain on each client, should I expect all user settings to be carried over, too?  (i.e, desktop shortcuts, Outlook 2003 mail accounts, etc.)  I know...a WINDOWS question...ewh!

---

