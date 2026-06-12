---
title: "Sync Sharepoint to Ubuntu"
date: 2016-09-19
forum: General Help
---

### Post by shivahnshankar on 2016-09-19
I have 20 Ubuntu 16.04.1 desktops that need to sync Sharepoint teamsite files. While I understand that there is no support for Sharepoint site sync in Ubuntu, i was wondering if there is a workaround, using a Windows 10 desktop. Here's what i was planning :
[LIST=1]
[*]Using Groove client on Windows 10, sync the Sharepoint site
[*]Share the Sharepoint folder via SMB
[*]Each Ubuntu desktop would then access the SMB share periodically (cron, ansible etc) and then sync the files locally
[/LIST]
Please let me know if this has worked for you or comments on how i can do this better.
Thanks

---

### Post by shivahnshankar on 2016-09-19
One limitation of this of course would be that per user access is not possible but the files are edited by a few people on Windows and the latest version needs to be used on all Ubuntu.

---

