---
title: "Xinerama - Nothing works any more."
date: 2006-11-15
forum: General Help
---

### Post by charlie. on 2006-11-15
I've setup two screens on one card in my xorg.conf, following the instructions linked to below:

[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-p.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-p.html)

I've done this because my two monitors both run at different resolutions. Everything works fine, but there is no way to move a window from one screen to the other.

When I enable Xinerama in my xorg.conf file, by adding...

Section "ServerFlags"
     Option          "Xinerama"    "true"
EndSection

... and restarting, applications break down. Both screens come back up at their correct resolutions, the mouse moves between them and does not fall into an area that does not display on either monitor (as it did when using nVidia's Xinerama-compatible extensions, presumably because the resolutions do not match) but many applications just don't work. For example, the console won't open in Gnome. I click the button and the cursor changes to a "busy" cursor, but nothing happens.

apt says that "libxinerama1" is at the newest version.

I don't want to have to go back to the nVidia Xinerama-compatible extensions - they don't seem to work nicely if your screens are not the same size.

Please help.

---

### Post by insub2 on 2006-11-16
you might try searching synaptic for "Xinerama" and installing anything that looks like it might help......maybe x11proto-xinerama-dev.....
but i have no idea, i'm having troubles with Xinerama myself.

---

### Post by charlie. on 2006-11-16
The package you mentioned is a development package - it's needed to compile apps that use Xinerama, not to run them.

I've done this already, most of the packages that look promising are "already at the newest version."

---

### Post by charlie. on 2006-11-16
[Bug #58232]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232") describes my problem: gnome-terminal will not work when xinerama is enabled and nvidia-glx drivers are used. They also give a fix - disable composite extensions...

```

Section "Extensions"
    Option	   "Composite"  "false"
EndSection

```

... which worked for me. I don't know what the composite extensions actually do, so I don't know what I'm losing here. I disabled them anyway.

I'm going to try two more things. Firstly, I'm going to try nVidias xinerama-compatible extensions again, to see if I can get them to work nicely. If they still behave as they used to, I'm going to try to manually upgrade my nVidia drivers to the latest version to see if that fixes the problem with the composite extensions. (I saw a guide to doing that on Edgy, I wish I could remember where it was...)

Any input would be nice. Thanks.

---

