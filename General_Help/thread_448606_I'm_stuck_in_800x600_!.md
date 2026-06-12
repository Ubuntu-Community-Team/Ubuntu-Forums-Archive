---
title: "I'm stuck in 800x600 !"
date: 2007-05-19
forum: General Help
---

### Post by ios_base on 2007-05-19
My computer doesn't know what monitor I have.  I used nvidia-settings and it said my monitor's model is "@@@"  Whatever that means.  Can anyone tell me how to tell it what monitor I have?

---

### Post by vigleik on 2007-05-19
Try "sudo dpkg-reconfigure xserver-xorg" and be sure to specify the native resolution when you're asked about it.

---

### Post by ios_base on 2007-05-19
Thanks!  That worked like a charm!  So all it did was modify the /etc/X11/xorg.conf file or what?

---

### Post by nerdman978 on 2007-05-19
It did modify your xorg.conf file and changed the resolution settings so you can select higher resolutions.

---

### Post by misfitpierce on 2007-05-19
Did you update nvidia drivers as well?

---

### Post by ios_base on 2007-05-19
um...  I didn't modify the nvidia configuration manually.  I wouldn't know how.  I'm using the proprietary driver installed with Feisty.  How do people learn how to modify those manually anyway?  Are there man pages for that or what?

---

### Post by strabes on 2007-05-19
Ubuntu doesn't come with proprietary drivers.

---

### Post by ios_base on 2007-05-19
> **strabes said:**
> Ubuntu doesn't come with proprietary drivers.

I saw an interview with Mark Shuttleworth about Ubuntu and he said that the Fiesty version installs proprietary graphics drivers for ATI and Nvidia cards.  The drivers run much faster so I think it's a great idea.  We'll always have our free version if nvidia or ATI doesn't let us use their drivers for free anymore.

---

