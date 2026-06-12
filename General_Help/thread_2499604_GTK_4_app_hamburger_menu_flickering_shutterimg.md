---
title: "GTK 4 app hamburger menu flickering/ shutterimg"
date: 2024-08-02
forum: General Help
---

### Post by a.mushtaqali on 2024-08-02
Hello every one 
I'm new here
I'm facing a problem with GTK 4 application. when i click om hamburger  menu. the menu start flickering. this happen after gnome 46 release.  with 45 every thing is buttery smooth. i think this bug is gnome's end.  did gnome change something in gnome 46?
I'm facing this issue on every DE now. Fedora Ubuntu and Linux Mint. 
i have old hardware like Intel Pentium Dual Core, 8GB Ram,128 SSD for  Distro installation, 160 HDD for store documents and Pictures &  Nvidia GT 218

---

### Post by &amp;KyT$0P# on 2024-08-02
As a test, does the issue occur if you launch an affected app with [FONT=monospace]LIBGL_ALWAYS_SOFTWARE=1[/FONT] environment variable set?

If that works, next test would be to unset [FONT=monospace]LIBGL_ALWAYS_SOFTWARE[/FONT] and try instead setting [FONT=monospace]GSK_RENDERER=gl[/FONT] environment variable.  Does the issue return?

---

### Post by a.mushtaqali on 2024-08-03
How I can use this command? Did i have to paste LIBGL_ALWAYS_SOFTWARE=1 in terminal

---

### Post by #&amp;thj^% on 2024-08-03
Like this, but i'll use firefox in this example:
```
 LIBGL_ALWAYS_SOFTWARE=1 firefox
```
But yes paste that line in the terminal.
For Files (nautilus)
```
LIBGL_ALWAYS_SOFTWARE=1 nautilus
```
If you are using GTK on very old hardware, you may be better off with the old GL renderer, since it makes fewer demands on the GPU. You can override the renderer selection using the GSK_RENDERER environment variable:

"GSK_RENDERER=gl"

---

### Post by a.mushtaqali on 2024-08-03
This issue is happening on every GTK 4 apps.

---

### Post by #&amp;thj^% on 2024-08-03
> **a.mushtaqali said:**
> This issue is happening on every GTK 4 apps.

We get that very clear from post#1
Did you run the suggested, and if so, did it help?

---

### Post by a.mushtaqali on 2024-08-04
Yes i tried both methods but the issue is same.

---

### Post by #&amp;thj^% on 2024-08-04
That is a problem that would bother me as well.

Recently, GTK gained not one, but two new renderers: one for GL and one for Vulkan.

Implementation details

The old GL renderer uses simple shaders for each rendernode type and frequently resorts to offscreen rendering for more complex content. The unified renderers have (more capable) per-node shaders too, but instead of relying on offscreens, they will also use a complex shader that interprets data from a buffer. In game programming, this approach is known as a ubershader.

The unified renderer implementation is less optimized than the old GL renderer, and has been written with a focus on correctness and maintainability. As a consequence, it can handle much more varied rendernode trees correctly.

Driver problems. The new renderers are using graphics drivers in new and different ways, so there is potential for triggering problems on that side.

Please file problems you see against GTK even if they look like driver issues, since it is useful for us to get an overview how well (or badly) the new code works with the variety of drivers and hardware out there.

But is it faster?

No, the new renderers are not faster (yet).

The old GL renderer is heavily optimized for speed. It also uses much simpler shaders, and does not do the math that is needed for features such as antialiasing. We want to make the new renderers faster eventually, but the new features and correctness make them very exciting, even before we reach that goal. All of the GPU-based renderers are more than fast enough to render todays GTK apps at 60 or 144&#8201;fps.

That being said, the Vulkan renderer comes close to matching and surpassing the old GL renderer in some unscientific benchmarks. [B]The new GL renderer is slower for some reason that we have not tracked down yet.
[/B]
And we know very little about your hardware currently.

Have you tried a a different DE rather than Gnome?

---

### Post by a.mushtaqali on 2024-08-04
First of all thanks for explaination. 
I tried Linux Mint Cinnamon and and kubuntu. Built in apps work fine. But the issue occure when i downlaod  apps from Flatpak ie Mission Center and Clapper
Before Gnome 46 release everything works smoothly. 
Windows 11 working properly and without issue. I think my old hardware is not supported by latest Gnome releases.
Again thank you for Helping.

---

