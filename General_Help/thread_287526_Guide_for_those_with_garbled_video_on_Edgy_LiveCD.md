---
title: "Guide for those with garbled video on Edgy LiveCD"
date: 2006-10-28
forum: General Help
---

### Post by DeathOnJuice on 2006-10-28
On NVidia cards, many people have problems on the Edgy LiveCD. When the GUI boots up, the screen is very garbled. I just had the same problem and could get little support here, so I figured it out on my own.

First, use the alternative install CD which you can download in the same place you get the regular CD. Use the text-based install. This should get the OS installed.

Still, when you try to log in, it will give you the garbled screen. Don't log in yet; instead, hold control and alt and press F1. If this gives you a scrambled screen, reboot and select "Recovery Mode" from the bootloader. Log in in this terminal. Then, type:

Code:

sudo nano /etc/X11/xorg.conf

Scroll down to where it says "Section" "Device". Where it says Driver "nv", change the nv to vesa. Then, hold control and press O then press enter (to save changed) and press control-x (to exit nano).

Now, type this:

Code:

sudo /etc/init.d/gdm restart

You can now login every time without a hassle. However, performance will be very, very bad (it takes a few seconds to scroll down in Firefox). So, we need to install a driver. I have only done this with an NVIDIA card, so MAKE SURE YOU ONLY DO THIS WITH AN NVIDIA CARD. The instructions are here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Also, in addition to these instructions, there is a security hole in the NVidia drivers, unless you're using the beta release. It can compromise your system or (more likely) just restart the X server while you're using Firefox. To fix it, open a terminal and enter:

```

sudo gedit /etc/X11/xorg.conf

```

In the Device section, above the line that says Driver "nvidia" (if you followed the instructions), add this line:

```

Option "RenderAccel" "false"

```

Then log out and press control-alt-backspace. That's it! There may be a very slight performance hit.

Enjoy your Edgy-working goodness! If you need help with anything, whether I posted it or it's in the guide, just ask. I'll monitor this topic for a while.

---

### Post by ramiro on 2006-10-28
actually you don't need to download a completely different cd

when you get the garbled screen just hit ctrl-alt-f1 to get to a console. it should be logged in automatically

then type sudo nano /etc/X11/xorg.conf and follow the instructions of the above post. When you restart gdm, it should be working and you can install.

once that's done your installed version should also be using the vesa drivers, I recommend you upgrade to the nvidia drivers straight away

---

### Post by DeathOnJuice on 2006-10-28
ramiro, I tried that, but there were some problems. First, as soon as the garbled screen shows up, it crashes. You have to mash control-alt-F1 until the terminal pops up. Second, gdm refuses to restart on the LiveCD, at least for me.

---

### Post by scotty2hott2k on 2006-10-29
ive tried this before, however even the terminal screen is garbled for me so i cant even see what im typing in, let alone edit the xconfig.

---

### Post by DeathOnJuice on 2006-10-29
Hmm, our problems must be slightly different. What graphics card do you have?

---

### Post by scotty2hott2k on 2006-10-30
nvidia gainward 512mb 6800gs (agp)

---

### Post by DeathOnJuice on 2006-11-02
I added a fix to the guide! Sorry it took so long. If you get a scrambled screen while in the terminal, reboot and choose recovery mode from the bootloader.

---

### Post by didobuntu on 2006-11-21
Just an info.

This problem not only happens to nvidia cards. It is also present for ATI cards like mine (an ATI Mobility Radeon X1600).

---

