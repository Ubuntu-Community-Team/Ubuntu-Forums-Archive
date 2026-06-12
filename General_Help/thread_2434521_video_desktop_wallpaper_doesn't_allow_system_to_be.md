---
title: "video desktop wallpaper doesn't allow system to become idle"
date: 2020-01-07
forum: General Help
---

### Post by ardouronerous on 2020-01-07
```
bash -c "sleep 1; mpv -loop-file=inf --no-audio --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/pcmanfm/ {print $1}') /path/to/video"
```

This is the code I'm using to run my video wallpaper at startup. Is there a way to modify the code to allow my system to become idle whilst my video desktop wallpaper continues to loop in the background?

Thanks.

---

### Post by Holger_Gehrke on 2020-01-07
mpv by default inhibits screen savers / blankers / lockers. You can tell it not to do so with the option '--no-stop-screensaver'.

Holger

---

### Post by ardouronerous on 2020-01-07
```
bash -c "sleep 1; mpv -loop-file=inf **--no-stop-screensaver** --no-audio --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/pcmanfm/ {print $1}') /path/to/video"
```

That worked thanks.

---

