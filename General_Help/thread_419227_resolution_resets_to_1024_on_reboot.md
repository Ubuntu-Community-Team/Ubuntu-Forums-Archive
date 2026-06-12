---
title: "resolution resets to 1024 on reboot"
date: 2007-04-22
forum: General Help
---

### Post by jimbojambo on 2007-04-22
I've got a monitor with a native resolution of 1680 x 1050. I had to install NVidia drivers to get Feisty to display anything higher than the usual 1024 x 768. I was able to get the full 1680 x 1050 by going to System Tools > NVidia Settings, and adjusting the resolution there. But after a restart, Ubuntu goes back to 1024 x 768, and I have to go back to the NVidia Settings app and change it back.

What's going on?

I actually just noticed something ... in the "X Server Display Configuration" section of NVidia Settings (the section where I switched to full res), there's a button near the bottom labeled "Save to X Configuration File." I didn't push that yet. Should I? Does that put the 1680 resolution into xorg.conf and keep it at 1680 permanently?

Thanks!

EDIT: never mind, should've done a Google search beforehand. That button would indeed do it, but only if I ran NVidia Settings as a super user, which I just did. Fixed.

---

### Post by Ziox on 2007-04-22
please mark this thread as "resolved"

---

### Post by jimbojambo on 2007-04-22
> **Ziox said:**
> please mark this thread as "resolved"

How? I'm looking everywhere and not seeing it. I checked the help section, couldn't find it.

---

### Post by Ziox on 2007-04-22
I think if you edit your first post, there's a box where you can mark "resolved"

---

### Post by jimbojambo on 2007-04-22
Thanks. It didn't show up in the basic reply controls, but I found it after hitting "Advanced."

---

### Post by Bubs on 2007-04-25
how do you run Nvidia settings as super user?

---

### Post by Bubs on 2007-04-25
I got it.  Thanks for the post

---

