---
title: "How do you enable vsync"
date: 2008-01-12
forum: General Help
---

### Post by BahBah on 2008-01-12
How do you enable vsync please ?

I have an nvidia 8800GTS 640MB, using the proprietary driver and Gutsy.

Thanks

---

### Post by lian1238 on 2008-01-13
Do you have nvidia-settings installed? You can turn vsync on with that. I installed my driver with Envy, and it installed nvidia-settings for me.

---

### Post by BahBah on 2008-01-13
Hi,

Thanks for your reply. I do have nvidia-settings installed, and have ticked everything I can see that relates to vsync but it's not working. If I run, for example WoW, my fps can drift off in the 100's when it should be locked to 60.

---

### Post by lian1238 on 2008-01-13
I don't play WoW, but can you do this in WoW?:
Esc -> Video Options -> Vertical Sync.

---

### Post by BahBah on 2008-01-13
Hiya,

Thanks again for your reply. Yep I have that ticked.

---

### Post by lian1238 on 2008-01-14
I'm out of ideas. Anyone else?

---

### Post by Sjet on 2008-05-31
I had the same problem in WoW, using Hardy and ForceWare beta 173.08.
To fix this, i have to run
nvidia-settings
every time i restart x. Although the boxes remain ticked, the options don't get applied until i started the config. You don't need to un/recheck the boxes.
WoW's ingame VSync option doesn't have any effect if you're running in OpenGL mode, it applies to Direct3D mode only.
You can reproduce and observe this strange behavior quite simple if you have a nVidia GPU and a LCD: Notice how the screen goes black for a second if you check/uncheck 'Force Full GPU Scaling'? Enable it. Now, restart x. As soon as you will run nvidia-settings, the screen will go black for a second, as the option has just been applied.

---

