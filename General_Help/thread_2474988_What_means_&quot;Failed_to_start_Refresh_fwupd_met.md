---
title: "What means &quot;Failed to start Refresh fwupd metadata and update motd&quot; ?"
date: 2022-05-13
forum: General Help
---

### Post by aug7744 on 2022-05-13
Hello.
Thanks for read my topic.
The error below only happen one time when the computer is power on. If pressing reset in Ubuntu second start the error not happen.

"Failed to start Refresh fwupd metadata and update motd"

What means it ?

---

### Post by tea for one on 2022-05-13
[COLOR="#0000FF"]F[/COLOR]irm[COLOR="#0000FF"]w[/COLOR]are [COLOR="#0000FF"]Upd[/COLOR]ate

[COLOR="#0000FF"]M[/COLOR]essage [COLOR="#0000FF"]o[/COLOR]f [COLOR="#0000FF"]t[/COLOR]he [COLOR="#0000FF"]d[/COLOR]ay

---

### Post by aug7744 on 2022-05-30
"Firmware update" only in OS modules ?
Have any problem loading the OS when show that message ""Failed to start Refresh fwupd metadata and update motd" ?

Thanks for your reply.

---

### Post by #&amp;thj^% on 2022-05-30
Try this please:
```
/usr/bin/fwupdmgr refresh --no-metadata-check
```
any better?

---

### Post by michael351 on 2022-09-09
I had the same problem and tried your code suggestion (/usr/bin/fwupdmgr refresh --no-metadata-check.

No luck:

WARNING: UEFI capsule updates not available or enabled in firmware setup
  See [https://github.com/fwupd/fwupd/wiki/PluginFlag:capsules-unsupported](https://github.com/fwupd/fwupd/wiki/PluginFlag:capsules-unsupported) for more information.
Firmware metadata last refresh: 5 hours ago. Use --force to refresh again.

---

