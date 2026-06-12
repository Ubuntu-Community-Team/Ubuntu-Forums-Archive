---
title: "issue with Video Wallpaper"
date: 2019-11-29
forum: General Help
---

### Post by ardouronerous on 2019-11-29
[ATTACH=CONFIG]284513[/ATTACH]

Every time I scroll my mouse wheel to navigate through desktops, it would cause my video wallpaper to go back to 0:00. Is there anyway to remedy this?

Here's my code for my Video Wallpaper:

```
[Desktop Entry]
Version=1.1
Type=Application
Name=Video Wallpaper
Exec=bash -c "sleep 1; mpv -loop-file=inf --no-audio --osc=no --cursor-autohide=no --wid=$(wmctrl -l|awk '/pcmanfm/ {print $1}') path/to/video"
```

---

### Post by guiverc on 2019-11-29
I'd love to see your screen feature  on [https://discourse.lubuntu.me/t/screenshot-thread/221](https://discourse.lubuntu.me/t/screenshot-thread/221)  :)

I take it you're talking about Lubuntu 18.04?  (*I note what looks like LXDE and see mention of `pcmanfm`, I don't have any ideas, but have never tried a 'moving' wallpaper or use mouse to switch windows...*)

---

### Post by ardouronerous on 2019-11-29
Yeah, it's Lubuntu 18.04. I tend to stick to the LTS releases.

Thanks for the heads up for Lubuntu Discourse, just shared my desktop screenshot there.

---

