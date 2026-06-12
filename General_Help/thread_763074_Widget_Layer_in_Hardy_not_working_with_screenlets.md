---
title: "Widget Layer in Hardy not working with screenlets"
date: 2008-04-22
forum: General Help
---

### Post by Ryuki_NdranC on 2008-04-22
I have steup all my screenlets with the option "treat as a widget" and i have activated the widget layer in compiz. All is working fine. When i press f9 my screenlets show just fine, but if i hit "show desktop" they all get minimized no matter what.

I alrdy tried type=screenlets.py

It worked fine till i pressed "show desktop" with the same results. Anyone else have this same problem? I had this setup in trhe same laptop under gutsy and it worked all fine.

Apreciate any support and clues. Thx in advance :)

---

### Post by Ryuki_NdranC on 2008-04-23
./bumb :(

nothing...:confused:???

---

### Post by Ryuki_NdranC on 2008-04-23
./bump :(

My last... I can't believe no one is having the same problem or has any clue :(

---

### Post by issih on 2008-04-24
Try this..

Open CCSM  -> General Options -> General Tab

Untick "Hide Skip Taskbar Windows"

Not 100% sure that will do what you want, as I'm a bit confused as to how you expect this to work within the widget layer....

The widget layer should just show 'widgetized' screenlets, overlayed on top of whatever is on the screen, when you hit F9, which you say it does. If you then hit "show desktop", surely it should take you back out of the widget layer and well...show you your desktop?

If this is what it is doing, then that behaviour makes sense to me. I used the above method because I have one screenlet (a clock) not in the widget layer, which I wanted to behave as if it was just part of the desktop background, and therefore wanted it to stay put when I used show desktop. The above method along with ticking keep below sorted that out for me.

Hope thats useful :)

---

### Post by Ryuki_NdranC on 2008-04-25
> **issih said:**
> Try this..

Open CCSM  -> General Options -> General Tab

Untick "Hide Skip Taskbar Windows"

Not 100% sure that will do what you want, as I'm a bit confused as to how you expect this to work within the widget layer....

The widget layer should just show 'widgetized' screenlets, overlayed on top of whatever is on the screen, when you hit F9, which you say it does. If you then hit "show desktop", surely it should take you back out of the widget layer and well...show you your desktop?

If this is what it is doing, then that behaviour makes sense to me. I used the above method because I have one screenlet (a clock) not in the widget layer, which I wanted to behave as if it was just part of the desktop background, and therefore wanted it to stay put when I used show desktop. The above method along with ticking keep below sorted that out for me.

Hope thats useful :)

really... thx for the answer. unfortunately it didn't work.

Let me elaborate more on my problem... back in Gutsy i had compiz (don't remember if i had tick or untick the "Hide Skip...") with widget layer ON (100% brightness, so it was completely clear) and unticked the "Stop widget layer on click". So as long i didn't press f9 again, all my windows on the widget layer and the desktop are shown indifferently. Back then as long i put all my screenlets on the widget layer they were never hide by the "show desktop".

NOW in hardy with the same setup... Every window attached to the widget layer (screenlets or not) hides even though it didn't on Gutsy. I tried your advice with several more combinations and i didn't notice any appreciable difference.

But thanks for your advice, always appreciated :)

Good luck

---

### Post by issih on 2008-04-25
I tried playing with the way you have things set up:

Widget layer 100% brightness
click to end widget layer : off
Hide skip taskbar windows : off

Hitting f9 made all the screenlets ticked as widgets visible as if they were normal windows.

Hitting ctrl-alt-d (my show desktop shortcut) all the normal windows minimized, but the widgets remained visible.

Not sure why it would work for me and not for you.

Just to check, do your screenlets show up in the taskbar?, Theres an option on each screenlet to set "skip taskbar" which I think is on by default, but is obviously the setting that the "Hide skip taskbar" setting in ccsm picks up on.

---

### Post by Ryuki_NdranC on 2008-04-25
I solve it with your help :)

I started to play with the windows effects and started to notice that when i change something, compiz didn't apply the effect. The i notice that my compiz systray icon has the option "refresh windows manager". I click on it, compiz "refreshed" and all the settings i change before started to make effect (including "Hide ...") :)

What was strange is that even though i reboot my computer, compiz needed that "refresh" so things started working, and whats even more strange is that it doesn't need it anymore. o.O

No all is working fine. Thanks to your advice i started looking around in that direction :)

Best of lucks for you :KS

---

### Post by issih on 2008-04-25
Glad to hear you got it sorted

---

### Post by dregin on 2009-07-28
> **issih said:**
> Try this..

Open CCSM  -> General Options -> General Tab

Untick "Hide Skip Taskbar Windows"

Not 100% sure that will do what you want, as I'm a bit confused as to how you expect this to work within the widget layer....

The widget layer should just show 'widgetized' screenlets, overlayed on top of whatever is on the screen, when you hit F9, which you say it does. If you then hit "show desktop", surely it should take you back out of the widget layer and well...show you your desktop?

If this is what it is doing, then that behaviour makes sense to me. I used the above method because I have one screenlet (a clock) not in the widget layer, which I wanted to behave as if it was just part of the desktop background, and therefore wanted it to stay put when I used show desktop. The above method along with ticking keep below sorted that out for me.

Hope thats useful :)

This had been annoying me for a while. Much thanks for the answer. Worked perfectly :)

---

