---
title: "Trying to get wider scrollbars"
date: 2017-08-04
forum: General Help
---

### Post by hatetech on 2017-08-04
16.04 Mate, rx480 video card. I've been trying to find a way to increase  the width of all scrollbars, but nothing  works. I saw something about editing  scrollbar width in the gtk3.0 css, but that only seemed to work on Chrome. It's stupid. Chrome abides by the  setting, but nothing else does (Firefox, Thunderbird, Hexchat,  qBittorrent, gFTP, etc). All this jumping through hoops to get things to look right on a 4K screen is really irritating. The icons for everything are too small, and the open dialogs on everything are too small to read anything since I cranked the fonts/DPI up. Not ot mention the fact that checkboxes/radio buttons on websites are ridiculously tiny now.

/home/username/.config/gtk-3.0/gtk.css". Like I said, it seemed to work, but only in Chrome. 
```


  .scrollbar {
  -GtkScrollbar-has-backward-stepper: true;
  -GtkScrollbar-has-forward-stepper: true;
  -GtkRange-slider-width: 20;
  -GtkRange-stepper-size: 20;
} 

```

---

