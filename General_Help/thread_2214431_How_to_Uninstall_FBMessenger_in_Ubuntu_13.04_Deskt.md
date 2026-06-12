---
title: "How to Uninstall FBMessenger in Ubuntu 13.04 Desktop 64Bit"
date: 2014-04-01
forum: General Help
---

### Post by awfordjr on 2014-04-01
Hello,

I need help to remove FBMessenger as it popped up when I was going to facebook & I clicked it by mistake. I have looked in the Ubuntu Software Center but did not find it there to uninstall. Can someone tell me what command line I can use in terminal to get rid of it, or how I need to go about uninstalling it?

Thank you!

---

### Post by slickymaster on 2014-04-01
Hi [COLOR=#000000]awfordjr, welcome to the forums.
[/COLOR]
To uninstall unity-webapps-facebookmessenger and its dependencies, purging your config/data too, open a terminal window and run the following:```
sudo apt-get purge --auto-remove unity-webapps-facebookmessenger
```

---

### Post by awfordjr on 2014-04-01
It is gone but still shows up as on my computer. In any case that helped do what I needed it to do so thank you very much!

---

### Post by slickymaster on 2014-04-01
> **awfordjr said:**
> It is gone but still shows up as on my computer. In any case that helped do what I needed it to do so thank you very much!

Apparently it didn't delete the icons. So you just need to go to **~/.local/share/applications** and delete the file _facebookfacebookcom.desktop_

---

### Post by awfordjr on 2014-04-01
[IMG]http://i57.tinypic.com/20sgaqu.jpg[/IMG]

It shows up here but when I go to the directory location you have indicated there is nothing there for FaceBook. I don't know why but it still shows up in the menu, but nothing in that folder.

---

### Post by su:bhatta on 2014-04-01
Didn't 13.04  reach EOL  a couple of months back?
Yes: [http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/](http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/)

awfordjr, you have to upgrade to 13.10. 
Ubuntu 13.04 reached end of life (not supported via security updates/updates since January 2014.)

---

### Post by slickymaster on 2014-04-02
> **awfordjr said:**
> 
It shows up here but when I go to the directory location you have indicated there is nothing there for FaceBook. I don't know why but it still shows up in the menu, but nothing in that folder.

_Do this:_
[LIST=1]
[*]Open the file manager
[*]Click View > Show Hidden Files (alternatively CTRL + H)
[*]Navigate to **~/.local/share/applications** and delete the file _facebookfacebookcom.desktop_
[/LIST]

---

