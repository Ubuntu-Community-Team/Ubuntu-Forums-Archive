---
title: "Moving window control buttons"
date: 2013-03-28
forum: General Help
---

### Post by Neil B. on 2013-03-28
I am trying to move my window control buttons to the right instead of the left. 

I have used gconf-editor to do so by going to apps -> metacity -> general and changing the button_layout value to menu:maximize,minimize,close

When I made the change, the control buttons move to the right side within google chrome, however, they did not move for other windows (terminal, gconf editor, etc). 

Did I do something wrong? Why would chromes controls but every other window not?
Also, I noticed there is a warning message in the button_layout dialogue that says "this key has no schema". Not sure if that has anything to do with it...

If there is a better way to accomplish this task, please let me know. Otherwise, let me know if Ive done something wrong. 

I have version 12.04
Thanks.

---

### Post by slickymaster on 2013-03-28
You can use [Ubuntu Tweak]("http://ubuntu-tweak.com/"), which has an easy GUI option to switch the window buttons to the right. It's found under the Windows Manager Settings option, under the Desktop category. Just select the "Right" radio button and you're done.

To install run these commands at a terminal:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

---

### Post by 3rdalbum on 2013-03-28
I think dconf-editor has superceded gconf-editor.

You'll get used to the buttons on the left side very quickly. Within a few days. I switch between Ubuntu 12.04 and Windows 7 every day and the different locations of the window buttons never trips me up.

---

### Post by stinkeye on 2013-03-28
Terminal commands for dconf.

Get current setting...
```
gsettings **get** org.gnome.desktop.wm.preferences button-layout
```

Buttons on right...
```
gsettings **set** org.gnome.desktop.wm.preferences button-layout menu:maximize,minimize,close
```

Reset to default (left)...
```
gsettings **reset** org.gnome.desktop.wm.preferences button-layout
```

---

