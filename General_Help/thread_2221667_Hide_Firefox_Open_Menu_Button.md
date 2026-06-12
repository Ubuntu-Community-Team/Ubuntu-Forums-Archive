---
title: "Hide Firefox Open Menu Button?"
date: 2014-05-03
forum: General Help
---

### Post by d4m1r on 2014-05-03
Hey guys, I took the leap of faith and upgraded to Firefox 29 which includes the new UI. I was pleasantly surprised because I actually like it and I have been able to restore the previous layout I had EXCEPT for that new "Open Menu" button....If you don't know what I am talking about, it's this button (far right corner);

[IMG]https://i.stack.imgur.com/ccUtF.png[/IMG]


The ironic thing is that it is the very button you use to customize your layout but it seems you can't remove/hide the button itself?? Does anyone have a workaround to remove/hide it from view maybe via about:config? I feel the button is unncessary and takes up screen real estate needlessly because all the functionality it "provides" I already access (and preffer to access) via the top menu bars.

---

### Post by vasa1 on 2014-05-03
> **d4m1r said:**
> ... Does anyone have a workaround to remove/hide it from view ...
You can do so using CSS:
```
/* AGENT_SHEET */ 
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
    
#PanelUI-menu-button { display: none !important; }   


```
The first line, **/* AGENT SHEET */**, may or may not be needed.
The code goes in *~/.mozilla/firefox/your_profile/chrome/userChrome.css* or into a Stylish sheet.

Of course, if you install [CTR]("http://forums.mozillazine.org/viewtopic.php?f=48&t=2773133"), you can remove it by simply right-clicking on it and choosing "Remove from toolbar"!

---

### Post by d4m1r on 2014-05-03
Thanks for the tip vasa!

Am I wrong to assume though that this manual change will get overwritten every time I update Firefox in the future? Specifically if any changes are made to user profile styling/formatting. I saw that addon but didn't want to install it because I actually like this new UI design as I mentioned and only have this minor gripe.

---

### Post by vasa1 on 2014-05-03
> **d4m1r said:**
> ...
Am I wrong to assume though that this manual change will get overwritten every time I update Firefox in the future? Specifically if any changes are made to user profile styling/formatting. ...
I answered your question as Firefox exists today :)
But, in the "normal" course of events, an update to Firefox should not alter the contents of userChrome.css. Of course, it's possible that Firefox devs may decide that userChrome.css is a danger and remove it :) The way Firefox is "evolving" anything is possible.

---

