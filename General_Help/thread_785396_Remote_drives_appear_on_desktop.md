---
title: "Remote drives appear on desktop"
date: 2008-05-07
forum: General Help
---

### Post by siersmak on 2008-05-07
Hi,

I've just installed Hardy, and I've noticed a behavior that I haven't seen before, and that I don't desire.  If I browse through Places -> Network -> A Samba Server -> A Samba Share, then an icon for the Samba Share gets appears on the desktop, and it won't go away unless I right click and select 'Unmount Volume'.  How can I turn this functionality off, so that it behaves like previous versions of Ubuntu?

Thanks,
Ken

---

### Post by jimv on 2008-05-07
Do you hard drive icons appear on the desktop too?

---

### Post by siersmak on 2008-05-07
Nope.

---

### Post by benste on 2008-05-07
I thought this is the normal way - isn't it? - all my ftp connections are listed on the desktop when they're active - but this is since 7.04 for me

---

### Post by siersmak on 2008-05-07
No, this did not occur in 7.10 or 7.04.  I'm talking about a SMB share, not an ftp server.

---

### Post by benste on 2008-05-07
I'm sorry though this one should have the same behaviour like ftp

---

### Post by jimv on 2008-05-07
if you go into gconf-editor, is this option checked?

/apps/nautilus/desktop/volumes_visible

---

### Post by drs305 on 2008-05-07
Reference the previous post, in terminal you can run:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'	
```

to turn off the gconf-editor 'volumes visible' check mark. You can restore the volumes by changing the value to 'true'

---

### Post by siersmak on 2008-05-07
Thanks to drs305 and jimv, that will do.  I had previously looked in the 'desktop' section of the gconf-editor, but didn't think to look in the 'apps/nautilus' section.  

Unfortunately it doesn't allow ftp mounts to be shown on the desktop, so it doesn't exactly replicate the behavior of previous versions of ubuntu/gnome/nautilus, but that's okay with me.

---

