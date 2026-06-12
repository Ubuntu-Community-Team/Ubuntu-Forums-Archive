---
title: "Applications/&quot;Start&quot;/Menu Button/Icon - How do you Change it - REALLY?"
date: 2008-04-01
forum: General Help
---

### Post by OzzyFrank on 2008-04-01
OK, I've pondered this question since 6.10 Edgy and seen it answered "wrong" many times... or should I say seen the same answer that people swear would work, but each person posting the question swear didn't. To change the Ubuntu logo on the menu button, people invariably say to go to **apps->panel->objects** under **gconf-editor** and use the **custom icon** setting and then run **killall gnome-panel**. This never works, but people seem to keep giving this advice.

Or they will say to replace the actual icon with your own preferred one, but the icon and path to it can differ WILDLY, eg: **/usr/share/icons/<iconset>/<size>/apps/gnome-logo-transparent.png**, or others in said folder like **start-here.png** or **distributor-logo.png**. Or they'll say to find your installed icon theme in **~/.icons** and replace one or all of the mentioned files, or one of many different pics in **/usr/share/pixmaps**, or...

As you can see, there are some wildly conflicting instructions for achieving this, so is there now a definitive answer? Also, since the gconf-editor way seems to have never worked for anyone in the last couple of years, why do we still see this?? Is it that in other Gnome-based distros it actually does work?

It might be mere trivium for many, but since there are quite a few who would like to change it _from_ the Ubuntu logo, or _back_ to it once an icon theme changes it to the Gnome foot or something, I would suggest a future version of Ubuntu either include a little app for it, or add it to Appearance or something.

---

### Post by bwhite82 on 2008-04-02
AFAIK, the gconf-method (the only method I am aware of) only works for the main menu applet (the one with **only **the Ubuntu icon) and NOT the menu applet with the text. Forget the exact names, am at work.

---

### Post by OzzyFrank on 2008-04-02
OK... is that the menu you would get when you "Add to Panel" and there is an option to add the menu? Anyway, hope at some point Gnome or Ubuntu make it easier to change it, like include an app for this task. For me it's more that when I try a new theme I am not stuck with the icon they give me, or have to go messing about just to change it.

---

### Post by munkyeetr on 2008-04-02
I agree there should be a definitive method that **works**!!

I went through a couple days of trying different methods that people were suggesting, and finally I got something to work for me, but when I relayed that information to the next person who was asking, it didn't work for them. Frustrating as hell!

For the record, and someone may very well contradict me because they were able to, but I found that I could not change the icon if I was using a default icon theme, like Human, but could change it no problem if I used a different theme I downloaded from gnome-look.org (And by that, I mean I could even change the one that came with the downloaded theme to whatever I want.)

---

### Post by OzzyFrank on 2008-04-02
Yeah, it's almost comedic, hehe... you see one person saying "Yeah, great, that worked for me!!" and the next saying "No, it didn't do a thing!". But most of the time it's disappointed people asking for new instructions. And then you have those people who wouldn't even know what their current icon theme is, and people like me who test icon themes a lot so changing the menu logo would be a waste of time. Wish someone would write a little app, hehe.

---

### Post by bwhite82 on 2008-04-02
> **OzzyFrank said:**
> OK... is that the menu you would get when you "Add to Panel" and there is an option to add the menu?

Yes. The applet to use is "main menu" and not "menu bar". You should, in theory, be able to change the icon in gconf then. At least its always worked for me.

---

