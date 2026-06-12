---
title: "USB desktop icon missing (8.04)"
date: 2008-06-09
forum: General Help
---

### Post by BrianR on 2008-06-09
What happened to the USB desktop icon that use to show up when you put a USB drive into the USB port? In 7.10, it would automatically show up. I like this action because now the only way to unmount the USB drive is to go the the Places pull-down menu, open the drive window and choose Unmount under the File menu. This is a lot of extra work. Is there a setting somewhere which turns this feature back on?

BrianR

---

### Post by ValPaliy on 2008-06-09
Had a similar problem. If you have (as I imagine you would) gconf-editor, start it Applications -> System Tools -> Configuration Editor (or Alt+F2 -> gconf-editor), go to apps -> nautilus -> desktop and select volumes_visible :-) Hope that helps!

---

### Post by BrianR on 2008-06-10
That's the ticket!!!

And I was able to turn on the Trash icon as well.

Thanks,

BrianR

---

