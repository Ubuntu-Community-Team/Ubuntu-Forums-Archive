---
title: "batch image editing with the gimp"
date: 2008-07-01
forum: General Help
---

### Post by twright on 2008-07-01
hi,
i am trying to apply an effect to 1000 images with the gimp but not having much luck (i have googled extensively on the issue):(

when i try using the the cartoon plugin in the script-fu console it doesn't want to accept the path i have entered
```
> (plug-in-cartoon 1 "/home/tom/Desktop/*.JPG" 0 22 0.88)
Error: Invalid type for argument 2 to plug-in-cartoon 
```the info from procedure browser seems to say that it needs the paths:
> INT32    run_mode    Interactive, non-interactive
IMAGE    image    Input image (unused)
DRAWABLE    drawable    Input drawable
SUCCESS    mask_radius    Cartoon mask radius (radius of pixel neighborhood)
SUCCESS    pct_black    Percentage of darkened pixels to set to black (0.0 - 1.0)it would be a great help if someone could help me figure this out :D

---

### Post by twright on 2008-07-03
finally figured it out :KS,
i posted the resulting script on the gimp plugin repository if anyone is interested:
[http://registry.gimp.org/node/6697](http://registry.gimp.org/node/6697)

---

