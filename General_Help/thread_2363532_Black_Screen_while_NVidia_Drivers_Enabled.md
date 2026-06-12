---
title: "Black Screen while NVidia Drivers Enabled"
date: 2017-06-11
forum: General Help
---

### Post by N1GHTS on 2017-06-11
I have a **desktop computer** with three OS installations selectable by grub.


[LIST]
[*][COLOR=#008080]Windows 7
[/COLOR] 
[*][COLOR=#008080]Kubuntu 15.04
[/COLOR] 
[*][COLOR=#008080]Kubuntu 17.04[/COLOR] 
[/LIST]

My main operating system is **Kubuntu 17.04**. I use 15.04 one in a blue moon. Windows is for games.

For a few months now everything has been fine with 17.04. A few days ago there were storms that knocked out the power to my house and somehow **caused the PSU to fail**. I took my computer to my workshop to replace the PSU using a **low-end monitor to test** if it worked.

When I took it back home and booted up to 17.04 and immediately following the Kubuntu loading screen I was greeted with a **black screen** instead of a blue login screen. I can switch between console mode and graphics mode just fine, but on graphics mode its always a black screen. **The monitor is not off** mind you, its definitely on but all black and no cursor. I've **rebooted countless times** with the same result. 

On my Kubuntu 15.04 and Windows 7 OS the **video accelerator works fine** so I know its **not** a defective video card.

So then I tried to uninstall the following packages in an effort to see if uninstalling the driver would have some positive effect. Note I am using an **NVidia GTX 450** video accelerator.


[LIST]
[*][COLOR=#ff0000]nvidia-367
[/COLOR] 
[*][COLOR=#ff0000]nvidia-375
[/COLOR] 
[*][COLOR=#ff0000]nvidia-opencl-icd-367
[/COLOR] 
[*][COLOR=#ff0000]nvidia-opencl-iicd-375
[/COLOR] 
[*][COLOR=#ff0000]nvidia-prime
[/COLOR] 
[*][COLOR=#ff0000]nvidia-settings[/COLOR] 
[/LIST]

When I removed all these packages I get a very ugly stretched yet **functional unaccelerated video screen** (which is how I am able to use this forum on my computer).

I've tried **reinstalling** them but get the same black screen results, forcing me to unload them again. I've also installed **two older versions** of the driver with the same results.

I'm not sure what to do next to fix this problem. I don't want to have to reinstall my OS. [B]Any ideas :?:

[/B][COLOR=#696969][SIZE=1]*Thank you for your help*[/SIZE][/COLOR]

---

