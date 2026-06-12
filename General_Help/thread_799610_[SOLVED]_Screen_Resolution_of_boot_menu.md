---
title: "[SOLVED] Screen Resolution of boot menu"
date: 2008-05-19
forum: General Help
---

### Post by tad1073 on 2008-05-19
How do I change the resolution of the boot menu?

---

### Post by ajgreeny on 2008-05-19
Do you mean the splash screen which shows the lengthening orange bar?  If so you can try editing the resolution in the file /etc/usplash.conf but make sure it's a resolution that your screen can handle.

Here's mine so you can see what it looks like:-
 
cat /etc/usplash.conf
# Usplash configuration file
xres=1280
yres=1024

---

### Post by Joeb454 on 2008-05-19
If you mean the Menu where you select what OS you want to boot (the one you can choose Recovery Mode from), then I don't think that it's possible. I could be wrong however

---

### Post by tad1073 on 2008-05-19
No, I already have mine set to vga=795, I am talking about the actual menu that list the kernels.

---

### Post by tad1073 on 2008-05-19
> **Joeb454 said:**
> If you mean the Menu where you select what OS you want to boot (the one you can choose Recovery Mode from), then I don't think that it's possible. I could be wrong however

Yes, that is what I am asking about.

---

### Post by ibuclaw on 2008-05-19
Would adding a large boot menu image help?

[http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

Or do you already have one in place?

Regards
Iain

---

