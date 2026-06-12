---
title: "Xsession issues..."
date: 2008-05-03
forum: General Help
---

### Post by DixieWolf on 2008-05-03
Okay, so. I have a laptop, and I have an external lcd monitor as well. I have used nvidia-settings, and made it successfully work using my external setup how I want. 

But this means I have to run nvidia-settings every time I get on my laptop, unless i save the changes to my xorg.conf, but then, If I run my laptop without the external, I can only see half of my 'screen' because xorg still thinks the external is there.

So what I'm doing is creating a seperate gdm session for Dual Monitor mode, so when I login, I can tell the computer "hey, computer! there's 2 monitors!" and otherwise, it just does single. The way I'm achieving the change is I have 2 copies of my xorg.conf - one configured for dual monitors, and one for single. now, I've added a file in my Xsession.d, so it checks when xsession starts, and its set to run at 25 (the first item in the list runs at 20) But the changes to the xorg aren't loaded. If i restart X, they are loaded...


So really, my question is, when/how does X load the xorg.conf, and is there some way I can get my changes to work after I login, but before X really gets going?

---

