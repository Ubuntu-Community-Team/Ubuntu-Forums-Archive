---
title: "Framebuffer Resolution."
date: 2007-11-28
forum: General Help
---

### Post by patchon on 2007-11-28
Hello ! 

I got an small problem, well its irritating to not have it working as i want. 

Here we go, 

i have to devices connected to my graphicard, one monitor and one projector. 
When i use the framebuffer it for some reason, limit my resolution to 800x600, if i unplug the projector and only have the monitor connected i can use resolutions up to 1280x1024. 

So, somehow the framebuffer detect an 800x600 limit when projector is plugged in, wich is really strange couse the projector isnt even on. So i dont understand where it gets its limitations from. As soon as i unplug the projector, reboot, then i can use higher resolution. 

Is there some option to the framebuffer to disable that kind of probing or whatever it does to limit my resolution  ? 

Thanks for any suggestions.

/Patrik, Sweden 

Btw, Using 7.10 and Geforce 7800GT.

---

### Post by overdrank on 2007-11-29
> **patchon said:**
> Hello ! 

I got an small problem, well its irritating to not have it working as i want. 

Here we go, 

i have to devices connected to my graphicard, one monitor and one projector. 
When i use the framebuffer it for some reason, limit my resolution to 800x600, if i unplug the projector and only have the monitor connected i can use resolutions up to 1280x1024. 

So, somehow the framebuffer detect an 800x600 limit when projector is plugged in, wich is really strange couse the projector isnt even on. So i dont understand where it gets its limitations from. As soon as i unplug the projector, reboot, then i can use higher resolution. 

Is there some option to the framebuffer to disable that kind of probing or whatever it does to limit my resolution  ? 

Thanks for any suggestions.

/Patrik, Sweden 

Btw, Using 7.10 and Geforce 7800GT.

Hi and welcome, are you using the nvidia settings with this command ```
gksudo nvidia-settings
```

---

