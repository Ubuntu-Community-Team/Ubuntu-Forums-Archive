---
title: "Firefox 3 Beta 5 Random Right Click Events"
date: 2008-05-11
forum: General Help
---

### Post by typeZERO on 2008-05-11
So when I am using Firefox 3 Beta 5 and I press the right button on my mouse sometimes I get random mouse on right click event. EX: I try opening a link using a new tab so I right click to get the right click menu but I get a random event like save link as or element properties. It is really frustrating because I want to open a new tab but I get a random event. Does anyone had this happen and how do fix it? should i report this too? please help thanks.

---

### Post by sdennie on 2008-05-11
Does it happen every time?  Sometimes when mice get worn out they start to randomly register double clicks.

---

### Post by ali999 on 2008-05-11
never had this issue but its beta, so don't go nuts over it. why don't you try a stable build of firefox or another web browser such as Opera. You can find it in the package manager.

---

### Post by typeZERO on 2008-05-11
vor - my mouse is clean since it's a new laser mouse
ali999 - it happen more so often that it becoming annoying and i couldn't find an answer. i don't want to get firefox 2 because i heard people are having problems with it

I think the only thing left to do is to just not use the right click button and just press CTRL to open new tabs until firefox 3 comes out

---

### Post by sdennie on 2008-05-11
Well, I was more referring to the click sensors.  It doesn't matter what type of mouse you have, they eventually wear out.  I would try another mouse if possible and see if you still see the problem.

---

### Post by steeleyuk on 2008-05-11
I've had this happen as well, not often but when it does it can be annoying. Mine has a habit of switching the page direction...

---

### Post by dirtylobster on 2008-09-25
I randomly experience this both with the laptop's touchpad and my bluetooth mouse.

Edit: And I'm obv. not using the beta version. :D

---

### Post by dirtylobster on 2008-09-25
This with both KDE and Openbox.

---

### Post by dirtylobster on 2008-09-25
The natural reason imo to this problem would be that the right-click release isn't registered properly, sometimes premature, sometimes delayed. Any way to fix/adjust this?

---

### Post by lukjad on 2008-09-25
The best I came by is to hold the right click for about 3 seconds then release. The dropdown menu should open normally.

---

### Post by rrrrrr on 2008-09-28
bump

---

### Post by heikor on 2008-10-05
I'm having the same problem. I'm using Firefox 3.0.3, not the beta.
The problem is that the right click menu opens very quickly, once you press the right button. So when you release the right button, the mouse pointer is already on one of the menu items, and the release button event is seen as a click on that item. This obviously happens too fast to see, but when I press and hold the right button, move the pointer over one of the options, and then release it, it's the same.
I haven't found a solution yet, but I think, the menu should be placed so that it's not below the mouse pointer, or that only the release button event is regarded as a click.
For now, I'm just holding the mouse button down while selecting a menu item.

---

### Post by lukjad on 2008-10-05
Yes. I agree. That is what I have experianced too. You just need to press and hold the right mouse button for three seconds and then release it. Usually it will form away from your mouse then.

---

### Post by clanger on 2008-10-05
Same issue here with 8.04 and firefox 3.0.3
Two different systems, two different mice, 1 is ps2 the other is usb
Sometimes it shifts the page display, most often it wants to email something and I get evolution mail trying to open, others are bookmark, save as - all corresponding to the menu issue described above.

---

### Post by herkamire on 2009-01-22
I'm so glad I'm not the only one experiencing this problem. This drives me nuts. Usually happens when I tap the right mouse button very quickly.

It frequently opened up evolution, but I've recently seed it randomly do every single thing under the right-click menu.

I deleted /usr/bin/evolution to somewhat mitigate the damage caused.

I have ubuntu 8.10 and firefox 3.0.5

I found that this bug is well documented an ubuntu's bug tracking site here:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313)

and that it's filed and assigned upstream at mozilla:

[https://bugzilla.mozilla.org/show_bug.cgi?id=404314](https://bugzilla.mozilla.org/show_bug.cgi?id=404314)

This bug is not getting a high enough importance, so please go to the mozilla bug page above and vote for it.

---

### Post by Orfintain on 2009-01-22
glad to hear its "upstream" I have noticed it as well

---

### Post by Saghaulor on 2009-01-27
It's definitely a bug in Mozilla.

Ever since v3 I've had issues with right clicking.

Many different computers, many different versions of Ubuntu. 

It's a Mozilla problem for sure.

---

### Post by brallan on 2009-06-11
well, I have a new install of 9.04 with the same annoying problem, so this bug is around for over a year. My system is updated and running Firefox 3.0.10, which the mozilla website says is the latest version. Should i install some kind of backport or is there some kind of workaround?

---

