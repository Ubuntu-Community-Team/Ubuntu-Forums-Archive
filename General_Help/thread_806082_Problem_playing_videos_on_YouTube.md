---
title: "Problem playing videos on YouTube"
date: 2008-05-24
forum: General Help
---

### Post by MicroBoy on 2008-05-24
**When I open a video first I have to click a play button then the video will play. Since I installed the Ubuntu 8.04 and I installed a plugin or something else I don't know what this thing shows to me.**

[IMG]http://img371.imageshack.us/img371/4727/screenshotne8.png[/IMG]

---

### Post by TeoBigusGeekus on 2008-05-24
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by akbob on 2008-06-01
> **TeoBigusGeekus said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

Didn't work for me.  Anyone have any other suggestions?

---

### Post by Lord Xeb on 2008-06-01
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by akbob on 2008-06-01
Thanks that didn't work until I removed gnash completly.  Don't know if it was a conflict or not.

---

### Post by ShinHadoken on 2008-06-01
Well, I would just trash Firefox and reinstall, but that's the more barbaric approach. Look in your addons list to make sure it isn't an addon, then go into Tools > Add-ons > Plugins and look for anything that could be causing a problem. Hope this helps! :D

---

