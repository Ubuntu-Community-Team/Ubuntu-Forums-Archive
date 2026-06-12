---
title: "autokey: how to select an item by a hotkey in a context menu"
date: 2018-01-14
forum: General Help
---

### Post by apollochan on 2018-01-14
I try to call the context menu in Firefox and save image: 

```
mouse.click_relative_self(0, 0, 3)
time.sleep(1)
keyboard.send_keys("&#1086;")
```

("&#1086;" is Russian hotkey for "Save Image as" item in Firefox context menu)

Context menu is brought up, and no further action is performed, send_key() variant doesn't work too.

What have I missed?

Thank you in advance.

---

### Post by vasa1 on 2018-01-14
So this is when you right-click on an image in a web page?

---

### Post by vasa1 on 2018-01-14
Try```
sleep 10s && xdotool click 3 && xdotool mousemove_relative --sync 25 100 && sleep 1s && xdotool click 1
```where you may need to change *100* (and possibly *25*) to suit your screen. Once you've got things going, you can remove the first sleep and remove the second sleep if the code works without it.

If you don't have *xdotool* get it from the repos.

---

