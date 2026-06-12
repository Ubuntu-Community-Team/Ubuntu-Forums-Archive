---
title: "Why is my Open Office doing this at every launch?"
date: 2007-03-16
forum: General Help
---

### Post by Hishgraphics on 2007-03-16
[IMG]http://img.photobucket.com/albums/v476/arctrooperbum/ubuntu/openoffice.png[/IMG]

Apparently when my sister was working on a word processing file, Ubuntu froze. When she rebooted and launched OO again, this message appears, but upon hitting the "recover" button, the "recovery failed" message is displayed. And this happens EVERY time OO is launched now.

Is there a way to stop this?

Thanks.

---

### Post by Lord Illidan on 2007-03-16
Can you start openoffice from the terminal with the switch -norestore ?

I don't know the exact command as it may be different on your system. On mine, it is openoffice,org-2.1 -norestore

---

### Post by Hishgraphics on 2007-03-16
Yipes.

All I had to do was hit the "No" button.

Sorry all. I'm an idiot.

Thanks for the suggestion anyway, Lord Illidan. :)

---

### Post by Hagar Delest on 2007-03-18
You can also try to delete the file ~/.openoffice.org2/user/registry/data/org/openoffice/office/recovery.xcu

---

