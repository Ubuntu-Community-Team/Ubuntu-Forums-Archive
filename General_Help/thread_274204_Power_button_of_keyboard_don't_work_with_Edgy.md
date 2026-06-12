---
title: "Power button of keyboard don't work with Edgy"
date: 2006-10-09
forum: General Help
---

### Post by Amnon82 on 2006-10-09
Hi. I used Dapper for a while. Now I updated to the newest beta. I've a little problem now. My power button don't work anymore. What did I wrong?

I did a search my self:

It is a bug of [gnome-power-manager ](https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/57872)

It's all a debian patch:

```
debian/patches/56-disable-session-save-on-shutdown.patch

@@ -865,9 +865,11 @@
        } else if (strcmp (action, ACTION_INTERACTIVE) == 0) {
                manager_explain_reason (manager, GPM_GRAPH_EVENT_NOTIFICATION,
                                        _("GNOME interactive logout"), reason);
+ /* This confuses too many people, so we commented it out
                gnome_client_request_save (gnome_master_client (),
                                           GNOME_SAVE_GLOBAL,
                                           TRUE, GNOME_INTERACT_ANY, FALSE, TRUE);
+ */
```

which disables the logout screen.

Here is a workaround:

Start the GUI of gpm and choose something at "When power button is pressed" but NOT "Ask Me".

Hope it will be fixed in a new release of gpm. The actual version with this bug: 2.16.1-0ubuntu1

Here is a [proposed fix (2.16.1-0ubuntu2)](http://librarian.launchpad.net/4713570/gpm.tar.gz) - seems to work.

---

