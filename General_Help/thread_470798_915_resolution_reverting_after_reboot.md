---
title: "915 resolution reverting after reboot"
date: 2007-06-11
forum: General Help
---

### Post by EvenStevens on 2007-06-11
Installed 915 resolution as I have done many times before.
Rebooted... and it didn't come up as 1440x900.
So I reset the graphics (Ctrl Alt Backspace) and it went into 1440x900. Great.


But after I reboot again it goes back to a lower resolution and I need to reset the graphics each time I turn the laptop on :|
How do I fix this so it's sets to my chosen resolution on each boot?

---

### Post by JohnPhys on 2007-06-11
Have you tried the following instructions?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

I find it odd that that is happening.  I don't have 1440x900, but I have 1280x800, and it always works just fine.

Note:  In my case I didn't have to follow the "make it permanent" section of that link, I just did apt-get install 915resolution, and it runs a script automatically in feisty (maybe edgy too) that sets the correct resolution at boot.

--John

---

### Post by AgentZ86 on 2007-10-29
I've got Nvidia and using the restricted drivers for 3D etc. working nice but when I reboot it reverts back to 1280 X 1024 And I just want 1024 X 768 that works perfect.

Well they both work perfectly but when I reboot it reverts back, then I change it back to 1024 X 768 as root for all users etc. all that stuff.

And reboot and it's fine. But if I use for a while then reboot like lets say tomorrow then it reverts again.

Strange that it would let me reboot a time or two in a short time and work fine, but after about a day or so if I reboot it always reverts. No big deal really but when I boot to windows then back to ubuntu it's really annoying to have to boot into ubuntu twice in order to get my proper resolution.

Anyhow any pointers on this would be nice.
Thanks

---

### Post by ilushkin on 2007-10-29
I have Nvidia 7600 and very same symptoms as the ones noted above. I need some advise, please.

---

### Post by JohnPhys on 2007-11-02
To the two above posters:

This thread is about 915resolution, which (to my knowledge) is only applicable with Intel graphics chipsets on widescreen monitors.  Nvidia chipsets are likely suffering from a different problem (assuming the original poster's problem was 915resolution-related).

---

### Post by ilushkin on 2007-11-02
> **JohnPhys said:**
> To the two above posters:

This thread is about 915resolution, which (to my knowledge) is only applicable with Intel graphics chipsets on widescreen monitors.  Nvidia chipsets are likely suffering from a different problem (assuming the original poster's problem was 915resolution-related).

Did you stumble upon a solutuion yet? I'm still expiriencing this issue.
Thank you in advance.

---

