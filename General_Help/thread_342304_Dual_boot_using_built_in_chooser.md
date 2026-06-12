---
title: "Dual boot using built in chooser"
date: 2007-01-19
forum: General Help
---

### Post by Dokatz on 2007-01-19
I have a built in like, Device chooser when I press F8 while my mobo boots. I currently have ONE hard drive hooked up, With Ubuntu installed on it. If I were to unhook this drive as a precaution, Install a second one, Install Windows on this drive and when all is said in done, Connect the one I had before...

Would everything just be fine? IE: SYstem will boot to my ubuntu drive cause I set is as default but if I choose to go windows I can do that to. GRUB would be on the MBR of my ubuntu drive and windows whatever boot on its own drive.

What do you think?

---

### Post by puneit on 2007-01-19
Never tried this... But it seems like it should work. Since both will have their own MBRs, and you are booting from one at a time, I sounds like it can work
Are you saying, the you can choose the HDD to boot from when you press F8...
If yes, then you can try this. But if you want to be too sure about it, wait for someone in the forum who knows this situation well to answer this post

---

### Post by Dokatz on 2007-01-19
I'll give it a shot, Worst comes to worst I reformat. Thats always fun.

---

### Post by rasgryphon on 2007-01-20
I do something similiar and it works fine.  I have two hard drives, one with windows on it, and one with Ubuntu on it.  Grub is installed on the HDD with Ubuntu and the windows boot loader is installed on the windows hard drive.  I just choose my boot device with F8 if I want to boot into the other OS.

---

