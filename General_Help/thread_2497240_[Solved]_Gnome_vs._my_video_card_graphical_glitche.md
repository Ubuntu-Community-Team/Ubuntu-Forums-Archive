---
title: "[Solved] Gnome vs. my video card: graphical glitches in core Gnome apps"
date: 2024-04-28
forum: General Help
---

### Post by eco2geek2 on 2024-04-28
I was running Ubuntu 24.04 from live media to see what it looked like, and was perturbed to find out that it displayed menus in core Gnome apps (Nautilus, Settings, the text editor, the log viewer, etc.) as small unreadable blobs. Here are a couple of screenshots of Nautilus to illustrate:

[IMG]https://i.imgur.com/z9d2nW0.png[/IMG]

[IMG]https://i.imgur.com/NTkWCAp.png[/IMG]

The worst glitch was in Setting's Appearance tab:

[IMG]https://i.imgur.com/wrdmyDw.png[/IMG]

This usually ended in a crash.

The prior version of Ubuntu (23.10) did not exhibit this behavior. I finally found a bug report on Gnome's GitLab page for GTK here, [https://gitlab.gnome.org/GNOME/gtk/-/issues/6654](https://gitlab.gnome.org/GNOME/gtk/-/issues/6654) that sounded very similar to my issue. It appears my old nVidia card and GTK4 don't get along. To be more specific, my card doesn't handle GTK4's renderer (called "ngl") well and I needed to set an environment variable to tell GTK to use another, older renderer such as "gl" or "cairo" instead. That done, the glitches went away. 

So if I set GSK_RENDERER=gl or GSK_RENDERER=cairo the menus appear as intended and the Appearance pane appears as intended.

(This is the first time a version of Ubuntu hasn't worked out of the box since I started using it with version 9.10. I think it's trying to send me a message about how old my graphics card is.)

Posted in the hope this helps someone.

---

