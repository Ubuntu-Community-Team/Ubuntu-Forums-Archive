---
title: "Recommendation needed for a lightweight text viewer"
date: 2012-11-24
forum: General Help
---

### Post by PeterTaps on 2012-11-24
Folks,

I am running minimal version of Ubuntu 12.04 with Openbox. 

Now I am looking for a lightweight graphics viewer for viewing text files. The idea is to associate this viewer within PCManFM file manager.

Note that the requirement is to view a text file, not necessarily edit it. However, if there is no text viewer available, I guess I could use a lightweight text editor.

Your help is much appreciated.

Regards,
Peter

---

### Post by VCoolio on 2012-11-24
Try with zenity:```
cat <file> | zenity --text-info
or
zenity --text-info --filename <file>
```
You can also specify --height=<px> and --width=<px>

Or you can use a lightweight text editor like x2.

---

### Post by philinux on 2012-11-24
> **PeterTaps said:**
> Folks,

I am running minimal version of Ubuntu 12.04 with Openbox. 

Now I am looking for a lightweight graphics viewer for viewing text files. The idea is to associate this viewer within PCManFM file manager.

Note that the requirement is to view a text file, not necessarily edit it. However, if there is no text viewer available, I guess I could use a lightweight text editor.

Your help is much appreciated.

Regards,
Peter

Try leafpad.

---

### Post by Cheesemill on 2012-11-24
Or just stick wih a CLI app and use [most]("apt://most").

---

### Post by PeterTaps on 2012-11-26
Thank you all for your help.

Leafpad turned out to be the application that is closest to my needs. Lightweight, easy-to-use, etc.

Regards,
Peter

---

