---
title: "gnome-terminal stretched background"
date: 2013-09-19
forum: General Help
---

### Post by eugene5 on 2013-09-19
Hello,

i made a small script to change gnome-terminal background image... But faced in with the problem - i cant find a way to stretch image or even better to keep image fit the terminal window when i resize the terminal ...

```

#! /bin/bash

files=(/dir/to/Wallpapers/*)
gconftool-2 --set /apps/gnome-terminal/profiles/Default/background_image --type=string $(printf "%s\n" "${files[RANDOM % ${#files[@]}]}")

```

i cant find any key inside "/apps/gnome-terminal/profiles/Default/" which is responsible for the image display mode like "tile" "stretch" etc.

any advices ? (better with the samples)

thanks.

---

