---
title: "Ubuntu Studio and nvidia-settings"
date: 2008-01-18
forum: General Help
---

### Post by Oysterville on 2008-01-18
Has anyone tried this combination successfully?  When I go to install nvidia-settings apt-get suggests to remove nvidia-glx-new and install nvidia-glx-legacy.  However, when this happens the nvidia module disappears and X won't start.  The only thing I can do is reverse the process by removing the legacy and nvidia-settings and installing the glx-new.  However, then I lose nvidia-settings and I'd like to have more control over my nvidia output.

Did I just make no sense whatsoever?  Anyone have any ideas on this one?

Thanks.

---

### Post by overdrank on 2008-01-18
> **Oysterville said:**
> Has anyone tried this combination successfully?  When I go to install nvidia-settings apt-get suggests to remove nvidia-glx-new and install nvidia-glx-legacy.  However, when this happens the nvidia module disappears and X won't start.  The only thing I can do is reverse the process by removing the legacy and nvidia-settings and installing the glx-new.  However, then I lose nvidia-settings and I'd like to have more control over my nvidia output.

Did I just make no sense whatsoever?  Anyone have any ideas on this one?

Thanks.

HI and what is the model of the graphics card? Have you tried the command ```
gksudo nvidia-settings 
``` with the nvidia-glx-new installed?

---

### Post by Oysterville on 2008-01-18
> **overdrank said:**
> Have you tried the command ```
gksudo nvidia-settings 
``` with the nvidia-glx-new installed?

Hey, lookie there!  *foreheadslap*

Thanks.

---

