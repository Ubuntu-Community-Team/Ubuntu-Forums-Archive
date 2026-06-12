---
title: "Strange Graphics Issue on Fresh Install"
date: 2012-12-04
forum: General Help
---

### Post by Martom on 2012-12-04
Hey all,

I just installed Xubuntu 12.10 on a brand new laptop and I'm seeing a weird graphics issue. I first noticed this during the (graphical) installation and it is persisting into the installed environment. Some bits of text and icons are getting garbled, either from the get-go or after mouse-over. It's a bit hard to describe, so I attached a screen shot of an example instance in the Ubuntu Software Center. Can anyone tell me what is going on here?

Cheers

---

### Post by Rebelli0us on 2012-12-04
I've had this, it's common complaint here. Mine had to do with the open source NVIDIA driver. I fixed it by installing nvidia-current in Synaptic.

---

### Post by Impavidus on 2012-12-04
It's a buggy graphics driver. Depending on the vendor of your graphics chip you may be able to install other drivers. If you're unlucky and have a brand new graphics card, you may have to wait for a bug fix. Maybe you can tell us what graphics card you're using?

---

### Post by Martom on 2012-12-04
I have an NVidia card so I tried Rebelli0us' suggestion and, so far, I haven't seen anything garbled, so it seems to have done the trick. Thanks!

---

