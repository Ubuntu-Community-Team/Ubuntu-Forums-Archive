---
title: "Just installed Gutsy. NVIDIA graphics gone!"
date: 2007-10-18
forum: General Help
---

### Post by mjpatey on 2007-10-18
I first ran the Live CD, and it worked BEAUTIFULLY.  1280 x 1024, my monitor's native resolution, came up automatically, and looked pristine, as it did in Feisty.  Upon installing, though, things are different.  :-(

I have a PNY nVIDIA GeForce 6200 card with 256 MB of onboard RAM, and a Dell 1801FP monitor, connected digitally.  Every attempt I make in the new "Screens and Graphics Preferences" dialog fails.  I set it to:

Monitor: Dell 1801FP (Digital), 1280 x 1024 at 60 Hz.

Graphics Card:  Chosen by name, I choose "nv" which worked on Feisty.  I planned to switch to "nvidia" later in order to enable Desktop Effects, also as on Feisty.  Using the other method, choosing the driver by model, I've tried NVIDIA GeForce, GeForce 6 Series, GeForce DDR, and "Legacy", and none of them have worked.

Every one of these attempts falls back to "Plug 'n' Play" monitor at 800 by 600, with a "Generic VESA" driver.  It feels like 1997, and that's being kind.

Does anybody know what I need to do to set Gutsy to my monitor's native resolution, and use my video card's actual driver?

Thanks for any insight you may have!

-Mark

---

### Post by phansiizwe on 2007-10-18
Try: 

System -> Administration -> Restricted Drivers Manager

hopefully, the NVIDIA driver is listed. Tick the Enable box and the NVIDIA drivers should be installed, after which more settings should become available.

---

### Post by mjpatey on 2007-10-18
It was listed, and was already ticked.  However, when I go to enable Desktop Effects, it tries, and says they couldn't be enabled.  I assume because the system is in its fallback low graphics mode.

---

### Post by phansiizwe on 2007-10-18
> I planned to switch to "nvidia" later

Try choosing this and see if it switches to the nvidia driver...

---

### Post by mjpatey on 2007-10-18
It's not an option in the Screens and Graphics Preferences dialog at all.  I was planning to switch to it by enabling Desktop Effects, or by enabling it under Restricted Drivers... but Desktop Effects won't run, and under Restricted Drivers, it says it's already installed and "in use"!  Yet I have no 3D, and am forced to run at 800 x 600 using baseline, generic drivers, and it looks awful.

---

### Post by yiyung on 2007-10-18
Please try to install NVIDIA linux driver by visiting the NVIDIA driver download page. That's always what I am doing whenever I upgrade the kernel. It worked for me.

---

### Post by phansiizwe on 2007-10-18
You might try and disable the NVIDIA driver under Restricted Drivers, press OK, then go in again and re-enable it. If nothing happens, try rebooting between the switch.

---

### Post by mjpatey on 2007-10-18
phansiizwe,

In trying to disable and re-enable as you suggested, I went in and noticed that now (after a reboot) the NVIDIA driver was UN-checked!  So I checked it, it installed the driver (earlier it said it already had the driver, and was using it!), performed the required reboot, and voila!  All my earlier settings are correct, from the monitor to the video driver.

And I'm working at 1280 x 1024, now with Desktop Effects turned on, including the "extra" effects... though I don't know how to access them yet (i.e. the workspace cube...)

Thanks for your help!

-Mark

---

### Post by fragos on 2007-10-18
OPen the Control Ceneter and select Advanced Desktop Effects.  Also available under System-> Preferences-> Advanced Desktop Settings.

---

### Post by pete992000 on 2007-10-19
Hi
I also had this problem. What you need to do is to go to

System -> Administration -> Software Sources

Then enable the restricted drivers repository

You will then be informed you software is not uptodate so click reload and all should be well

Regards Pete

---

### Post by Nunu on 2007-10-19
> **pete992000 said:**
> Hi
I also had this problem. What you need to do is to go to

System -> Administration -> Software Sources

Then enable the restricted drivers repository

You will then be informed you software is not uptodate so click reload and all should be well

Regards Pete

Worked for me on Feisty. Although it didn't like it when i enabled the beta pack of visual effects.

---

