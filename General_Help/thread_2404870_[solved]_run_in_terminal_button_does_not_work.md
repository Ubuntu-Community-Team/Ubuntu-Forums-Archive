---
title: "[solved] run in terminal button does not work"
date: 2018-10-29
forum: General Help
---

### Post by nozombian on 2018-10-29
Hello guys, I must have screwed something, so I can no longer run my .sh scripts from desktop. When I click onto whatever.sh, I get dialog Do you want to run "whatever.sh" or display its contents? And buttons. [Display] works (it opens as text in leafpad), but [Run in terminal] does not do anything. How can I reconfigure it so it will open in terminal? I'm using lubuntu with cinnamon de, filemanager is nemo. .sh files are marked executable. The problem is present since I deleted ~/.cache and ~/.thumbnails, but maybe I did yet something in the meanwhile. .cache and .thumbnails folders recreated itself.

Thank you!

edit: I managed to fix it using
```

sudo apt autoremove qterminal
sudo apt autoremove gnome-terminal
sudo apt install gnome-terminal
```

---

