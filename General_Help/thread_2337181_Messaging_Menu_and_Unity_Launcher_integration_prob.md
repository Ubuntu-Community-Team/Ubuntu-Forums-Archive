---
title: "Messaging Menu and Unity Launcher integration problem"
date: 2016-09-15
forum: General Help
---

### Post by rsteinmetz70112 on 2016-09-15
The Messaging Menu and Unity Launcher integration  version 1.3.1 by Mike Conley in Ubuntu 12.04 Thunderbird 45.2.0 seems to cause a problem with certain malformed/malicious emails.

I have Ubuntu machines I use as back up archives for my pop3 accounts my primary work computers are Windows. I hold all of my mail on the mail server for a time and periodically download a backup copy to 2 machines at a remote location. There are often a lot of messages and it can take some time.

When I last downloaded to my backups I discovered the download was stopping at the same place and hanging Thunderbird. I had to kill the process and restart. Once this had happened, reopening the Inbox caused the same problem. renaming the old Inbox cleared the issue but downloading again recreated it. Working in safe mode allowed a normal download. I tried to figure out which extension/plugin was causing the problem and eventually isolated this extension.

I found instructions for removing the extension, but it seems It would just get reinstalled with the next update so I think I'm better off leaving it disabled, which should hold through upgrades, what do you think?

---

### Post by ian-weisser on 2016-09-15
Well done!
Please file a bug report.

---

