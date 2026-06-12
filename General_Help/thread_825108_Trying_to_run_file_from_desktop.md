---
title: "Trying to run file from desktop"
date: 2008-06-10
forum: General Help
---

### Post by wrgb2 on 2008-06-10
Hi,
I have dowloaded a game to the desktop that I want to install.  The name of the file is "BtRLDemoInstaller.run" .  I am trying to run this file by typing, in the terminal "./BtRLDemoInstaller.run" , but it says "no such file or directory".  What am I doing wrong?
Thanks,
Randy

---

### Post by overdrank on 2008-06-10
> **wrgb2 said:**
> Hi,
I have dowloaded a game to the desktop that I want to install.  The name of the file is "BtRLDemoInstaller.run" .  I am trying to run this file by typing, in the terminal "./BtRLDemoInstaller.run" , but it says "no such file or directory".  What am I doing wrong?
Thanks,
Randy

HI and have you changed directory to where the file is located
```
cd ~/Desktop
```and you will more than likely have to use sudo also.

---

### Post by Ejas12 on 2008-06-10
Did you tried o execute it from the desktop directory 
```

```
 cd Desktop
./BtRLDemoInstaller.run

---

### Post by wrgb2 on 2008-06-10
Ok, that got it.  Thanks, guys.
Randy

---

