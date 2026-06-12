---
title: "Ubuntu &quot;crashing&quot; but not telling me why"
date: 2017-11-23
forum: General Help
---

### Post by Lloydb39 on 2017-11-23
I have a homebuilt AMD 64 bit machine running Ubuntu 16.04. Has worked well until recently when I began getting a popup window message about a "system failure" that it asked me to report. No crash, or Blue Screen of Death like Windows. Really no noticeable effect at all but annoying. Seems to me it usually happens while I'm using Chrome. Can anybody tell me how to trace it and fix it?

---

### Post by yetimon_64 on 2017-11-23
In the terminal you could list the contents of /var/crash with the command "ls /var/crash" (without the quotation marks). Any application causing a "system failure" warning should leave a file at that location, usually with the application name included in the file name or within the file content.

Alternatively you could just navigate to /var/crash with the file manager and inspect the files there. That should give you a better idea which applications are failing causing the "system failure" warning.

---

### Post by Lloydb39 on 2017-11-23
ls returned this: _usr_bin_appstreamcli.0.crash   _usr_bin_appstreamcli.0.uploaded_usr_bin_appstreamcli.0.upload
But I don't know what it means...

---

