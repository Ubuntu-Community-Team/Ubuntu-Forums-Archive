---
title: "1024x768 resolution and lower is not filling screen"
date: 2013-03-24
forum: General Help
---

### Post by sandstorm75 on 2013-03-24
I've just recently installed xubuntu on my Dell latitude e6400.  In the highest resolution (1280x800) works perfectly, but when I reduce the resolution to 1024x768 or less, it kind of squishes the screen in so that it's square in shape, and there's about an inch of monitor on each side that remains unused. When I run a game or play a video in 800x600, everything is distorted so that the images are skinnier than they're supposed to be.  I have combed the internet and no one else seems to have this problem.  Since it works fine in 1280x800 I'm kinda at a loss at what could be wrong.  Any ideas?

---

### Post by sandstorm75 on 2013-03-25
ok well it's solved now... a wizard told me to type in the terminal
     xrandr --output LVDS1 --set "scaling mode" "Full"

It worked!
He told me not to reveal his identity, so fearing for my life I will comply :P

---

