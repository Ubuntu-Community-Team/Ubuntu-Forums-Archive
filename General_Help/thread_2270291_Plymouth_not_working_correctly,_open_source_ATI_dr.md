---
title: "Plymouth not working correctly, open source ATI driver"
date: 2015-03-21
forum: General Help
---

### Post by residualbit on 2015-03-21
Running 14.04.2

At boot, the splash screen is just solid puprle, no logo with dots. I've installed the numix theme, and if I try to use it, it seems to sort of affect the shutdown splash, but not the boot. I say sort of, because it also just shows a solid color.

I'm doing 
```
sudo update-alternatives --config default.plymouth
```
```
sudo update-initramfs -u
```

Any ideas?

---

### Post by residualbit on 2015-03-22
I have another computer I was playing around with and am not having this problem there. Granted, that one is using intel integrated graphics.

Is this maybe a bug with the open source ATI driver? I'm aware the the proprietary ati and nvidia drivers cause all sorts of issues with plymouth, but I though the open source ones were fine.

Lastly, I've wiped and re-installed a few times just to be sure, but same problem every time. Strangely enough, when I boot from USB to "try ubuntu" the splash screen works fine. Very weird, and annoying...

---

