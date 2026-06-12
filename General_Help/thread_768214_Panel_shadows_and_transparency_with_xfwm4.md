---
title: "Panel shadows and transparency with xfwm4"
date: 2008-04-26
forum: General Help
---

### Post by Zacharias Knudsen on 2008-04-26
Hi people,

I've finaly gotten Xubuntu running on my shitty laptop. Couldn't boot from usb nor the dvd drive (it's too unstable, I could only get about half-way, sometimes more). I ended up doing a netboot and installing that way.

So that's good, however I'm currently trying to make a neat looking interface and I have a few specific customizations that I'm having trouble implementing.

Sadly I can't use Compiz since my laptop is running on some ATI Rage chip for which I cannot find any drivers. So I'm stuck with xfwm4 (which is fine, actually, since it seems to be pretty fast).

[LIST=1]
[*]What I want to do (with xfwm4), is have my panels drop shadows. I know this was possible (I even believe it was forced), in older versions of xfwm.
[*]I've turned on the compositor and made my panels sligthly transparent, however, this also affects the icons on the panel, is it possible to keep the text and icons opaque?
[*]I'd also like to have the drop-down menus from the panel be transparent, is this possible?
[/LIST]

That's it. Is this doable in Xubuntu?

---

### Post by dbbolton on 2008-04-26
> **Zacharias Knudsen said:**
> Hi people,

I've finaly gotten Xubuntu running on my shitty laptop. Couldn't boot from usb nor the dvd drive (it's too unstable, I could only get about half-way, sometimes more). I ended up doing a netboot and installing that way.

So that's good, however I'm currently trying to make a neat looking interface and I have a few specific customizations that I'm having trouble implementing.

Sadly I can't use Compiz since my laptop is running on some ATI Rage chip for which I cannot find any drivers. So I'm stuck with xfwm4 (which is fine, actually, since it seems to be pretty fast).

[LIST=1]
[*]What I want to do (with xfwm4), is have my panels drop shadows. I know this was possible (I even believe it was forced), in older versions of xfwm.
[*]I've turned on the compositor and made my panels sligthly transparent, however, this also affects the icons on the panel, is it possible to keep the text and icons opaque?
[*]I'd also like to have the drop-down menus from the panel be transparent, is this possible?
[/LIST]

That's it. Is this doable in Xubuntu?
1. You can turn on shadows by going to Settings > Window Manager Tweaks > Compositor. However, this will put shadows under panels and windows.

2. As far as I know, this is not possible with xfce-panel. It is possible with gnome-panel, pypanel, and kicker.

3. You can enable transparency with the compositor, but like shadows, it will apply to all window types.


As an alternative, you might try using xcompmgr for a compositor.

---

### Post by Zacharias Knudsen on 2008-04-26
> **dbbolton said:**
> 1. You can turn on shadows by going to Settings > Window Manager Tweaks > Compositor. However, this will put shadows under panels and windows.

2. As far as I know, this is not possible with xfce-panel. It is possible with gnome-panel, pypanel, and kicker.

3. You can enable transparency with the compositor, but like shadows, it will apply to all window types.


As an alternative, you might try using xcompmgr for a compositor.

1. This only works for windows and dropdowns, I don't see any option to turn it on for panels.

2. Can I use one of those without slowing my system noticably?

3. Works like a charm. :)

---

### Post by dbbolton on 2008-04-26
> **Zacharias Knudsen said:**
> 1. This only works for windows and dropdowns, I don't see any option to turn it on for panels.

2. Can I use one of those without slowing my system noticably?

3. Works like a charm. :)
1. Hmm, I thought it applied to all windows but I suppose not. You could disable shadows in the Compositor, keep the transparency, then use xcompmgr to set your shadows. Here is a guide: [http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527)

2. gnome-panel uses about 10MB of memory, so I doubt it would make a big difference. You'll probably have to install a lot of dependencies though, so unless you have very limited hard disk space it should be fine to use.

---

### Post by Zacharias Knudsen on 2008-04-26
Thanks man. :)

---

### Post by dbbolton on 2008-04-26
Quite welcome

---

