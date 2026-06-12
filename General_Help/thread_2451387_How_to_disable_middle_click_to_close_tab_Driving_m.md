---
title: "How to disable middle click to close tab? Driving me crazy"
date: 2020-10-03
forum: General Help
---

### Post by cforput on 2020-10-03
Ubuntu Mate 20.04
Acer Aspire F5-573G-56CG

When I click on a tab in Firefox, sometimes I accidentally use the center portion of my touchpad and it closes the tab. This is terribly annoying. I've looked through the mouse / touchpad settings and can't find anything that will disable this. Is there a way to do that? At one point, I thought I saw a setting that had something like this but I don't see it now. It could have been on a different version of Ubuntu since I've tried several lately. Just looking for a way to completely disable this annoying feature.

---

### Post by ajgreeny on 2020-10-03
See what the output os command ```
synclient -l
```shows you.  There is nothing that appears to relate to middle-click in my output using Xubuntu-20.04 but it may depend on the exact model of touchpad you use, both make and model.

Xubuntu mouse and touchpad settings allow "Tap to click" to be enabled/disabled completely, which may be what you saw previously.

---

### Post by TheFu on 2020-10-03
If the hardware supports it, you can configure 2-fnger and 3-finger clicking for right and center mouse buttons.

```
synclient AreaRightEdge=850 &
synclient AreaLeftEdge=50 &

synclient TapButton1=1 &
synclient TapButton2=3 &
synclient TapButton3=2 &
```

synclient has all sorts of settings.

---

### Post by coreyaw1 on 2021-05-22
I am having the same issue. I used the xinput command to change it and it seemed to fix it but it looks like either an update or something else has reenabled it. Is there a good way to make these changes permanent? Same as the OP this is incredibly frustrating when you are trying to click on a tab that you have work on and it closes it instead. There is no circumstance where I will ever want to use that feature.

[https://askubuntu.com/questions/597064/disabling-middle-mouse-button](https://askubuntu.com/questions/597064/disabling-middle-mouse-button)

---

