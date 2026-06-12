---
title: "DVD Sound with VLC"
date: 2005-08-31
forum: General Help
---

### Post by RIVE on 2005-08-31
I use VLC to see DVD's, the problem I have is that no sound is avialable.

Using Totem there is sound but the image is to slow.

Can anyone sugest me how to anable VLC to play DVD's sound?

Thanks in advance, I'm using Hoary ppc.

---

### Post by Perfect Storm on 2005-08-31
Do you have wxvlc, vlc and vlc-plugin-esd installed?
Under Preferences click the advance box, then choose Audio.
Change Audio output module from default to EsounD audio output.
Press the save botton. Hope it helps.

---

### Post by Lord Illidan on 2005-08-31
Typing ```
killall esd
``` in a terminal before launching VLC might also help..

---

### Post by RIVE on 2005-09-01
Thanks for the help, installing vlc-plugin-esd the problem was resolved.

---

