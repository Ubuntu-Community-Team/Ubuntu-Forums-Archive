---
title: "[SOLVED] thunderbird 2 official mozilla build offlineMenuItem"
date: 2007-04-22
forum: General Help
---

### Post by nanotube on 2007-04-22
So, i have just installed the official mozilla build of thunderbird 2 (on top of a previous install of tbird 1.5, also official mozilla build), and everything works, but there's a strange extra panel on the bottom that seems to be displaying some kind of error.

The text reads:

```
    <menu id="offlineMenuItem" insertafter="trashMenuSeparator" label="&offlineMenu.label;" accesskey="&offlineMenu.accesskey;">
----^
```

screenshot is attached.
anyone have any ideas what this could mean and how to get rid of it?

---

### Post by nanotube on 2007-04-22
ok, problem resolved after some more googling.

removing the file /opt/thunderbird/chrome/offline.manifest has solved the issue.

i found this solution on here:
[http://groups.google.com.ar/group/mozilla.support.thunderbird/browse_thread/thread/8c2e2998f248053a/094a7a671bd9ba36?lnk=gst&q=offlinemenuitem&rnum=1#094a7a671bd9ba36](http://groups.google.com.ar/group/mozilla.support.thunderbird/browse_thread/thread/8c2e2998f248053a/094a7a671bd9ba36?lnk=gst&q=offlinemenuitem&rnum=1#094a7a671bd9ba36)

note: if you installed thunderbird somewhere other than /opt/thunderbird, then obviously your offline.manifest will be somewhere else. :)

---

