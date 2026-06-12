---
title: "compiz login/out effect"
date: 2008-04-27
forum: General Help
---

### Post by patmalcolm91 on 2008-04-27
hi, i just installed the compiz login/out effect on hardy. for some reason, though, it doesn't work. i noticed in ccsm that the window match is ^ksplash, is there any way that this effect can be used in gnome (or is there any other way to achieve a smooth login)?

---

### Post by patmalcolm91 on 2008-04-30
anyone?

---

### Post by Sam on 2008-05-01
Wondering the same thing here...

---

### Post by patmalcolm91 on 2008-05-04
does anyone have any idea? I'm sure there are more people who are wondering how to do this.

---

### Post by Sam on 2008-05-05
As seen [here](http://forum.compiz-fusion.org/showthread.php?p=56803):

> Hey guys,
This is all I could find about the loginout plugin;

Loginout plugin:
This plugin provides the KWin4 login and logout effects. Following combinations should work:
KDE3: login only
KDE4: login and logout
Gnome: logout only

So it appears that this is mainly for KDE4 support rather than gnome or kde3


coz

---

### Post by conorsulli on 2008-05-08
It can be used in gnome! the guy here
[http://ubuntuforums.org/showthread.php?t=779151&highlight=login%2Flogout]("http://ubuntuforums.org/showthread.php?t=779151&highlight=login%2Flogout")
said that he had it working but then lost it. This would be a major help in ubuntu looking like a well pollished desktop I think. any ideas guys in getting it to work in the faintest?

---

### Post by rabbit251 on 2009-05-02
Enabling the effect doesn't do anything here either. A smoother entry and exit really would clean things up. Hmmm...

---

### Post by Locoxella on 2009-06-27
You can make it work at gnome logout by using this string on the "logout window match" textbox:

```
(class=X-session-manager & type=Dialog) | (class=Fast-user-switch-applet & type=Dialog)
```

That enables the effect when you push your shutdown button or choose close session, restart or shoutdown.

As for the login effect, im afraid that showing some window (like the old gnome starting up window) might be required. Therefore, I recommend instead to use the Splash compiz plugin with your own images or with blank images (in case you got bored of the compiz logo). Try to play around with both plugins settings, matching the saturation and brightness. Im sure that the final effect would be what you were looking for, I kown it was it for me.

cheers

---

### Post by cespinal on 2009-11-12
this window match did not work for me in karmic... do you know any way to make it work???

---

### Post by Janhouse on 2009-12-10
In Karmic I use these settings:

```
[loginout]
s0_out_match = class=Gnome-session & (title=Log Out of the Session | title=Shut Down the Computer) & type=DIALOG
s0_out_time = 1.405200
s0_out_brightness = 85.714302
s0_out_opacity = 27.868900
```

I guess this works only for english version but it is not hard to modify it. :)

And you can't use it for indicator-applet-session panel applet.

---

### Post by m.alaa8 on 2010-06-21
in login window match type:

(iclass=^xsplash)

in logout window match type:

class=Gnome-session & (title=Log Out of the Session | title=Shut Down the Computer) & type=DIALOG


i hope that help

---

### Post by Detritus Anon on 2011-01-01
> **m.alaa8 said:**
> in login window match type:

(iclass=^xsplash)

in logout window match type:

class=Gnome-session & (title=Log Out of the Session | title=Shut Down the Computer) & type=DIALOG


i hope that help

  If these settings don't work for you, make sure you have ADDialog enabled in CCSM.

---

