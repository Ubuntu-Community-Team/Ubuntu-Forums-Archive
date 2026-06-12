---
title: "Problem with the system font"
date: 2013-10-14
forum: General Help
---

### Post by Helvio_Vairinhos on 2013-10-14
Hi,

Recently I've had a rendering problem with the Desktop, which was solved here: [http://ubuntuforums.org/showthread.php?t=2180408](http://ubuntuforums.org/showthread.php?t=2180408)
However, another problem (which occurred soon after and might or might not be related) remains unsolved.
The system font is rendered badly, as you can see from the picture:

[ATTACH=CONFIG]246938[/ATTACH]

This issue shows up everywhere, from the terminal, to menus, to bookmark titles in the web browser. Everything else is functional.
Is there a way to revert this? I am waiting for the final release of 13.10 to see if this problem goes away, but it would be nice if I learned how to solve it.

Thanks,
Helvio

---

### Post by CatKiller on 2013-10-14
I've seen similar crazy wonky kerning when the font DPI setting is wrong; the font rendering tries to line the text up with the wrong grid. I believe the easiest way to fiddle with that is Gnome-Tweak.

---

### Post by Helvio_Vairinhos on 2013-10-14
Hi CatKiller, thanks for your reply. I've played with all the font options in the Gnome Tweak Tool, but none of them solved the problem. The bad kerning persists, it gets scaled up or down, with our without anti-aliasing, etc.

---

### Post by CatKiller on 2013-10-14
It's possible that the graphics driver is mis-reporting the DPI (that's what had happened when I experienced this). I see from your other thread that you're using Nvidia graphics; are you using the proprietary driver? Is there something there that you can see wrong?

EDIT: To clarify, when I experienced the problem nvidia-settings was reporting the DPI of my monitor as 100, when it should have been 96. Re-detecting the monitor did the trick in my case.

---

### Post by Helvio_Vairinhos on 2013-10-14
Yes, my graphic card is a GeForce GTX 460M and I am using the proprietary driver. The DPI reported in my nvidia-settings is 96, and redetecting the monitor changed nothing. Nothing seems to be wrong with it...

As an experiment, I reverted to the open source driver to see what happens, but then I lose resolution down to 1280x800 (it should be 1920x1080) and the font problem persists.

---

### Post by CatKiller on 2013-10-14
I'm out of sensible suggestions, I'm afraid.

Does the behaviour persist with different fonts?

---

### Post by Helvio_Vairinhos on 2013-10-14
Yes, the problem persists for any other choice of font in the option "Monospace Font". But I noticed the following: regardless of the font that I choose for the "Monospace Font" in Tweak Tool, the displayed font is the normal, bold and/or italic versions of a single font. In other words, the displayed font doesn't change when I select one at random.

But thanks anyway. I hope to find the solution soon, because it is really unpleasant to use the terminal like this.

---

### Post by CatKiller on 2013-10-14
OK, that's freaky. Probably related. I don't know enough about the font rendering system to know where to tackle that. It's safe to say that it's not working as it should.

---

