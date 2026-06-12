---
title: "WINS Problem"
date: 2005-10-17
forum: General Help
---

### Post by screamingFit on 2005-10-17
This was not a problem in RC1.  

Seems that the setting in Sharing Settings in Shared Folders for the WINS resolution server doesn't hold a setting.  You can enter the info and OK out and go back in and there's nothing there.  And it's not "hidden" as even after entering the information, WINS resolution still doesn't work.

I'm guessing the /etc/samba/smb.conf needs to edited by hand to get this working.  I think I found the area to do this in the conf file: under global settings, WINS Server (line 38 in the default .conf file).  I've entered the IP there of the WINS server and it still doesn't work.

Anyone  have any ideas?  I'm really hating editing the .hosts file by hand and adding servers!

---

