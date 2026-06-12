---
title: "Changing screen resolution through terminal?"
date: 2006-12-21
forum: General Help
---

### Post by DasLemm on 2006-12-21
Somehow when I went to change my screen resolution, the screen didn't actually change. Then when I restarted my computer and logged in, the screen went out. Apparently I changed it to a resolution that didn't actually work with my monitor. So now, I need to change the screen resolution via one of the text-based login modes. How would I do that?

---

### Post by taurus on 2006-12-21
Boot into recovery mode from GRUB menu and at the prompt, do

```
nano -w /etc/X11/xorg.conf
```

---

### Post by DasLemm on 2006-12-21
Is there a section that i can edit that will change the resolution of a specific user?
Because only one user has this problem. I can still log in to my guest account and it works fine (simply no admin controls).

---

### Post by DasLemm on 2006-12-22
So what do i do to the xorg config file?

---

### Post by taurus on 2006-12-22
> **DasLemm said:**
> So what do i do to the xorg config file?

I thought you said you need to modify it to get it to work!!!

---

### Post by mitanc on 2007-02-12
> **DasLemm said:**
> So what do i do to the xorg config file?

Scroll down the file, I don't have it in front of me, but there will be a bunch of resolutions.  Change the one thats wrong to what you want and you should be good to go (as long as the resolution you want is supported by your monitors configuration)

If you need more help google xorg config file of XF86Config.  

Cheers!

---

