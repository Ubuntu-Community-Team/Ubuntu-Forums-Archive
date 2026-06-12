---
title: "How can I temporarily prevent sleep or suspend while an app is running?"
date: 2018-06-01
forum: General Help
---

### Post by Paddy Landau on 2018-06-01
An app called Caffeine keeps the system awake while certain actions are active, e.g. watching a video. It used to be configurable, so that you could (for example) set Caffeine to activate automatically when a specific program was running, and deactivate when it ended.

Unfortunately, the configuration options were removed (deliberately — why?), so that only the default actions work. That doesn't work for me, because I want to activate it when a specific program is running, e.g. my backup script.

Therefore, I'm looking for a way to temporarily prevent sleep or suspend. I'm happy to write a simple script, such as something in cron. My problem is that I don't know how to programmatically disable and enable sleep and suspend.

A configurable alternative to Caffeine would also work for me.

What can you recommend for me, please?

Note that I'm running Lubuntu, not Ubuntu; version 16.04, soon to upgrade to 18.04.

---

### Post by ajgreeny on 2018-06-01
I'm not sure about 16.04 as I don't have it any more and have moved to Lubuntu-18.04 but in 18.04 there is a Computer icon in my system tray showing the computer is plugged into power from mains (it's a desktop so no battery).

If I right click on that I get a context menu option to enable "Presentation mode" which does exactly what you want, ie, it disables the Power-manager and stops any sleep or even a screensaver, if you use one, I think, though I'm not certain about that.

I have to use this when using my desktop as a plexmedia-server as otherwise I get partway through a movie on my TV and suddenly it all disappears; very annoying.

---

### Post by Paddy Landau on 2018-06-02
@ajgreeny thank you. I have the icon and had completely forgotten about it!

I wanted something automatic (sorry that I didn't make it clear in my question), but the icon will do as a workaround in the meantime.

Now, I just have to find out how the icon does its thing so that I can duplicate it programmatically!

---

### Post by Paddy Landau on 2018-06-02
Ah&#8230; Now that I know the name "presentation mode", I can search using that term. And I found this.
```
[COLOR=#696969]# Toggle presentation mode.[/COLOR]
xfconf-query --channel xfce4-power-manager --property /xfce4-power-manager/presentation-mode --toggle

[COLOR=#696969]# Turn on presentation mode[/COLOR]
xfconf-query --channel xfce4-power-manager --property /xfce4-power-manager/presentation-mode --set true

[COLOR=#696969]# Turn off presentation mode[/COLOR]
xfconf-query --channel xfce4-power-manager --property /xfce4-power-manager/presentation-mode --set false
```
I want to find out the various options available to the property, but try as I might, I cannot find the documentation! Never mind, at least I have my answer.

Thanks again for pointing me in the right direction.

---

