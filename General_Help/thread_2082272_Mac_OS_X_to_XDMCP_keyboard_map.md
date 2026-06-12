---
title: "Mac OS X to XDMCP keyboard map"
date: 2012-11-08
forum: General Help
---

### Post by noorez on 2012-11-08
I am currently testing the ability to connect my Mac OS X to my linux installation via XDMCP. I already have XDMCP setup and am able to connect XQuartz to XDMCP with 
```

'XQuartz -query 192.168.56.2 -once'. 

```

However, the keymap is completely wrong... I have already searched on google quite a bit finding that many people have this problem without a working solution...

---

### Post by noorez on 2012-11-09
(bump).

I tried using this guide but it did not work...

[http://www.cognitive-antics.net/mw/index.php?title=Linux_on_the_OS_X_desktop](http://www.cognitive-antics.net/mw/index.php?title=Linux_on_the_OS_X_desktop)

'''
The keyboard problem is more serious, and when I first started searching for a fix I found plenty of conflicting advice about it. Eventually I gave up on searching, and played around with gconf-editor until I found something that worked.

Select /apps/gnome_settings_daemon/plugins/keyboard and uncheck active. Do the same for a11y-keyboard. This will configure gnome to leave the keymap alone. Exit your gnome session on the virtual machine and try starting it again via ssh. If all is well, the keyboard should function properly.
'''

---

### Post by jes-13 on 2012-12-27
> **noorez said:**
> (bump).
The keyboard problem is more serious, and when I first started searching for a fix I found plenty of conflicting advice about it. Eventually I gave up on searching, and played around with gconf-editor until I found something that worked.

Select /apps/gnome_settings_daemon/plugins/keyboard and uncheck active. Do the same for a11y-keyboard. This will configure gnome to leave the keymap alone. Exit your gnome session on the virtual machine and try starting it again via ssh. If all is well, the keyboard should function properly.
'''

excellent, works for me too. Thanks for sharing the solution.

---

