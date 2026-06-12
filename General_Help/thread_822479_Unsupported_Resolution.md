---
title: "Unsupported Resolution"
date: 2008-06-08
forum: General Help
---

### Post by befragen on 2008-06-08
When I boot my computer I can pick from Windows Vista or Linux just like normal, when I boot linux, you can see the little loading progress bar thingy and then my screen goes black and says it is running an unsupported resolution and suggests I fix it. Well how the heck am I supposed to fix it if I can't see it? Please help. Thanks.

---

### Post by ago on 2008-06-08
press esc at boot after "ubuntu" and select the second option

---

### Post by befragen on 2008-06-08
Thank you much. I'll try that now.

---

### Post by kumarkrishnan on 2008-06-10
I also have same problem. Description
My Ubuntu installation with wubi went without problem. After that, Rebooted and Ubuntu started. After getting status bar moving left and right, suddenly, My Monitor (LG, TFT monitor with 1024X768 resolutions) shows out of range (46 KHz/ 63Hz). But If I press Ctrl+Alt+F1, I am getting still some booting process and after some times, login screen opens. After that there is no problem and even I checked wvdial application. Works well. I had never seen this problem while running with Virtual Machine. Please some one, let me know, whether out of range problem will damage my monitor or how to solve this? 

Today I will try second option. It will be helpful, if someone tells exactly, what I have to do with this option.

With Thanks and Best Regards,
KK

---

### Post by ago on 2008-06-11
Yes try the safe graphic mode. That is generally a monitor issue, but the installer is fully automated and it will finish even if you turn the monitor off. 

If you have already installed from the Linux side (second reboot), you can always boot in rescue mode and manually adjust your video settings.

---

### Post by kumarkrishnan on 2008-06-11
Hi,
  There is no graphical safe mode option. Just I entered safe mode and selected ?fix x..." and rebooted. Still problem exists.
   Provide me some other suggestion.
Regards,
KK

---

### Post by ago on 2008-06-11
you need to edit /etc/X11/xorg.conf

sudo nano /etc/X11/xorg.conf

search the forum for the appropriate parameters to use given your monitor.

---

### Post by kumarkrishnan on 2008-06-11
Yesterday. I checked xorg.conf file. There is no resolution parameter in it (Option "Modes" "1024X768"). I believe that need to be added under SubSection. I will try this today. Did you mean the same thing?
KK

---

