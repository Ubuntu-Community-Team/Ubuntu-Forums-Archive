---
title: "Not recieving updates"
date: 2006-08-16
forum: General Help
---

### Post by ThrobbingBrain66 on 2006-08-16
About two weeks ago it occured to me that I hadn't been notified of any updates in over a week.  I went for a few more days and still hadn't received any.  About one week ago I did a clean install as I assumed with all my tinkering that I borked Adept.  I assumed that all my update problems would be fixed, but since I did the fresh install, I STILL have not received any updates.  Has there just been a lack of updates lately or is something more seriously wrong?

EDIT: using ```
 sudo apt-get upgrade
``` just now gives me three updates (imagemagick, libkrb53 and libmagick9)....so it seems to me that adept notifier just isnt working.  any ideas?

---

### Post by ThrobbingBrain66 on 2006-08-16
I MAY have fixed the problem....I just purged adept and reinstalled and when I rebooted, adept_notify welcomed me with those three updates...any ideas would still be welcome.

---

### Post by taurus on 2006-08-16
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by ThrobbingBrain66 on 2006-08-17
i always use those two commands in tandem (sudo apt-get update && sudo apt-get upgrade).  thanks though.  the problem is/was that adept would never pop up in my system tray telling me i had updates.

---

### Post by jmacak on 2006-08-17
Hi 

You know, I had the same problem, no notification of updates in the system tray.  If I went to the update menu and manually fired off the update process, I'd get the updates just fine.

I came to find out that lame-*** gnome requires you to set aside a little area for 'notifications'.  During my customization, I inadvertently removed that area, and thus never got the notifications.  I added the notification area back and now I get the update notifications.  It's added the same way that you would add little widgets or tools to the bar.

cheers

joe in seattle

---

