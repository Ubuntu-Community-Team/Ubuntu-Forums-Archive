---
title: "reset unity desktop to all defaults"
date: 2016-08-12
forum: General Help
---

### Post by mgaeremynck on 2016-08-12
Hello,

Something wrong happened with my unity settings and I can't send a window to another work-space anymore with the right mouse button. 

I tried to reset Unity to standard configuration with:
```

dconf reset -f /org/compiz/
setsid unity

```
but this did a reset to default of most settings except for my right mouse click behavior.

Anybody an idea how I can reset unity completely to it's default values?

---

### Post by howefield on 2016-08-12
Sorry, stupid and basic question.. but have you switched workspaces off ?

---

### Post by mgaeremynck on 2016-08-12
Hello, no I still have my 4 work-spaces. I still can move my windows with keyboard shortcuts or move to other work-spaces. However, when I right click on a title bar, the window is minimized instead of having the application menu :-(

---

### Post by howefield on 2016-08-12
Do you have unity-tweak-tool installed ?

Try Window Manager > Additional > Titlebar Actions > Right Click and select the menu option.

---

### Post by mgaeremynck on 2016-08-14
Hello Howefield, 

Thanks for your help! Menu bars are back as they should :-)

---

### Post by howefield on 2016-08-14
Hello, glad to hear that you got it.

For info, the other way of getting there if you don't have/want unity-tweak-tool installed is to use dconf-editor and navigate to org > gnome > desktop > wm > preferences > action-right-click-titlebar and change to read 'menu' by pressing the Set to default button.

Please mark the thread as solved if you are happy to.

---

