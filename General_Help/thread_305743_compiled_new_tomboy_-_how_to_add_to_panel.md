---
title: "compiled new tomboy - how to add to panel?"
date: 2006-11-23
forum: General Help
---

### Post by futz on 2006-11-23
The basic Tomboy Notes in the repos is v0.3.5, I think. I wanted to run 0.5.1 so I compiled it. Now I want to replace 0.3.5 on my top panel, but I don't know how to.

I can get it there by adding the launcher to the panel, launching the program and then removing the launcher, but that's a stupid, clumsy way of doing it. Also this only works till the next reboot. Then I have to do it again.

So, how do ya replace old panel programs with new ones? Can't be too tough, right?

---

### Post by dcstar on 2006-11-23
> **futz said:**
> The basic Tomboy Notes in the repos is v0.3.5, I think. I wanted to run 0.5.1 so I compiled it. Now I want to replace 0.3.5 on my top panel, but I don't know how to.

I can get it there by adding the launcher to the panel, launching the program and then removing the launcher, but that's a stupid, clumsy way of doing it. Also this only works till the next reboot. Then I have to do it again.

So, how do ya replace old panel programs with new ones? Can't be too tough, right?

You should be able to just edit the Launcher properties of the existing panel icon to use the new settings - and you should not lose panel settings between reboots.

---

### Post by futz on 2006-11-23
> **dcstar said:**
> You should be able to just edit the Launcher properties of the existing panel icon to use the new settings - and you should not lose panel settings between reboots.
Well, if there is a way to do that, I missed it. I tinkered with everything I could think of. No go.

But I did find a solution, and it *was* easy. Here's the quote:
> 5.3. My applet isn't available in the menu Add To Panel.

When you compile and install an applet by hand, the applet is installed into /usr/local/ by default. Gnome looks for its panel applets in /usr. You can run ./configure --prefix=/usr to install your applet to the preferred location. You will also need to logout and log back in to Gnome for the applet to become available.

I recompiled with that option and it works perfect now. Just restarted to test. All cured! I'm running 0.5.1. :mrgreen: :mrgreen:

---

