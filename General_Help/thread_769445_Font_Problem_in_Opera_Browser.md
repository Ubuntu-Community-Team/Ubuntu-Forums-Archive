---
title: "Font Problem in Opera Browser"
date: 2008-04-26
forum: General Help
---

### Post by GameKing505 on 2008-04-26
I don't know what part of the forums this should go under so mods i guess you can move it if it doesn't belong here.

I'm having a problem with the fonts in the Opera web browser. In firefox, when I open up a webpage, the fonts are crisp and clear. In Opera, they are grainy, fuzzy, and far too small. This is in the web pages as well as the menus. It's not a setting, because with the same version of Opera in Gutsy Gibbon, the fonts are beautiful. Hardy has somehow messed with my fonts. I've stumbled on a few other forum posts detailing this problem, but none of the solutions have worked for me.

Any help would be greatly appreciated.

Here's an image if it helps:

[http://img107.imageshack.us/img107/5319/badfontshk1.png](http://img107.imageshack.us/img107/5319/badfontshk1.png)

---

### Post by TransitMan on 2008-04-26
Have you double checked the setting in Opera's fonts?
Are the fonts being used the same as Firefox? Same size?

If not, then problem 1 lies there.

As far as "grainy" looking, I do notice a difference, but that is something to do with the way page was rendered.

---

### Post by GameKing505 on 2008-04-26
Not sure about firefox, but they are the same settings as Opera itself in a seperate install (in gutsy) and that one works fine. I'm pretty sure that its a problem in Hardy only.

---

### Post by TransitMan on 2008-04-26
I just did a comaprison between my Opera nad Firefox browsers.
Made sure the fonts rendered the same (Arial) and the size set to 14.
Brought up my home page in both and compared them and there was no difference. Both clear and crisp.

Have you install the msttcorefonts to Hardy yet?

---

### Post by Mze on 2008-04-26
See if this [solution]("http://ifacethoughts.net/2007/09/02/smooth-fonts-for-opera-in-linux/") helps

---

### Post by GameKing505 on 2008-04-26
This is so frustrating!!!

Yes I have installed msttcorefonts in hardy, and they helped in Firefox, but not in Opera at all. As for matching the firefox fonts, here's where the weirdness comes in. In firefox, the default is serif size 16. In Opera serif is not even a choice for a font. I went into Open Office, and serif isn't there either. What's that all about?

EDIT: Posted a little late there and didn't see your response Mze. Unfortunately, that doesn't make a difference either... If this keeps up I'm moving to firefox.

---

### Post by TransitMan on 2008-04-26
In my test, I used Arial font, because the serif font was not available to me in Opera.

Now as to the whys, don't know.
The devs might know for each browser and Open Office.

---

### Post by Mze on 2008-04-27
I'm using in Opera 9.50 beta2 and my fonts look OK to me. 

Which version of Opera are you using?

---

### Post by GameKing505 on 2008-04-27
I'm not using the beta for 9.5. I think the version I have is like 9.27 or something...

I'll check out the beta though and see if it's any better.

---

### Post by TransitMan on 2008-04-27
In my tests I am using the Opera 9.5 Beta2 which just came out last week.

---

### Post by luvinit on 2008-04-27
Is it related to this?



[http://ubuntuforums.org/showthread.php?t=760223](http://ubuntuforums.org/showthread.php?t=760223)

---

### Post by GameKing505 on 2008-04-28
I don't think so because Opera isn't a kde application is it? Anyway the fix you offered there was to install a kde app which I have none of. It would have to come with like 15 dependencies and I don't really want to install any kde stuff on my computer.

---

### Post by cookies on 2008-04-28
> **GameKing505 said:**
> I don't think so because Opera isn't a kde application is it? Anyway the fix you offered there was to install a kde app which I have none of. It would have to come with like 15 dependencies and I don't really want to install any kde stuff on my computer.

No, but it is a Qt Application. In which case it may apply.

---

### Post by juamez. on 2008-06-11
Anything yet?

Still having the same problem as topic starter. Ubuntu 8.04, opera 9.27 and msttcorefonts. Firefox is not affected.

edit: Little more explanation: AFTER installing msttcorefonts, all fonts in opera look too short. As in broad enough, but not high enough. When upping the font size in the preferences, all fonts get larger, but remain too broad or wide or whatever you may call it. Never are the fonts looking the way they are supposed to look. This is only the case with Opera, msttcorefonts and Hardy. Opera did just fine in Gutsy, really.

Why is Opera acting so strange now?

edit2: the same is true for Opera 9.5beta2 (upgraded from 9.27, maybe I'd fiddle some more with a pure version of 9.5b2 and a fresh install of Ubuntu 8.04

BUT REALLY, what gives? I'm not too happy with this kind of regression.

---

### Post by TransitMan on 2008-06-11
I am using Opera 9.50 RC1, with the Arab fonts set at 15 and my web pages appear clear and without distortion.

This is under both Xubuntu and Ubuntu 8.04.

I am not sure of what "regression" you are referring to. Under 7.10, I had minor issues of fuzzed fonts, but after going with the 9.50 test builds it all cleared up.

---

### Post by juamez. on 2008-06-12
> **TransitMan said:**
> I am using Opera 9.50 RC1, with the Arab fonts set at 15 and my web pages appear clear and without distortion.

This is under both Xubuntu and Ubuntu 8.04.

I am not sure of what "regression" you are referring to. Under 7.10, I had minor issues of fuzzed fonts, but after going with the 9.50 test builds it all cleared up.

What can I say? 

A picture says more than a thousand words. And here is proof:


**ubuntuforums.org rendered in Ubuntu 8.04 with FF3 beta 2**[IMG]http://hawn.be/pics/ff3b2ubuntuforums.png[/IMG]


**ubuntuforums.org rendered in Ubuntu 8.04 with Opera 9.50 beta 2**[IMG]http://hawn.be/pics/op9.5b2ubuntuforums.png[/IMG]


**ubuntuforums.org rendered in Windows XP SP3 with Opera 9.27**[IMG]http://hawn.be/pics/op9.27winXPubuntuforums.png[/IMG]


**tweakers.net rendered in Ubuntu 8.04 with FF3 beta 2**[IMG]http://hawn.be/pics/ff3b2tweakers.png[/IMG]


**tweakers.net rendered in Ubuntu 8.04 with Opera 9.50 beta 2**[IMG]http://hawn.be/pics/op9.5b2tweakers.png[/IMG]


**tweakers.net rendered in Windows XP SP3 with Opera 9.27**[IMG]http://hawn.be/pics/op9.27winXPtweakers.png[/IMG]


**_My conclusion:_**

You can see that the fonts are looking how they should be looking in FF3, but not in Opera on ubuntu. This is proven with the pictures taken from Windows where fonts aren't such a problem.

Now, does anybody have the slightest guess into why this is like it is?

When ubuntu 8.04 came out and with FF3a5 having problems with the fonts, everybody was saying to fix the DPI setting, but it did not fix this problem. It only made the same "wrong" fonts a bit bigger.

---

### Post by Ulysses4ever on 2008-10-23
Seems to have the same problem as the topic starter, Opera 9.60, Hardy. Looking forward Ibex to fix it. No other hopes...

---

### Post by Nikoalos500s on 2008-12-18
I think, the problem is not related with the Opera fonts itself but on the fact that Opera does not recognise or use the system fonts which FireFox does pretty well!!
Ubuntu 9.10 Intrepid and Opera 9.63 is here yet the fix hasn't come along. Opera's fonts are still pixelised and grispy. Does anybody came up with something new or we migrate to FireFox?):P

---

