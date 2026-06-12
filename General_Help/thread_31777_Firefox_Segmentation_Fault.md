---
title: "Firefox Segmentation Fault?"
date: 2005-05-04
forum: General Help
---

### Post by DutchLau on 2005-05-04
Hello Ubuntu community!

Firefox keeps shutting down unexpectedly, so I decided to run it from the terminal. These are the error messages I keep getting:

> ADDED URL: herbie_fully_loaded_m240.mov
code: 45
 speed 2800
ADDED URL: herbie_fully_loaded_m240.mov
code: 45
 speed 2800
Segmentation fault 

I keep getting this "segmentation fault" is this a problem with the website, or with firefox and what can I do to fix it?

Thanks already,

DutchLau

---

### Post by kvidell on 2005-05-04
My first guess would be that FireFox is trying to load a plugin or external application through plugger to play your .mov there... and either mozplugger can't load the app, or the app loads but doesn't have the .mov codec needed and Firefox poohs the bed.

Do you think this could be?
- Kev

---

### Post by DutchLau on 2005-05-04
Maybe, but I have mozilla-mplayer installed and I have all w32codecs & the gstreamer codecs, so I don't think this could be it. 

Any other ideas? It seems only to do this with certain ([www.apple.com](www.apple.com)) sites.

Thanks,

DutchLau

---

