---
title: "Custom Murrine-based theme - disable transparency?"
date: 2008-04-28
forum: General Help
---

### Post by okalex on 2008-04-28
Greetings everyone,

Recent Ubuntu convert here (from Debian, sheesh).  I'm currently playing around with my desktop theme and have created a custom one based on Human-Murrine.  The problem (to me) is that certain applications, most notably Terminal, have transparent menu bars and widgets.  Is there any way to disable this transarency, either in my gtkrc file or elsewhere?

Cheers,
Alex

---

### Post by okalex on 2008-04-29
- nudge, wink -

---

### Post by firefeather on 2008-05-03
> **okalex said:**
> I'm currently playing around with my desktop theme and have created a custom one based on Human-Murrine.  The problem (to me) is that certain applications, most notably Terminal, have transparent menu bars and widgets.  Is there any way to disable this transarency, either in my gtkrc file or elsewhere?

How did you get them to be transparent in the first place? This might give us a hint at where to start in helping you.

Human-Murrine isn't transparent in the menu bars and widgets for me.

---

### Post by okalex on 2008-05-03
> **firefeather said:**
> How did you get them to be transparent in the first place? This might give us a hint at where to start in helping you.

Human-Murrine isn't transparent in the menu bars and widgets for me.

In that case, I have no idea what I did.  In Preferences>Appearance, when I set Visual Effects to 'None', the transparency goes away, but I also lose drop shadows, fade in/out, and other effects that I'd like to keep.  If Visual Effects are set to 'Normal' or 'Extra' the transparency is there, but only in certain applications, like Terminal.  I've disabled transparency in Metacity using Configuration Editor (gwd>app, but this only affects the title bar and window border, not the GTK+ widgets.  Are there any other settings which may affect GTK+ opacity?

---

### Post by firefeather on 2008-05-04
> **okalex said:**
> In that case, I have no idea what I did.  In Preferences>Appearance, when I set Visual Effects to 'None', the transparency goes away, but I also lose drop shadows, fade in/out, and other effects that I'd like to keep.  If Visual Effects are set to 'Normal' or 'Extra' the transparency is there, but only in certain applications, like Terminal.  I've disabled transparency in Metacity using Configuration Editor (gwd>app, but this only affects the title bar and window border, not the GTK+ widgets.  Are there any other settings which may affect GTK+ opacity?

Well, if you have visual effects on, Metacity isn't actually doing anything; your window manager is Compiz. If you don't have the [FONT="Courier New"]compizconfig-settings-manager[/FONT] package installed, it is a great way to make sure the visual effects are working the way you want. Once it's installed, go to System -> Preferences -> Advanced Desktop Effects Settings. It even has a way to search for options you can change.

Maybe you could include a screenshot, because I don't know quite what's happening.

---

### Post by okalex on 2008-05-04
> **firefeather said:**
> Well, if you have visual effects on, Metacity isn't actually doing anything; your window manager is Compiz. If you don't have the [FONT="Courier New"]compizconfig-settings-manager[/FONT] package installed, it is a great way to make sure the visual effects are working the way you want. Once it's installed, go to System -> Preferences -> Advanced Desktop Effects Settings. It even has a way to search for options you can change.

Maybe you could include a screenshot, because I don't know quite what's happening.

I've set Compiz to use Metacity as the window decorator by adding 'gtk-window-decorator --replace' to the command field in Compiz Config Settings Manager.  That being said, the problem isn't with Metacity, because my window borders are displayed properly.  It's only the GTK+ widgets that are bing drawn semi-transparently.  I've attached a screenshot below.  You can see the transparency in the menu bar and, it's a little more difficult to see, but in the scroll bar as well.

I've searched through the CompizConfig Manager and haven't found anything related to this issue.  The Opacity Settings in General Options apply to all windows and don't seem to have an affect on this.  I've also checked the various settings in Terminal with no luck.  This isn't a huge deal, I'd just like to know that the problem is not with my theme.

Thanks,
Alex

[ATTACH]68766[/ATTACH]

---

### Post by firefeather on 2008-05-05
> **okalex said:**
> I've set Compiz to use Metacity as the window decorator by adding 'gtk-window-decorator --replace' to the command field in Compiz Config Settings Manager.  That being said, the problem isn't with Metacity, because my window borders are displayed properly.  It's only the GTK+ widgets that are bing drawn semi-transparently.  I've attached a screenshot below.  You can see the transparency in the menu bar and, it's a little more difficult to see, but in the scroll bar as well.

I've searched through the CompizConfig Manager and haven't found anything related to this issue.  The Opacity Settings in General Options apply to all windows and don't seem to have an affect on this.  I've also checked the various settings in Terminal with no luck.  This isn't a huge deal, I'd just like to know that the problem is not with my theme.

Thanks,
Alex

[ATTACH]68766[/ATTACH]

Thanks for the screenshot! I can see what you're describing.

Metacity isn't actually running if you set it to  'gtk-window-decorator --replace'; it's still Compiz and it's using a window decorator (border) that looks like Metacity. After what you described, I don't think it's Compiz, and it doesn't look like it's a problem with the window decorator; it looks like your GTK theme is causing the problem. I'm not especially experienced, though, so I'm not sure where to go from there, but maybe this will tip you off to something helpful.

---

### Post by dyfet on 2010-10-19
The cause is having rgba = TRUE in Murrine.

---

