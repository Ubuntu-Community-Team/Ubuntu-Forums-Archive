---
title: "mouse cursor alignment"
date: 2004-11-10
forum: General Help
---

### Post by shookmon on 2004-11-10
Not sure how to even phrase this question, but....

If I were to try an put the mouse cursor over a single pixel hotspot, then I'd have to have the cursor about 5 pixels left and 5 pixels down to be able to click on the hotspot.

I'm running Ubuntu on VMware workstation 4.5.2

any ideas?

Thanks!!

Michael Shook
Omega Tower Design Partners

---

### Post by HungSquirrel on 2004-11-10
You didn't ask a question.

---

### Post by FLeiXiuS on 2004-11-11
[QUOTE=HungSquirrel]You didn't ask a question.[/QUOTE]


Good reply  :razz:

---

### Post by shookmon on 2004-11-11
Ah, I see. The cursor is SUPPOSED to not be actually over the click spot then?

---

### Post by TravisNewman on 2004-11-12
[QUOTE=shookmon]Ah, I see. The cursor is SUPPOSED to not be actually over the click spot then?[/QUOTE]
 I think he's saying that if the * is where he wants to click, then the ^ is where his mouse has to be to click it, as best as you can represent in plain text:

---*
^

---

### Post by fulvioo on 2004-11-12
Of course he asked one question, read it again!

And yeah, I got the same problem with mouse on:
vmware 4.52+vmwaretools

---

### Post by shookmon on 2004-11-12
fulvioo: That has been my leading suspicion, did you find a fix or workaround?

---

### Post by fulvioo on 2004-11-13
Not yet m8.
Actually I havent looked on this very close, but if I get any hints/leads ill post it here

---

### Post by HiddenWolf on 2004-11-13
Should be in vmware indeed. Never had a display as crisp and concise as ubuntu's.

---

### Post by TravisNewman on 2004-11-13
I was running it in vmware just to try it out a bit before making the plunge, and  I had no problems like that. Are you using the Windows or Linux version of VMWare? I was using Windows.

---

### Post by shookmon on 2004-11-14
I'm running VMWare on Windwoes XP SP2 with, and this might be the issue, VMTools installed. I wonder if changing the mouse driver back to defaults would help....

---

### Post by TravisNewman on 2004-11-14
[QUOTE=shookmon]I'm running VMWare on Windwoes XP SP2 with, and this might be the issue, VMTools installed. I wonder if chnging the mouse driver back to defualts would help....[/QUOTE]
 Yeah I never installed VMWare tools, and I never had this issue, so it may be worth a shot to try out the default mouse driver. If I remember correctly, I had some issues with VMWare tools.

---

### Post by shookmon on 2004-11-14
Yup, thats the issue. Changing the driver and protocol back to defaults fixed the issue. I've updated my [ubuntu-warty-on-vmware](http://www.omegatower.com/library/ubuntu-warty-on-vmware.htm) How-To with the new changes.

While this does fix the isssue, it unfortunately removes the ability for the mouse to gracefully exit the VMware window, so you'll have to use the [CTRL]-[ALT] to exit the window. Since I usually run full screen anyway, this won't hurt me at all.

Perhaps VMware could get a push from the Ubuntu developers to include support?

---

### Post by TravisNewman on 2004-11-14
Yes, I love that feature. It's been so long since I've actually installed VMWare Tools, I forgot it was there, but CTRL+ALT isn't that big a deal.

If you haven't yet, you should post your howto on the wiki.

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=panickedthumb]Yes, I love that feature. It's been so long since I've actually installed VMWare Tools, I forgot it was there, but CTRL+ALT isn't that big a deal.

If you haven't yet, you should post your howto on the wiki.[/QUOTE]


boo CTRL ALT.  I just stick to my normal sessions.  Multiple sessions are always a fan of mine.  Plus they are more configurable. :-D

---

### Post by shookmon on 2004-11-15
I thought I had put it in the appropraite places, well, a reference to it's url anyways. Do you see somewhere it isn't that I should put it?

---

