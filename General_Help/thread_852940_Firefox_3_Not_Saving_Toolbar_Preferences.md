---
title: "Firefox 3 Not Saving Toolbar Preferences"
date: 2008-07-08
forum: General Help
---

### Post by war59312 on 2008-07-08
Hey,

Firefox 3 (Ubuntu 8.04) is refusing to save its tool-bar preferences.

Yet it remembers just fine if I wish to show icons or text or use small icons. But it refuses to remember which icons to show on the standard tool-bar.

Very strange, any thoughts?

Thanks,

Will

Update: Damn addon: [http://trac.arantius.com/ticket/174](http://trac.arantius.com/ticket/174)

---

### Post by wynneth on 2009-01-07
months later, mine is doing this as well.... wonder if anyone ever found an answer

---

### Post by polytropos on 2009-01-21
Pretty sure I have the same problem, but I've got other related problems as well.  When I go to View>Toolbars>Customize, all that I have available to add are buttons that come initially with Firefox; so, for example, even though I've added DownloadHelper, I can't add a DownloadHelper button to the toolbar.  When I do add, e.g., the bookmark button, it will stay on the toolbar throughout the session, but it will not be there upon opening a new session.

This is only mildly irritating, but it's still that: mildly irritating.  Any help?

---

### Post by wynneth on 2009-01-22
I believe I have found the solution. I googled some more and found this::KS

[http://tmp.garyr.net/forum/viewtopic.php?p=](http://tmp.garyr.net/forum/viewtopic.php?p=)

I'm using Tab Mix Plus 0.3.7.3 and as soon as I disabled it, the problem was solved. I'll do some testing and see if it's a particular option or simply the extension in it's entirety.

---

### Post by wynneth on 2009-01-22
After further testing I solved the problem without disabling Tab Mix Plus! I went in and changed the options, now I can't tell you which option specifically did it, but here is what I changed:

Do not display new tab button, do not display all tabs button, do not display in tools menu.

I'm betting it was one of those tab buttons that's doing it. Anyway, problem SOLVED

---

### Post by wynneth on 2009-01-22
It seems my answer may have been premature. It seems afterall that the only way to fully solve the issue is to disable TMP entirely. :(

---

### Post by wynneth on 2009-01-22
Answered prematurely... further testing reveals the only way so far to fully solve is to disable TMP. After several restarts the bug returned with TMP enabled and just having changed options. :(

---

### Post by polytropos on 2009-01-23
Wynneth's fix works--thanks for figuring that out.  I'm not willing to part with Tab Mix Plus, however, so I'll be living with this bug until there is another fix.

---

### Post by clwoodard on 2009-04-07
Disable the Ubuntu extensions to Firefox and your other mods will work fine. It overrides stuff it shouldn't, in the incorrect order.

---

