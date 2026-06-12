---
title: "USB Mouse Problem"
date: 2007-04-29
forum: General Help
---

### Post by Ajjw on 2007-04-29
When I boot up Ubuntu, my USB mouse stops working, I have to unplug it and plug it back in, then it works.

My mouse is a Razer Copperhead. I am using Feisty Fawn 64 bit. Mouse is working no problem under Vista on same machine.

How do I fix this problem? I am new to Ubuntu.

Thanks.

---

### Post by teachop on 2007-04-29
I am Ubuntu-new too, and have a similar glitch.  I have tried two mice, a Logitech optical (corded) and an Apple mighty.  Both of these work glitch-free on the Mac, but on my Acer Aspire 3100 under Feisty, they quit randomly.  I unplug / replug the usb connection and it works again.  Someone posted about backing out of the restricted video driver to the "ati" driver to fix it, but no go.

After the mouse quits, I can still use the touchpad in the laptop.  I was wondering if there was any system log output that would help us to troubleshoot this issue.

---

### Post by thread on 2007-05-08
I have the same issue. When I boot up, the mouse is lit up, but it doesn't work in X. As soon as I unplug it and reinsert, it works. What's up with that!?

I, too, am running Feisty (happened with Edgy as well) on AMD64 with a Razer Copperhead mouse.

---

### Post by justin_guerin on 2007-05-08
> **teachop said:**
> I am Ubuntu-new too, and have a similar glitch.  I have tried two mice, a Logitech optical (corded) and an Apple mighty.  Both of these work glitch-free on the Mac, but on my Acer Aspire 3100 under Feisty, they quit randomly.  I unplug / replug the usb connection and it works again.  Someone posted about backing out of the restricted video driver to the "ati" driver to fix it, but no go.

After the mouse quits, I can still use the touchpad in the laptop.  I was wondering if there was any system log output that would help us to troubleshoot this issue.

There should be something in the Xorg log file.  It should be in /var/log/.

Also, check your mouse configuration in /etc/xorg.conf (or whatever the X config file is called as I don't have it in front of me).  Make sure the driver you're using is appropriate for your hardware  (i.e. don't use the ps2 driver for a usb mouse, etc.).

Hope that helps,
Justin

---

### Post by CocoAUS on 2007-05-09
My sister has the same problem with hers.  My IntelliMouse has that problem *sometimes* (like twice total).  Anyway, from all of us having the same problem, it definitely seems to be an Ubuntu problem.  I can tell you it doesn't happen with Fedora.

---

### Post by thread on 2007-05-09
Bogus... I guess there's a real problem with this, then.... any experts?

---

### Post by titus1950 on 2007-05-09
Read this .......
[http://ubuntuforums.org/showthread.php?t=414152&page=2&highlight=mouse](http://ubuntuforums.org/showthread.php?t=414152&page=2&highlight=mouse)

---

### Post by thread on 2007-05-09
Thanks for the reply titus... Unfortunately, "acpi=force irqpoll" didn't seem to make any difference.

My keyboard is ps2, so that's not an issue, but my Razer Copperhead USB mouse doesn't move the cursor on the screen until I unplug it and plug it back in.

What to do.......

---

### Post by Crafty Kisses on 2007-05-09
> **thread said:**
> Thanks for the reply titus... Unfortunately, "acpi=force irqpoll" didn't seem to make any difference.

My keyboard is ps2, so that's not an issue, but my Razer Copperhead USB mouse doesn't move the cursor on the screen until I unplug it and plug it back in.

What to do.......

Hmmm, I would of though "acpi=force irqpoll" would of done it. This sucks, I'll work on it and let you know man.

---

### Post by thread on 2007-05-10
I've found a number of other threads regarding this issue. It seems related to my scenario: Razer Copperhead mouse on AMD64. No working solutions yet...

Yeah ok I guess I'm just bumping this thread.

---

### Post by Galactix on 2007-05-11
I had some similar problems with Edgy, and hoped Feisty would solve the problem. Feisty only worsened it, after replugging the mouse the entire USB subsystem locks up (including my G15 keyboard, iPod and other USB things).

Turning off Legacy USB support in BIOS solved my problem.

But this meant no keyboard in grub, so no switching to a different OS, unless I changed the settings in BIOS...

acpi=force irqpoll

Did (so it seems) solve my problem. The BIOS solution should work, as you use a PS2 keyboard.

---

