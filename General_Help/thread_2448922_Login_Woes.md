---
title: "Login Woes"
date: 2020-08-16
forum: General Help
---

### Post by gerj52 on 2020-08-16
I'm new to Ubuntu and hope some one out there can help me.
I installed Ubuntu 20.04 and all was going pretty good then I thought I'd try the xfce and kde desktops.
Wasn't grabbed by either of them so want to return to original LTS but with no joy, when I tried uninstalling both the xfce and kde desktops the terminal reports there are no such files.
Now, my real problem is this ... every time I start my computer I am faced with an on screen keyboard and I have to enter my password.
It doesn't accept my wireless keyboard to enter my password I HAVE to use the on screen one.
I tried turning on automatic login but it keeps turning off again and forcing me to use the on screen keyboard to enter password.
SOMEONE HELP PLEASE while I still have some hair left!

Thanks in advance

---

### Post by crip720 on 2020-08-16
Would google proper command to remove each desktop, might have missed something and terminal too nice to tell we are stupid making a typo.  For your keyboard, try installing 'xserver-xorg-input-all', might have better luck than I with kernel update.

---

### Post by TheFu on 2020-08-16
Can't help with this specific problem besides to suggest always using a different userid/login with testing different, but related DEs.  KDE is sorta on it's own, so the configs shouldn't conflict, but all the others are usually based on Gnome2 or Gnome3 and use the same config files.  These may not be compatible between releases of the same DE software, much less when we use XFCE or Mate or Cinnamon or Gnome3 or any of the others.
There are other ways to accomplish similar things, but creating a new userid for each is usually the safest when shopping around for a DE.

BTW, you don't actually need to use any DE if you don't want.  GUI software is layers on layers on layers, with the DE being the last, top, layer before addons for that DE come into play.  Below the DE is something called a Window Manager, WM, for short. Some DEs are tied to specific WMs, but most are not.  There are standards for how and what a WM should handle - for example, the border, title, buttons around each window is controlled by the WM, not any DE. Many WMs also control management of the different virtual desktops and backgrounds for each.

In general, I use either **openbox** or **fvwm**. These are both lite WMs compared to the commonly used, bloated, WMs for Gnome3.  Openbox is the WM used under Ubuntu-Mate.  Fvwm has been around since the mid-1990s and can make for beautiful, custom, desktops.  Fvwm is probably what all the newer StarTrek computer screens used. It allows control over every detail of the Windows - fonts, colors, thickness for borders, sliders, titles, button placement, window transparency and it is still small and fast since it was created to work on 16MB computers.

If you don't want a GUI login screen, then you don't need to have one.  We logged into a console, then ran **startx** for over a decade. It works and it is nice as a fallback.  There are usually 8 "consoles" on a PC.  Switch between them using <cntl><alt>-F1 .... F8.  On my systems, <cntl><alt>-F7 is the X11 "console."  When the GUI locks up or mouse stops working, try changing to a different console, logging in, and seeing what is happening from there.  Usually, you'll see that wayland or xorg is using 900% of the CPU. Killing that process will recover the system to working. Just switch back to the F7 console, login, and get back to work. This doesn't happen very often, usually only when there is some other, not-yet-discovered, root problem on the system.

There is good news about fvwm.  It doesn't share any config files with any other WM or DE.  People like to apply different themes to fvwm enough that **fvwm-crystal** is in the repos. It looks best at resolutions above 1080p. Below that and the title bars seem huge. The config files inherit settings from the top "widget" down, which is hard for normal people to understand.

If your wireless keyboard uses a USB dongle, then it shouldn't matter. If it is tied to bluetooth, problem, since BT drivers aren't loaded until after you login in some situations. Connect a USB keyboard to get around that.  I have a $15 RF "gamer" hand-held keyboard to enter login data, but then use my normal keyboard.

This can seem overwhelming, but either you'll get used to thinking through how things really work, or have an easier head to groom. ;)

---

