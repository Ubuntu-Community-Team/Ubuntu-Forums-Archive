---
title: "Launch program with option"
date: 2012-10-23
forum: General Help
---

### Post by dangerousdave44 on 2012-10-23
I want chromium to launch with this option:  --use-system-ssl

I'm using 12.04 LTS with Unity.  How do I make my Chromium browser launch with that option when I click (ie, I'm not wanting to have to launch via command line every time).  In Windows, I would have accomplished this by using 'modify target.'

Thanks in advance.  This is about my third attempt in as many years at migrating to Linux and it is going very well so far.

---

### Post by Cheesemill on 2012-10-23
Hit ALT+F2 and run the following:
```
gksudo gedit /usr/share/applications/chromium-browser.desktop
```

Then just scroll to the bottom of the file and edit the Exec= line and add your option to the end. Save the file and you should be sorted.

---

### Post by dangerousdave44 on 2012-10-23
Exactly what I was after.  Thanks very much.

---

