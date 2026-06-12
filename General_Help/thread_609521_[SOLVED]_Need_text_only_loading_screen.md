---
title: "[SOLVED] Need text only loading screen"
date: 2007-11-11
forum: General Help
---

### Post by RudolfMDLT on 2007-11-11
Hi there,

I just installed gusty on my laptop and I'm busy smoothing out the wrinkles! :) 

When I boot up, the grub menu appears, as soon as it loads Ubuntu the screen goes black. after a couple of minutes the log in screen appears. Is there any way for me to remove the Ubuntu loading splash screen and just have text showing what's loading?

Thanks,

Rudolf

PS: The laptop is a HP nc6000... a little old now! :)

---

### Post by mcduck on 2007-11-11
Sure. You just need to edit the /boot/grub/menu.lst file, find the line that is used to boot your kernel, and remove the 'splash' option from it. If you want even more text, remove the 'quiet' option as well.

---

### Post by RudolfMDLT on 2007-11-11
Thanks a lot! That actually increased my boot up time by more than 15seconds! WOW! THANKS!

---

