---
title: "Marble Mouse again"
date: 2020-10-05
forum: General Help
---

### Post by phillip2 on 2020-10-05
As it traditional on upgrading my ubuntu to 20.04 my Logitech Marble Mouse set up has broken again.

I have been using this for three or four runs, just running as a shell script on login

```

xinput --set-prop "Logitech USB Trackball" "libinput Scroll Method Enabled" 0 0 1

xinput --set-prop "Logitech USB Trackball" "libinput Button Scrolling Button" 8

```


But this seems to fail in 20.04, with no scroll wheel emulation.

Anyone got any thoughts?

---

