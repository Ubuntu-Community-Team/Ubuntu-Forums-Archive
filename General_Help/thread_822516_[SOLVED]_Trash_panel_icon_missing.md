---
title: "[SOLVED] Trash panel icon missing"
date: 2008-06-08
forum: General Help
---

### Post by ezramorris on 2008-06-08
Hi,
I seem to have lost the trash icon. I tried re-adding it with 'add to panel', but it won't appear. Could this be a missing icon? All the appropriate icons are in /usr/share/icons/Human/scalable/places (I think).

If I click in just the right place on the panel, the trash appears.

Thanks.



Shown in the attachment is the location the icon should be. Clicking in the correct place displays the trash.

---

### Post by drs305 on 2008-06-08
If this just happened in this session, you could try to refresh the Desktop with:
```
killall gnome-panel
```

If you have already rebooted, switched users, or know this is a recurring problem this isn't likely to help.

---

### Post by ezramorris on 2008-06-08
> **drs305 said:**
> If this just happened in this session, you could try to refresh the Desktop with:
```
killall gnome-panel
```

If you have already rebooted, switched users, or know this is a recurring problem this isn't likely to help.

Thanks, but this is a recurring problem.

Edit: This was fixed with the lastest Ubuntu updates.

---

