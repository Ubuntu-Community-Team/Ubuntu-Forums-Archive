---
title: "crashdump on encrypted LVM?"
date: 2014-09-24
forum: General Help
---

### Post by Calle_Kabo on 2014-09-24
I'm running an Ubuntu 14.04 Server that's experiencing frequent crashes (once or twice per day). See previous thread [here]("http://ubuntuforums.org/showthread.php?t=2225908").

I figured I could try collecting a crashdump, but it isn't working out very well. When I first installed crashdump and forced a panic it wouldn't reboot into the crashkernel. But then I increased the memory from 128M to 256M and it tries to enter the crashkernel. Yeay! But when it asks for my password for the encrypted disk I can't enter it. The whole thing just sits there and won't accept any input. Is there something more I need to do to make crashdump work with an encrypted LVM?


[ATTACH=CONFIG]256662[/ATTACH]

---

