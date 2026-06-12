---
title: "Upgrade to 20.04 changed my GIMP in a bad way"
date: 2021-03-03
forum: General Help
---

### Post by galacticstone on 2021-03-03
One weird side-effect of my recent upgrade from 18.04 to 20.04 is that it tampered with my GIMP installation. It has a different splash screen when it loads and the menus and tools are slightly different. One major negative effect (for me) is that the Sharpen filter is no longer there. There is now an Unsharp Mask where my Sharpen used to be. I used Sharpen ALOT to improve my crummy photos which I use to sell online. I need that filter back, bad. I looked all over the menus and I found a Sharpen that only sharpens a selected area and doesn't appear to do anything. I think it rolled back my GIMP to a previous version for some reason. The weird version I have now is 2.10.18 and I am not sure how to proceed to get my old GIMP and filters back.

Any help would be appreciated. If I can't fix it, I will have to find and learn a new photo editor that has a proper Sharpen tool.

---

### Post by CatKiller on 2021-03-03
The version in 18.04 was 2.8.22. The version in 20.04 is, as you note, 2.10.18. The latest version, which you can install easily as a snap, is 2.10.22.

I don't use it much, but I understand that they're changing everything to use a standard architecture and migrating to gtk 3 now that gtk 4 is here. Maybe one of those projects has changed your workflow? Also Python 2 is now officially dead, which will have affected old unmaintained plugins.

---

### Post by mastablasta on 2021-03-04
workarround: [https://www.gimp-forum.net/Thread-Re-instating-missing-plugins-in-2-10](https://www.gimp-forum.net/Thread-Re-instating-missing-plugins-in-2-10)

they say there are better alternatives, but i am no pro to be able to give you advice on alternative. 

i know that nomacs viewer/editor has some image sharpening tool. or maybe it's just for colour?!?

---

### Post by galacticstone on 2021-03-04
> **mastablasta said:**
> workarround: [https://www.gimp-forum.net/Thread-Re-instating-missing-plugins-in-2-10](https://www.gimp-forum.net/Thread-Re-instating-missing-plugins-in-2-10)

they say there are better alternatives, but i am no pro to be able to give you advice on alternative. 

i know that nomacs viewer/editor has some image sharpening tool. or maybe it's just for colour?!?

Thanks for the link to that GIMP forum. I tried that and it worked. That is a life saver. I like GIMP, but I am not a power-user and my usual workflow is pretty limited. I don't venture outside my narrow workflow, so I am unfamiliar with a lot of it's tools, filters, and plugins.

I mainly just open the photo, resize it, brighten/contrast adjusting, sharpen, and then export for web use. I find it works really well to clean up the images from an ancient digital camera. 

Thanks again!  :)

---

### Post by galacticstone on 2021-03-04
> **CatKiller said:**
> The version in 18.04 was 2.8.22. The version in 20.04 is, as you note, 2.10.18. The latest version, which you can install easily as a snap, is 2.10.22.

I don't use it much, but I understand that they're changing everything to use a standard architecture and migrating to gtk 3 now that gtk 4 is here. Maybe one of those projects has changed your workflow? Also Python 2 is now officially dead, which will have affected old unmaintained plugins.
That sounds like exactly what happened. Most of the other filters and tools that I use were unchanged. It just happened by chance that one of the few changes took place within my usual workflow, so I immediately noticed it.

---

### Post by mastablasta on 2021-03-05
> **galacticstone said:**
> 
I mainly just open the photo, resize it, brighten/contrast adjusting, sharpen, and then export for web use. I find it works really well to clean up the images from an ancient digital camera. 


then try nomacs: [https://nomacs.org/](https://nomacs.org/)

repositories have one version, but there is also flatpack format if you need latest version (see download page).

it loads faster (image viewer), has limited editing options and these operations can easily be done in a batch. i used  auto adjust batch when kids did their scans of schoolwork to make it more visible (pencil is not so visible when you scan especially if insufficient pressure is applied when writing). 

nomacs is similar to irfanview (works only on windows).

---

