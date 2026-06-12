---
title: "Photshop 7 running in Wine...kind of...need to copy directories?"
date: 2008-06-16
forum: General Help
---

### Post by calicat on 2008-06-16
Im having a problem with PS 7 running in wine...I get a error message when I try to enter text.  I searched the internet and found this as a fix:

[CENTER] I had an error every time I tried to enter text in PhotoShop that said default font not found and I could never enter text in PhotoShop. Well, I copied over the whole directory 'C:\WINDOWS\Fonts' to '/.wine/drive_c/windows/fonts' and now I can use text in PhotoShop 7. I just thought that I would post this incase anyone else had this problem too. Oh, and the 'C:\WINDOWS\Fonts' directory is my XP install on the other partition in case that was not clear.[/CENTER]

But I don't really know how to copy over files from one directory to another and dont want to mess anything up.. Could someone give me simple, step-by-step instructions??

Thanks so much!  :KS

---

### Post by ibuclaw on 2008-06-16
1) Enter the mounted XP partition in nautilus  (Usually under /media) and enter the **WINDOWS** directory, find and select the "Fonts" folder and copy.

2) Go into your home directory and show hidden files/folders (**Ctrl+H**). Locate the ".wine" folder and proceed to enter it, continuing on with "drive_c/windows" and paste the Fonts folder in that directory.

Regards
Iain

---

### Post by calicat on 2008-06-16
> **tinivole said:**
> 1) Enter the mounted XP partition in nautilus  (Usually under /media) and enter the **WINDOWS** directory, find and select the "Fonts" folder and copy.

2) Go into your home directory and show hidden files/folders (**Ctrl+H**). Locate the ".wine" folder and proceed to enter it, continuing on with "drive_c/windows" and paste the Fonts folder in that directory.

Regards
Iain

I don't have 'media' under my tabs, I searched for nautilus in add/remove and all it gives me is a add on...

I'm very new with this OS, Im sorry if Im being a blonde

---

