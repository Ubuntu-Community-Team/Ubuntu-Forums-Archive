---
title: "[SOLVED] No S-Video signal to TV"
date: 2008-02-04
forum: General Help
---

### Post by The Avatar of Time on 2008-02-04
Hello, I have been trying to install Ubuntu Gutsy 7.10  as such:

Command line install the base system, then install xorg, fluxbox, fluxconf, irrelevant other apps, etc.

Now the trouble I have is that my NVidia 8600GTS video card has an s-video port that I use to hook up my TV as a dual monitor (which works fine with a full Ubuntu or Kubuntu install). 

However when only installing Fluxbox I get no signal at all to the TV (though fluxbox will work if installed with a full Ubuntu or Kubuntu install, and then selected at login). However having a login manager is not the issue, or at least not all of it as I have tried that with no success. I can get signal to a dual monitor with the other dvi port but not s-video. 

I have installed the driver for the video card with envy, restricted driver manager, and command line. So there is apparently some package/packages that KDE and GNOME bring in that Fluxbox doesn't. Also if I install kde-base from a command line install it also doesn't seem to have s-video support. 

I realize that I could just install KDE or GNOME and then Fluxbox and it would work just fine, however I am a fan of the minimalist install and since I have no intention of using KDE or GNOME I would rather not install them at all. I'm just odd that way. If any other information is needed just ask. Does anyone have any idea what I might be missing?:confused:

---

### Post by The Avatar of Time on 2008-02-04
Or does anyone know of a tool/app that would help me with this problem? Or a guide that I have missed somewhere? Any advice is really appreciated.

---

### Post by The Avatar of Time on 2008-02-04
I have figured out the problem that I had now. In the event that anyone else has the same trouble this worked for me:

sudo apt-get install nvidia-glx-new linux-restricted-modules 

Depending on your nvidia card you might need one of these commands instead:

nvidia-glx-legacy (corresponds to the 71xx driver)
nvidia-glx (which corresponds to the 96xx driver)
nvidia-glx-new (which at the time of writing corresponded to the 97xx driver)

Then to enable the driver (which is the step that I left out and apparently Envy doesn't do):

sudo nvidia-xconfig

To set up the dual monitor. (I have heard that kdesu or gksu is better than sudo for this though):

sudo nvidia-settings

And now I have a nice minimal install with a working tv on fluxbox.

---

