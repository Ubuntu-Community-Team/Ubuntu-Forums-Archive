---
title: "how do I make this video into a wallpaper in Xubuntu?"
date: 2020-11-05
forum: General Help
---

### Post by ardouronerous on 2020-11-05
In Lubuntu 18.04, I used this video as my wallpaper: [https://www.youtube.com/watch?v=gpueugXDTBg](https://www.youtube.com/watch?v=gpueugXDTBg)

And here's the code that I used in Lubuntu:

```
bash -c "sleep 1; mpv -loop-file=inf --no-stop-screensaver --no-audio --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/pcmanfm/ {print $1}') 'path/to/video.mp4'"
```

Is there a way to do this in Xubuntu?

Thanks.

---

### Post by Holger_Gehrke on 2020-11-06
Works just the same, you only have to change the name of the window awk should search for from 'pcmanfm' to the name of the desktop-window. This name probably depends on your locale, on my system with German locale it's named 'Schreibtisch' so it's probably 'Desktop' for systems with some variant of English. And if you have any icons on the desktop those will not be visible or useable while that video is running.

Holger

---

### Post by ardouronerous on 2020-11-06
Any ideas on how I can get the name of the desktop window on Xubuntu?

---

### Post by ardouronerous on 2020-11-06
> **Holger_Gehrke said:**
> Works just the same, you only have to change the name of the window awk should search for from 'pcmanfm' to the name of the desktop-window. This name probably depends on your locale, on my system with German locale it's named 'Schreibtisch' so it's probably 'Desktop' for systems with some variant of English. And if you have any icons on the desktop those will not be visible or useable while that video is running.

Holger

This is the result when I tried to execute the command:

```
bash -c "mpv -loop-file=inf --no-stop-screensaver --no-audio --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/xfce4-desktop/ {print $1}') 'path/to/video.mp4'"
Error parsing option wid (option requires parameter)
Setting commandline option --wid= failed.

Exiting... (Fatal error)
```

Not even sure if *xfce4-desktop* is correct.

---

### Post by Holger_Gehrke on 2020-11-06
Just execute 'wmctrl -l' in a terminal. This shows a list of all open windows with four columns separated by spaces (window-id, number of the desktop the window is on, hostname, window title). The title to search for with awk should be obvious from the list.

Holger

---

### Post by ardouronerous on 2020-11-06
> **Holger_Gehrke said:**
> Just execute 'wmctrl -l' in a terminal. This shows a list of all open windows with four columns separated by spaces (window-id, number of the desktop the window is on, hostname, window title). The title to search for with awk should be obvious from the list.

Holger

Thanks that worked.

I created this executable and placed it in autostart.

```
[Desktop Entry]
Version=1.1
Type=Application
Name=Video Wallpaper
Comment=Start video wallpaper
Exec=bash -c "sleep 1; mpv -loop-file=inf --no-stop-screensaver --no-audio --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') 'path/to/video.mp4'"
```

Thanks again.

---

### Post by ardouronerous on 2020-11-06
Looks like I spoke too soon, when I restarted my system, the video background didn't autostart.

---

### Post by ardouronerous on 2020-11-07
UPDATE: Finally figured out the problem, although, I don't understand why it created such a problem in the first place.

Apparently, it was conflicting with another startup program that I created:

```
[Desktop Entry]
Version=1.1
Type=Application
Name=Flatpak Updater
Comment=Show and install available flatpak updates
Icon=flatpak
Exec=sh -c "sleep 1 && gnome-terminal -t 'Flatpak Updater' -e 'flatpak update'"
Categories=Settings;System;
```

So, I did this:

```
[Desktop Entry]
Version=1.1
Type=Application
Name=Video Wallpaper
Comment=Start video wallpaper
Icon=video-wallpaper
Exec=bash -c "sleep 2; mpv -loop-file=inf --no-stop-screensaver --no-audio --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/Desktop/ {print $1}') 'path/to/video.mp4'"
Categories=DesktopSettings;GTK;Settings;
```

---

