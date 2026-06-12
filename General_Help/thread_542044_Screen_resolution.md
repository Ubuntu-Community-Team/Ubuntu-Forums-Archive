---
title: "Screen resolution"
date: 2007-09-03
forum: General Help
---

### Post by Xenophoribic on 2007-09-03
I went out for the night, and shut down my computer. When I came back an hour ago, and turned it on, instead of the resolution being 1280x1024, it was 1024x768. I don't even have the option to use 1280 anymore, because it's no where to be found. Also, my max refresh rate showing up is 60, making even looking at the monitor physically painful. Any help is greatly appreciated.

---

### Post by Amazona aestiva on 2007-09-03
If Nvidia type:
```
sudo nvidia-settings
```
Choose "X server Display Configuration" then modify res to auto or other and click "Save to X Configuration File".

---

### Post by Tucatts on 2007-09-03
I have a nvidia card and this has always worked for me in Dapper. Have not had a screen resolutiion problem in Feisty YET! lol. Anyway, if you are still stuck you might try this:

Go to terminal and type in sudo dpkg-reconfigure xserver-xorg

follow the reconfig then manually choose 1280x1024 or whatever you are choosing. Hit the space bar when you have made your choice to select then just follow it out and restart x server. ctrl+alt+backspace to restart.
  If you have a ATI card then not sure what you can do other than doing a search on the forum. Good luck.

---

