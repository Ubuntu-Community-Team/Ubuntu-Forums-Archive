---
title: "Ubuntu left out the X1300 when they made edgy eft"
date: 2007-04-05
forum: General Help
---

### Post by ambien on 2007-04-05
If you post trying to make your Radeon X1300 work with hardware acceleration on a (otherwise totally badass because of upgrades) 2002 motherboard, GOOD LUCK! I have tried every guide, suggestion, manual, hint, etc. NOTHING WORKS FOR THIS SETUP. Even though screen savers fps turn into spf (seconds per frame), and you can't use beryl...it is still faster than windows lol. Feisty fawn is supposed to have better support, so hopefully in 2 weeks linux will become new again!

Your sleepless buddy,

Ambien

---

### Post by cantormath on 2007-04-05
> **ambien said:**
> If you post trying to make your Radeon X1300 work with hardware acceleration on a (otherwise totally badass because of upgrades) 2002 motherboard, GOOD LUCK! I have tried every guide, suggestion, manual, hint, etc. NOTHING WORKS FOR THIS SETUP. Even though screen savers fps turn into spf (seconds per frame), and you can't use beryl...it is still faster than windows lol. Feisty fawn is supposed to have better support, so hopefully in 2 weeks linux will become new again!

Your sleepless buddy,

Ambien

ubuntu forgot nothing.  ATI will not make a driver for you to use linux.  They want you on windows.

Did you try envy?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by shavenlunatic on 2007-04-05
I had an AGP x1300 up until about 4 weeks ago (upgraded and went for nvidia)... i managed to get it working, with beryl, and running games under Wine....  it can be fustrating at first but you will get there..

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)    (for your drivers)

and

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)  (for everything else)

were very useful.. assuming you are using edgy, but there are equivalent guides on those sites for other versions)

good luck.. keep at it!

p.s. I did have everything working fine.. but moving to nvidia is still noticeable better performance.. but in Counter-Strike:Source on the x1300 under wine i could still get 40-60FPS easilly :)

---

### Post by ambien on 2007-04-11
Thank you for posting, this is a reply to both posts:

To ShavenLunatic:
I appreciate the link for drivers, but the link you sent has never worked for me. It makes my display nearly unusable. However, I notice usability returns when I remove the composite disable line from my configuration. However, I do not get acceleration then.

To CantorMath:
Yours is a solution I have yet to try, I have never heard of envy, but I intend on using it. I am about to reboot in Ubuntu and give it a go. I will post the results.

---

### Post by ambien on 2007-04-11
No luck with envy, I got the same results as if I installed from the wikiguide. The symptoms are this: windows don't refresh themselves. In fact nothing does, if I drag an icon, it seems to disappear until I highlight my desktop. Then it pops back up. Also when I am on the Internet, when I scroll up and down the page stays the same, except for about an inch of garbled text at the bottom which seems to be moving. If I want to see the page I have to highlight it, and then it is clear until I scroll again. When I open windows they often pop-up transparent until I highlight them. I don't know how to describe the problem. But no matter what, it always goes away if I erase the "Composite" "Disable" line in my xorg.conf file. But it also turns off the acceleration, as I get mesadrivers when I type fglrxinfo in terminal. 

I'm trying envy with manual install option, maybe it will work this time lol

---

### Post by ambien on 2007-04-11
Still no luck, as I say this absolutely refuses to work on my computer. Please help

---

### Post by Hobo Joe on 2007-04-18
> **ambien said:**
> No luck with envy, I got the same results as if I installed from the wikiguide. The symptoms are this: windows don't refresh themselves. In fact nothing does, if I drag an icon, it seems to disappear until I highlight my desktop. Then it pops back up. Also when I am on the Internet, when I scroll up and down the page stays the same, except for about an inch of garbled text at the bottom which seems to be moving. If I want to see the page I have to highlight it, and then it is clear until I scroll again. When I open windows they often pop-up transparent until I highlight them. I don't know how to describe the problem. But no matter what, it always goes away if I erase the "Composite" "Disable" line in my xorg.conf file. But it also turns off the acceleration, as I get mesadrivers when I type fglrxinfo in terminal. 

I'm trying envy with manual install option, maybe it will work this time lol

Exact same problem. I've tried EVERYTHING. Even my Ubuntu genius friend couldn't get it to work. We tried every single guide under the sun.


Although I just noticed this: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I don't have Linux installed becuase I got so frustrated with this, and this is the only thing I havn't tried, so if someone could tell me if it works that would be great.

---

### Post by Espreon on 2007-04-18
> **cantormath said:**
> ubuntu forgot nothing.  ATI will not make a driver for you to use linux.  They want you on windows.

Did you try envy?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Oh really, I use a Radeon X1400 , so why was ATI being sooooo nice to allow my graphics card to goto Linux heaven. Oh well I guess X1300s will have to stay in Windows hell!

---

### Post by Hobo Joe on 2007-04-18
> **Espreon said:**
> Oh really, I use a Radeon X1400 , so why was ATI being sooooo nice to allow my graphics card to goto Linux heaven. Oh well I guess X1300s will have to stay in Windows hell!

Why oh why did I not get a 1600?!

I rue that decision to this day.

---

### Post by crispy_420 on 2007-04-18
Get official ATI drivers and follow this howto:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by ambien on 2007-04-19
Thanks for the link, but I have tried that guide already. Is it possible that my BIOS needs to be updated? I'm running a 2002 motherboard, but Windows always worked fine with my current setup. I don't know what to try next.

---

### Post by Hobo Joe on 2007-04-19
> **crispy_420 said:**
> Get official ATI drivers and follow this howto:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Yeah, I've done that one too.  

*sigh*
I really wish it would work, becuase I just saw a video from Ubuntu that made me want it REALLY bad.

---

