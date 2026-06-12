---
title: "Can I customize each desktop background and widget separately on diff. workspace?"
date: 2008-06-01
forum: General Help
---

### Post by D.Sync on 2008-06-01
As the title stated, Can I customize each desktop background and widget separately on diff. workspace? 

If possible, what should I do in order for them to boot as the aforementioned customization for each workspace?

Thanks for all your answer.:)

---

### Post by Forlong on 2008-06-02
In case you are using Compiz on GNOME, you can stop Nautilus from drawing your desktop, then you will able to use Compiz' own background settings:```

gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false
```

However then you will be left without desktop icons and you'll lose the ability to right-click your desktop and access the usual context menu.


What are you referring to, when saying "widget"?

---

### Post by D.Sync on 2008-06-02
Screenlets are one of them.

---

### Post by klange on 2008-06-02
For Screenlets and any other widgets you may have, just set them to not appear on all desktops (make them not sticky). You may need to use some fancy placing methods to get them to start on the right workspace, but it's definitely doable.

---

### Post by D.Sync on 2008-06-02
But how can I make them placed in the right workspace. If I placed them, say  in 4 diff. workspace. The next time I restart my comp. and they'll just show up in 1 workspace. All jumbled up of course.

---

### Post by Forlong on 2008-06-02
As a matter of fact, Screenlets should start on the same viewport on their own. The geometry gets saved in a config file and as long as you don't switch Compiz off, they "memorize" their position.

When you do switch Compiz off on occasions, you can use Compiz' Place plugin to let them start on a specific viewport.

---

### Post by D.Sync on 2008-06-02
I see. I will try that later.

---

### Post by Forlong on 2008-06-02
Just come back if you have any problems with the Place plugin. :)

This may also be of help: [http://wiki.compiz-fusion.org/Plugins/Place](http://wiki.compiz-fusion.org/Plugins/Place)

---

