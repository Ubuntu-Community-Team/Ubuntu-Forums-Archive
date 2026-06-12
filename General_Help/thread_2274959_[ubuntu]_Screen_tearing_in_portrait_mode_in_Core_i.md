---
title: "[ubuntu] Screen tearing in portrait mode in Core i5 Intel NUC (haswell version)"
date: 2015-04-23
forum: General Help
---

### Post by Poisonwolf on 2015-04-23
Hi folks,

I'm struggling with a graphical issue.  I have a Core i5 NUC with the HD5000 integrated GPU but I'm getting abysmal performance in the Unity Desktop Environment (ubuntu 14.04 lts).  I'm getting screen tearing when I'm dragging windows across the desktop, when I'm scrolling in Firefox or Chrome, etc. 

I only started noticing this issue once I started using my monitor in portrait mode (1080x1920). Screen tearing does not occur in landscape mode. 

Does anyone have any solution to this? 

My 7 year old laptop running a Core 2 Duo chip with a 1280x800 resolution does not even have screen tearing when Im dragging windows across the desktop (also ubuntu 14.04 lts).  I know it's not a resolution issue because when I reduce the resolution to 600x800 (portrait mode) on my NUC, I STILL get screen-tearing. 

Thank you in advance for any help you might provide.  This is extremely annoying. =(

---

### Post by mc4man on 2015-04-23
If you are using compiz - 
It would appear that what compiz does to prevent tearing are lost when you rotate the screen 90 degrees, file a bug if concerned. 
(I've a laptop so no possible use here of a rotated screen

---

### Post by Poisonwolf on 2015-04-23
> **mc4man said:**
> If you are using compiz - 
It would appear that what compiz does to prevent tearing are lost when you rotate the screen 90 degrees, file a bug if concerned. 
(I've a laptop so no possible use here of a rotated screen

Thank you so much for your quick response.  I am using the default Ubuntu 14.04 LTS and have not deviated from the built in Compiz compositor.  Is there a different compositor that works for portrait mode? I tried compton by temporarily installing XFCE4, as I could not disable compiz without disabling other Unity plugins that rely on it (everything disappears in unity when I try to disable the compiz).  No luck as well, compton does not appear to work in portrait mode as I still got screen tearing all over.

---

