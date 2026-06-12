---
title: "Lightdm doesn't start"
date: 2012-11-17
forum: General Help
---

### Post by EvertVP on 2012-11-17
I upgraded my NVIDIA drivers to 310.19 manually (with service lightdm stop, sh NVIDIA-310.19.run and reboot), and when ubuntu (12.10) started again, it froze. I looked around a bit on the internet, tried to apply a few fixes, and now ubuntu boots into tty1. service lightdm start now gives me the same screen  as  the previous 'normal' boot did.
The last few lines of the text on my monitor when I do this are:
* Starting set console font
* Stopping set console font
* Starting Userspace bootsplash
* Stopping
* Starting LightDM Display Manager
* Stopping Userspace bootsplash

And then I just get a blinking underscore.
Thus, I assume the problem is with lightdm. Any ideas on how to fix/troubleshoot this?

OK, fixed by installing 304 via apt.

---

