---
title: "AMD Over/Underscan"
date: 2013-03-21
forum: General Help
---

### Post by SgtHubcap on 2013-03-21
gfx:Ati 6870HD

Upon reboot scan settings get set back to default. Is there a way to fix it, it must not be saving my settings. 
Is it possible to change the default configuration file, if there is any?

---

### Post by SgtHubcap on 2013-03-22
Had to do this twice. The first time I changed the setting with in the Catalyst gui
then I inserted code in to terminal:

```
[FONT=Ubuntu Mono]sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0[/FONT]
sudo reboot
```

Didn't work... 

So, I un-ticked "Use scaling value override"->Set my Scaling option->Re-inserted
I had become lazy by now, and remember my settings wouldn't even save after I re-logged in. 
So I did just that,re-logged, seem to be saved and didn't change my display. So I preceded to Reboot, low and behold it worked and saved. 
Hope this helps.

---

