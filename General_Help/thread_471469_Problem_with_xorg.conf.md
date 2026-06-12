---
title: "Problem with xorg.conf"
date: 2007-06-12
forum: General Help
---

### Post by RelativelyQuantum on 2007-06-12
Hi all.

When I booted up a few minutes ago, my pointer was tracking slower than it usually does. I went into xorg.conf to see weather any settings had changed, and everything was the same as I had left it. I rebooted twice, only to find the same result. Also, tapping is enabled, despite the fact that my "MaxTapTime" is set to 0, and my trackpad scroll setting is disabled.

Any suggestions?

---

### Post by RelativelyQuantum on 2007-06-12
The problem persists; anything would help :(

---

### Post by dogatemycomputer on 2007-06-12
> **RelativelyQuantum said:**
> Hi all.

Any suggestions?

I'm not sure I can help  but I suggest including a copy of your xorg.conf and hardware information may lead to additional responses.   At the very least others running linux searching Google may have a better chance of finding your post and commenting on their successes and failures.

Good luck!

---

### Post by fragos on 2007-06-13
Try installing "gsynaptics" from the Ubuntu repositories.  Synaptic can be used for this purpose.  This will add to System-> Preferences a Touchpad preference tool.  It's a little more understandable and being GUI is easier to use.  These overide xorg.conf and will be used accross boots.

---

### Post by RelativelyQuantum on 2007-06-15
Thanks - this really helps. I'll have to use it when I reinstall Edgy, though, as my computer stopped recognizing my screen in Feisty :(. I appreciate the advice in any case; I'm sure it'll come in handy in the future ;)

---

