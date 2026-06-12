---
title: "Problem with Chromium"
date: 2013-11-09
forum: General Help
---

### Post by mariodav9429 on 2013-11-09
I was just trying to install the pepper plugin in chromium because flash player lags sound and image.
As I am totally new in ubuntu and doing things on terminal I tried to install the plugin I maybe did some error and now chromium just wont open at all.

I even tried to remove chromium and install it again but it made no difference 
what can I do?


Edit: Maybe it could help that if you did the change from flash player to pepper, show to me images and specific examples about how you did it and maybe I can fix what i did

---

### Post by fantab on 2013-11-09
To remove Chromium use 'Synaptic package manager'.

```
sudo apt-get install synaptic
```

From Synaptic remove Chromium, when doing so use the option "*mark for complete removal*"
Also remove the .chromium (dotchromium) from your /home directory. dotfiles are hidden use CTRL+H to reveal them.
If you have installed Flash from Ubuntu repos then remove that as well. (I am not 100% sure that you need to remove Flash-plugin..).

Restart ubuntu.
Reinstall Chromium.

To install Pepper Flash read this: [http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

---

