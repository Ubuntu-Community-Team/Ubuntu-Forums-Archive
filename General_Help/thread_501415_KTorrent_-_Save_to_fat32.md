---
title: "KTorrent - Save to fat32 ?"
date: 2007-07-15
forum: General Help
---

### Post by drytear on 2007-07-15
Hello, i'm having a problem with ktorrent, it doesn't want to save the downloads to a fat32 partition. Is that even possible? cause i know ktorrent has to set some permissions and i think he doesn't know how to do that on fat32. Is there any workaround or something that will enable it to use a fat32 partition directly for downloads?

---

### Post by mikewhatever on 2007-07-15
If you, not ktorrent, have write permission for that partition, there should be no problem. Another thing to remember is that FAT32 has a file size limit of up to 4 GB.

---

### Post by scooper on 2007-07-15
From what I remember I think there's also an issue with ktorrent needing to create symlinks to downloading files.  This is impossible to do with FAT32.  That's why I switched to utorrent under wine.

---

### Post by drytear on 2007-07-16
my utorrent under wine goes black if i minimize the wine window in wich it runs. what's happening? it won't unminimize.

---

### Post by QCompson on 2007-07-16
> my utorrent under wine goes black if i minimize the wine window in wich it runs. what's happening? it won't unminimize.

Have you tried disabling the system tray icon (both minimize and close to tray options)?

I used to have various issues with my utorrent under wine until I did this.

edit: for the record, I have downloaded many torrents successfully using ktorrent to a fat32 partition.

---

### Post by drytear on 2007-07-17
thanks man! that did the trick. it's working now.

---

