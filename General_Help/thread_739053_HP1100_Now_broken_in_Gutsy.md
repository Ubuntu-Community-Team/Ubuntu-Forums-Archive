---
title: "HP1100 Now broken in Gutsy"
date: 2008-03-29
forum: General Help
---

### Post by chromedome on 2008-03-29
My printer is an elderly but functional HP 1100.  I'd originally installed it under 6.10, and it worked fine...I just said yes to all the defaults, and life was good.  Recently I did a clean install of Gutsy, and again, it was trouble-free...no tweaking required.

About two days ago, though, the daily software update brought me a new version of HPLIP.  I can't say absolutely that this is my problem, but ever since it was installed my printer won't run.  I have worked my way methodically through the foomatic and Gutenprint drivers, and none of them work.  Nothing has changed physically.  I have used Synaptic to uninstall and re-install everything related to HP printers.

Any suggestions?

(Linux noob, but I go back to DOS 3.0 so I'm comfortable with CLI)

---

### Post by chromedome on 2008-03-29
I should have specified... it's the LaserJet 1100, not the inkjet model of the same number.

---

### Post by chromedome on 2008-04-02
<bump>

Anyone?  Class....class....Bueller?

---

### Post by chromedome on 2008-04-07
Never mind, brain fart on my part.  Sorted it out for myself.

---

### Post by Phosphoric on 2008-04-09
> **chromedome said:**
> Never mind, brain fart on my part.  Sorted it out for myself.

Hi, care to lets us know how you fixed it.  We can all make mistakes from time to time and hopefully learn from other's. :)

---

### Post by chromedome on 2008-04-11
Just a stupid thing, of course...the default became "HP1100 LPT parport", and the printer crapped out until I switched it to "HP1100 LPT#1".  

(facepalm)

---

