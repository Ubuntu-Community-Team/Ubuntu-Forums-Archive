---
title: "Computer Extremely Laggy--HELP!"
date: 2008-02-02
forum: General Help
---

### Post by jsnelli2 on 2008-02-02
Here's the deal,  tonight I have been noticing that my computer has been pretty slow.  I just updated my graphics drivers to ati's new 8.1 proprietary driver.  It sped up compiz and all of its apps without a doubt.  But now I seem to have a problem with my computers resources being taken up.  If I am listening to music on Rhythmbox I can really notice it. 

Whenever doing something as menial as scrolling up and down on firefox my computers resources begin to immediately shoot up.  Depending on the amount of scrolling I'm doing I can get it to max out to 100 percent.  I can really tell that it is capping out my cpu whenever I'm playing music because the music will stop for a second as if it is trying to load it.  Music is all on an external hdd.  I've got a 1.6 ghz Dell Inspiron 9300 with 1 gig of ram.  I definitely didn't have this problem before updating the graphics driver, but it has without a doubt sped up and made my graphics more reliable.

I've also got a 3 gig swap partition that system monitor doesn't show being used....

The cpu takes massive hits when doing small jobs whether compiz is on or off.

Any ideas?

---

### Post by Cresho on 2008-02-02
try disabling indexing

system->preference->indexing service preference

---

### Post by jsnelli2 on 2008-02-02
Thanks for the response...unfortunately that didn't seem to make any difference.  I turned off indexing and rebooted and no difference. 

Just running Rhythmbox while playing a song seems to take anywhere from 20-50% resources, and that is not doing anything else.   I'm using 450 mb of ram and no swap.

I just don't know what could be causing this problem all of a sudden.  If I didn't see such an improvement with the rendering and speed of the compiz apps I would undoubtedly say it was something with that new driver...

---

### Post by nemilar on 2008-02-02
Which application[s] is/are it that are eating up your CPU?  Is it one in particular (perhaps X, compiz, or something), or is the individual applications you're using (firefox, rhythmbox, etc)?

You seem to already know how to monitor resources, but for reference, the 
```
top
```

command is used for this.

---

### Post by jsnelli2 on 2008-02-02
Xgl is jumping up to close to 100 percent whenever I scroll on firefox.  Rhythmbox stays at about 10 percent constantly while playing music.

---

### Post by nemilar on 2008-02-02
Alright, now that we've figured out the problem process, it seems that you're basically experiencing this bug:

[http://ubuntuforums.org/showthread.php?t=401186]("http://ubuntuforums.org/showthread.php?t=401186")

Some people seem to have various solutions to the problem, posted here:

[http://ubuntuforums.org/archive/index.php/t-581634.html]("http://ubuntuforums.org/archive/index.php/t-581634.html")

If you need more help, post your card model as well as its Device section in your xorg.conf and I'll try my best.

---

### Post by jsnelli2 on 2008-02-03
Okay, thanks for the reply.  I have had a busy weekend and have been unable to look into those solutions yet.  I will check it out either tonight or tomorrow and let you know if I that works for me!

---

### Post by jsnelli2 on 2008-02-04
Section "Device"
	Identifier	"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

No go on the reference....couldn't get anything to work.  This is all I could find in the xorg file on my card

---

### Post by jsnelli2 on 2008-02-04
Does no one have any other ideas for me?

---

### Post by jsnelli2 on 2008-02-04
I changed my xorg file driver section from fglrx to ati.  I now have fully regained my speed, but totally lost the ability to run compiz.  
Section "Device"
	Identifier	"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Driver		"ati"
	Busid		"PCI:1:0:0"
EndSection

I noticed a section at the bottom of the xorg file saying:

Section "Module"
	Load		"glx"
EndSection

It seems as if the posts referenced by nemilar say it is a problem with some ati cards running xgl.  If I change the aforementioned section from ati or fglrx or something similar could this alleviate the problem?

---

### Post by jsnelli2 on 2008-02-04
I've got speed back to normal..what can I do to get compiz working again?  It says "composite extension not available" whenever I try to enable it.

---

### Post by jsnelli2 on 2008-02-04
I enabled the composite extension in the xorg file by changing the composite value to 1...but now I am back to my original problem of the speed of compiz not being as fast...though my computer is back to the correct operating speed.  Before I formatted my computer recently I had compiz running better so I know that it's not necessarily my gfx card.  Any ideas?

---

### Post by jsnelli2 on 2008-02-04
OK-I just noticed that when running fglrxinfo it states that i'm using mesa driver 7.01 instead of the ati driver.  It also says Segmentation fault (core dumped).  What does this mean/ What could be wrong?  I'm running "ati" in the xorg file and fglrx in the module section.  Any info would be great...I'm sick of messing with this.  I just want it back to running smooth like it was before I formatted.

---

