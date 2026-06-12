---
title: "Help With Un-Installation"
date: 2013-05-15
forum: General Help
---

### Post by Cowi on 2013-05-15
I've installed a corrupted Ubuntu from Wubi and I can't find out how to un-install it could somebody please help and describe how to fix this in a easily understood way? (I am using Windows 7)

---

### Post by ajgreeny on 2013-05-15
Go to Windows Control Centre and uninstall ubuntu/wubi the same way as any other application in windows using Add/Remove, or whatever it's now called.

Simple.

---

### Post by Cowi on 2013-05-15
I have tried to do this but Wubi / Ubuntu aren't there.

---

### Post by Mark Phelps on 2013-05-15
OK, then do the following:

1) If the option in the Windows OS selection menu for Ubuntu is still there, download and install EasyBCD from NeoSmart Technologies.  Launch that and use the option to remove the Ubuntu option from the BCD.

2) Use Windows Explorer to remove the root.disk file from your Win7 OS partition.

---

### Post by Cowi on 2013-05-15
Thanks I'm trying this right now!

---

