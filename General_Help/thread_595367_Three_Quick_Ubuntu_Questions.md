---
title: "Three Quick Ubuntu Questions"
date: 2007-10-28
forum: General Help
---

### Post by Mark Grice on 2007-10-28
Hey all,

Newbie Ubuntu user -- old time Unix user waaaay back in the day. Haven't been in the *nix world since CURSES was considered a GUI...

Anyway, I'm using UBUNTU and I have a couple of quick questions that I can't find anywhere online, so here goes:

***1: No Root account? Really?*** Does that mean that absolutely EVERYTHING I would have done as root I can now do as long as I preface it with sudo? 

(BTW... I somehow missed sudo's meaning. The first few times I tried to put in someone's step by step, I assumed sudo was their login name... then I thought.. hey ... wait... is that Super User DO by chance...?  Oh... and I also reinstalled UBUNTU once cause I was trying to login as Super User, and every time I put in a password it rejected it. So I thought - Damn, I guess I forgot the #@$% password) 

I guess it's OK, but it will take some getting used to. It just doesn't feel right not to be root on my own system...

[B][I]2. What is the difference between using sudo apt-get and synaptic package manager? 
[/I][/B]
3. This is a Firefox question. ***Why can't I resize my Firefox window?*** I can resize Firefox on windows, or MAC, but not here? How come? (Or is there a way and I'm just missing it???)

Thanks!

---

### Post by Wiebelhaus on 2007-10-28
> **Mark Grice said:**
> Hey all,

Newbie Ubuntu user -- old time Unix user waaaay back in the day. Haven't been in the *nix world since CURSES was considered a GUI...

Anyway, I'm using UBUNTU and I have a couple of quick questions that I can't find anywhere online, so here goes:

1: No Root account? Really? Does that mean that absolutely EVERYTHING I would have done as root I can now do as long as I preface it with sudo?

***_Yes! it's fabulous  _***

(BTW... I somehow missed sudo's meaning. The first few times I tried to put in someone's step by step, I assumed sudo was their login name... then I thought.. hey ... wait... is that Super User DO by chance...?  Oh... and I also reinstalled UBUNTU once cause I was trying to login as Super User, and every time I put in a password it rejected it. So I thought - Damn, I guess I forgot the #@$% password) 

I guess it's OK, but it will take some getting used to. It just doesn't feel right not to be root on my own system...

2. What is the difference between using sudo apt-get and synaptic package manager?

***_None really , Apt-get is the term old school way and synaptic gives you a sweet GUI , Both get you the same effect respectively.  _***


3. This is a Firefox question. Why can't I resize my Firefox window? I can resize Firefox on windows, or MAC, but not here? How come? (Or is there a way and I'm just missing it???)

***_Un - maximize it by clicking the box in the middle between the X and minimize , it's locked unlock it then you can_***

Thanks!

No worries , you'll love it!

---

### Post by Mark Grice on 2007-10-28
> **sx66gns said:**
> 
Un - maximize it by clicking the box in the middle between the X and minimize , it's locked unlock it then you can
!

OK.. thanks for the fast reply -- SO, I don't mean to seem really dense here... but what do you mean "unlock it?"

I checked the EDIT->properties, I right clicked all over the place... I can't see anything telling me it's locked... Or giving me the chance to unlock... Where do I find that? (BTW. when I select RESIZE from the right click option on the window bar, the screen gives me blue box like it is going to let me resize, but then I can't click to execute it... I end up having to ESC out of that)

Searching FireFox HELP for "UnLock" returns nothing...

---

### Post by Wiebelhaus on 2007-10-28
click it , you'll see the windows dismount , you can then grab the edges and resize.

---

### Post by Mark Grice on 2007-10-29
> **sx66gns said:**
> click it , you'll see the windows dismount , you can then grab the edges and resize.

Hmmm... Nope. It doesn't work for me. I can click maxsize and then click unmaximize all day long, and I never get and handles to resize my window.

I have changed my default look and feel (using theme manager). Could that change things?

BTW, Nautilus works find. The Text Editor works fine. I Just can't resize FireFox.

Is Firefox KDE? Maybe I'm having a problem with KDE but not gnome windows?

---

### Post by Wiebelhaus on 2007-10-29
There's only one answer , HAX.



...just fooling





idk man , good luck.

---

### Post by dayvy on 2007-10-29
Firefox is not a KDE application. Right click the window title bar and choose "unmaximize" if it isn't unmaximized already. Move your mouse to the button right window and the mouse should change it's look. Drag the window corner to resize. Sometimes gnome unmaximizes but doesn't really change the window size unless you drag the corner as I suggested. It should remember the unmaximize size after that.

d.

---

### Post by prshah on 2007-10-29
Or you can try to resize it using Alt+middle (scroll) button anywhere within the window. That works for all windows if you are running gnome/compiz...

Cheers,
Priyasen

---

### Post by Mark Grice on 2007-10-30
Thanks all! 

Unfortunately, none of that worked... but I did find the culprit.

***It was the change in the theme! ***

I wish now I remember which theme it was I installed (from GNOME-look) but it would not let me resize Firefox. It also wouldn't let me resize SeaMonkey (not surprising, I guess)

But the "system" windows (ie Nautilus) were fine. Weird.

Anyway, I clicked on Theme Editor, went back to ClearLook, and now things are running fine.

Thanks again!

---

