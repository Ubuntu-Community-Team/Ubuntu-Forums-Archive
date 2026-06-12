---
title: "Problems after beryl installation"
date: 2007-01-28
forum: General Help
---

### Post by g0nzo on 2007-01-28
Hi,

I've just updated my nvidia drivers to the latest version using envy and tried to install beryl. I used a script from [this]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Creating_the_script") page, but now xserver can't start.

Here are some errors I remember:
- missing '/lib/modules/2.6.17-10-generic/volataile/nvidia.ko' file
- 'failed to load nvidia kernel module' - probably related to the previous one
- no screens found

I tried to restore xorg.conf using backup copy made by beryl installation script, but I still get the same errors. I tried 'nvidia-xconfig', but it still doesn't work.

Any ideas how to fix it and install beryl correctly?

---

### Post by Puschkin on 2007-01-30
Seems like your kernel module has not been correctly installed.
If the module exists in "'/lib/modules/2.6.17-10-generic/volataile/nvidia.ko'" try
```
sudo depmod -a
```
followed by
```
sudo modprobe nvidia
```
and then try 
```
startx
```
if it works you have to add the module "nvidia" to "/etc/modules" to make it availabe after reboot.

if this isn't working try to get the latest driver from the NVidia-Homepage and compile it yourself
(There are many how-to's out there)

Good luck,
Puschkin

---

### Post by g0nzo on 2007-01-31
Thanks.

Actually reinstalling the nvidia driver using envy fixed the problem.

However beryl doesn't work correctly - when I start beryl manager I can't see windows' title bar or any buttons (so I can't close or move it), additionaly i.e. terminal shows just as a white window, without caret or any text.

I guess I'll wait for a new (hopefully better) release :)

---

### Post by Snookered on 2007-02-16
Same problem, here. Installed Beryl with nvidia driver following instructions on the Beryl website. It upgraded my kernel from 2.6.17-10 to 2.6.17-11. At first Beryl worked,but after shutting down and rebooting the nvidia driver didn't work. The nvidiadriver needed to be reinstalled, and used the instructions on the nvidia website. Now there are no title bars at the top of any window opened. But the cube can be rotated by switching work spaces on the panel.


MSI K8NGM2-FID, onboard Nvidia GeForce 6150/430, AMD64, Edgy 6.10

---

### Post by tribble222 on 2007-02-16
The fix for no window decorations is to add the following line to your xorg.conf

Option "AddARGBGLXVisuals" "True"

---

