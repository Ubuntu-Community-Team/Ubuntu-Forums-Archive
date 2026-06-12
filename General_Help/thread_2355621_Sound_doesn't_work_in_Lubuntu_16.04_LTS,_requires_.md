---
title: "Sound doesn't work in Lubuntu 16.04 LTS, requires PulseAudio"
date: 2017-03-14
forum: General Help
---

### Post by John_Patrick_Mason on 2017-03-14
What commands do I need to type in order to install PulseAudio?

I tried:

```
dpkg --list | grep -i pulsea 
```

and

```
apt-cache search PulseAudio
```

but I couldn't find the appropriate package(s).

---

### Post by ajgreeny on 2017-03-14
Replace the upper case P and A in pulseaudio, or add an * to pulsea, ie, pulsea* in the other command and you will see lots of packages listed from the two commands.

You're using a version of Ubuntu that does not already have pulseaudio installed as far as I can remember but ```
sudo apt install pulseaudio pavucontrol
``` should bring in everything needed for a start including any lib packages that are dependencies.

---

### Post by John_Patrick_Mason on 2017-03-14
I did what you said and typed in this command:

```
sudo apt install pulseaudio pavucontrol
```

then I restarted. The audio seems to work fine, but now I'm having another issue. Everytime I log in, it takes forever for the menu taskbar to show up. I'm also getting this error message now:

HPLIP Status Service
No system tray detected on this computer system.
Unable to start, exiting.

Does installing PulseAudio interfere with the menu taskbar in any shape or form?

---

### Post by ajgreeny on 2017-03-15
No, it doesn't, and HPLIP Status Service is the printer software GUI needed (or useful) if you have an HP printer and want the control software for that.  The package that would give you that is **hplip-gui** and to see the panel icon you need to ensure that system tray applet is added to your panel.  If you installed hplip direct from their website the GUI is included with the installation, but is separate if from the Ubuntu repos.

I'm not using Lubuntu so can not remember properly but I think you can do that with a right click in the panel.

---

