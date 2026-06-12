---
title: "Tip: fix gaim2 buddy list not showing"
date: 2006-11-05
forum: General Help
---

### Post by jms830 on 2006-11-05
My gaim buddy list wasn't showing up when i clicked the tray icon. It would disappear whenever i clicked on it.

To fix this just delete the prefs.xml file in your home/yourusername/.gaim

Terminal:
```
rm ~/.gaim/prefs.xml
```

afterwards, you may want to open gaim, set up your preferences again, and then backup the prefs.xml file.

Terminal:
```
cp ~/.gaim/prefs.xml ~/.gaim/prefs.xml_backup
```

To restore:
```
cp ~/.gaim/prefs.xml_backup ~/.gaim/prefs.xml
```

---

