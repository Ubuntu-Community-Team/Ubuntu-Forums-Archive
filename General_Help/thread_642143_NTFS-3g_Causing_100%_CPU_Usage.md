---
title: "NTFS-3g Causing 100% CPU Usage"
date: 2007-12-16
forum: General Help
---

### Post by Anthony M on 2007-12-16
Just the past few days NTFS-3g has been causing 100% CPU everytime I try to write to my second HD, which is formatted to NTFS, as I dual boot w/ XP. This renders me unable to access anything on that HD....

The only way to stop it is to either kill "mount.ntfs-3g" or log-out.

What can I do to solve this?

Thanks,
Anthony

---

### Post by Anthony M on 2007-12-16
So Ive realized that this is attributed to two pdf files in My Documents. These pdfs have Japanese characters in them that Evince was having trouble handling. After letting the folder sit open for a few hours while Evince created the thumbnail preview, my CPU usage went back down to normal percentages. 

Now, when I open these two files with the Japanese characters, Evince doesnt even show the characters....Its just blank.

Does Evince have a Japanese add-on?

Thanks!

---

### Post by p_quarles on 2007-12-16
I did a quick search of the repositories, and didn't find one specifically for Evince, but it will probably work if you install the Gnome language support pack for Japanese:
```
sudo apt-get install language-pack-gnome-ja
```
If that doesn't take care of the problem, the XPDF package (which is a generic PDF viewer for X windows environments) has a Japanese plugin:
```
sudo apt-get install xpdf-japanese
```

---

