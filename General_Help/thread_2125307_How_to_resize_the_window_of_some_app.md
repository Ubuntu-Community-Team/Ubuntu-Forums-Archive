---
title: "How to resize the window of some app"
date: 2013-03-13
forum: General Help
---

### Post by Rebelli0us on 2013-03-13
I have a misbehaving app that creates a window that is larger than the screen. So I want to change the startup command, to start the app, wait for it to launch, then resize its window. For example:

guvcview
wmctrl -r GUVCVideo -e 0,600,0,640,512

Both commands work when run individually, but not as a single command line or script. Any ideas?

---

