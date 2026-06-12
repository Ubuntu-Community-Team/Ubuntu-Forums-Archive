---
title: "RAR extraction."
date: 2023-11-24
forum: General Help
---

### Post by Hewjr100 on 2023-11-24
Downloaded an RAR compressed file, but when I right click to extractI get the folllowing error:

RAR Solid Archive Support Unavailable.

If there is a GUI app for this please let me know.

Henry

---

### Post by Holger_Gehrke on 2023-11-24
Most of the graphical (un-)packers are just front-ends for command line tools. For RAR archives there are two unpackers: 'unrar-free' and 'unrar'. The '-free' version is a clean-room reimplementation following the format description of older versions of RAR and is therefore limited in its compatibility and won't unpack newer RAR files. Use ```
dpkg -l  'unr*'
``` to see which version is installed and install the non-free version if it's not installed. The non-free unrar in the multiverse part of the repositories for Ubuntu 22.04 is at version 6.11 and should support solid archives.

Holger

---

### Post by Frogs Hair on 2023-11-24
Try the following which works with the file roller.

```
sudo apt install p7zip-full
```

---

### Post by Hewjr100 on 2023-11-24
Frogs Hair, I went with your option.  Thank you very much.

Henry

---

### Post by Hewjr100 on 2023-11-24
BTW there is an extension that makes the top bar exit menu cleaner and not a wide, but I cannot remember the name and can't find it in Gnome Extensions web site.  Anyone know the name.

Henry

---

### Post by Hewjr100 on 2023-11-24
BTW there is an extension that makes the top bar exit menu cleaner and not a wide, but I cannot remember the name and can't fing it in Gnome Extensions web site.  Any one know the name.

Henry

---

### Post by Hewjr100 on 2023-11-24
What extension slims down the top bar menu on the left.

Henry

---

### Post by MAFoElffen on 2023-11-25
This one? [https://extensions.gnome.org/extension/5669/compact-top-bar/](https://extensions.gnome.org/extension/5669/compact-top-bar/)

---

### Post by Hewjr100 on 2023-11-25
Yes I saw that one, the one I am trying to find does the same thing to the top bar where you can logout shutdown or lock system window.

Henry

---

### Post by Hewjr100 on 2023-11-25
BTW the extension I was looking for is "Compact Quick Settings".  How ever it is not compatible with Gnome 45 yet.

Henry

---

### Post by ariel on 2024-11-10
For the record, PeaZip from flatpak can handle "rar solid archives" with no issues. 

RE replies above, the non-free version of unrar that can be installed easily with apt works as well but it's not 'picked up' by file roller for some reason (I guess file-roller uses the free version library), so "unrar non-free"  can only be used from the command line: unrar x some-solid-archive.rar

---

