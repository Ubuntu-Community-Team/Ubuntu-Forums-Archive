---
title: "Ubuntu 14.04 customising applets"
date: 2014-05-18
forum: General Help
---

### Post by CaptainMark on 2014-05-18
Can it be done?

I want to hide the networking applet and the keyboard/language one, they are both IMO useless for a wired in desktop with only english users.  Also the hideous applet that chromium shows when you allow it to run in the background, I want to hide that but without stopping chromiums background processes.

Thanks for any assistance

Regards
Mark

---

### Post by westie457 on 2014-05-18
The keyboard/language applet is easy to hide.
System Settings > Text Entry. At the bottom of the window uncheck the box 'Show current input source in the menu bar'.

No idea how to hide Network icon.
Have never seen the Chromium applet - mainly because I have never run Chromium in the background.

---

### Post by CaptainMark on 2014-05-18
Thanks for that one. The chromium applet only appears if you allow it within chromiums own settings, which is great because hangouts stays connected all the time but you get the fugly icon then

---

### Post by vasa1 on 2014-05-18
> **CaptainMark said:**
> Thanks for that one. The chromium applet only appears if you allow it within chromiums own settings, which is great because hangouts stays connected all the time but you get the fugly icon then
With a little searching (and trial and error) you maybe able to find where that icon for that applet is located on your system and replace it with something more pleasing to you. I do that a lot.

---

### Post by deadflowr on 2014-05-18
You should be able to hide the network applet in dconf-editor
in dconf go to org > gnome > nm-applet > show-applet > uncheck it.
or try 
```
gsettings set org.gnome.nm-applet show-applet false
```

I would think the chromium applet can be set in chromium's preferences, somewhere.

---

