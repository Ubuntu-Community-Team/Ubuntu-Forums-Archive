---
title: "Firefox 1.5.0.7 crashes"
date: 2006-11-03
forum: General Help
---

### Post by ahaslam on 2006-11-03
Hi,

I'm using Dapper & have started to experience persistant problems with Firefox. It's crashed before but after hours of use with multiple tabs. Today it crashed 4 times in the same hour with only 1 tab. I'm just wondering whether it's a problem with Firefox or the website. Here's the site: [http://www.autotrader.co.uk/](http://www.autotrader.co.uk/)

Is it the site, Firefox or simply my settings? All advice welcome.

Tony.

---

### Post by dcstar on 2006-11-04
> **Anthony Haslam said:**
> Hi,

I'm using Dapper & have started to experience persistant problems with Firefox. It's crashed before but after hours of use with multiple tabs. Today it crashed 4 times in the same hour with only 1 tab. I'm just wondering whether it's a problem with Firefox or the website. Here's the site: [http://www.autotrader.co.uk/](http://www.autotrader.co.uk/)

Is it the site, Firefox or simply my settings? All advice welcome.

Tony.

To test your settings, rename your hidden .mozilla directory and restart Firefox (this will create a fresh profile).

If it is now stable, copy any saved data (bookmarks etc.) from the renamed directory to the newly created one.

---

### Post by ahaslam on 2006-11-04
Thanks for your reply.
I don't believe that it's my browser settings, I've started using Opera 9 and it crashes in exactly the same way.
Another site which seems to cause frequent crashes on both browsers is: [http://maps.google.co.uk/maps](http://maps.google.co.uk/maps)

Cheers.

---

### Post by stream303 on 2006-11-04
Ok, this one may be a bit out there, but I had the same problem when I drove my graphics too hard with a low-memory video card.  Everything would be fine, but certain graphics-intensive sites would actually crash the whole machine.  (Old Dell GX-150 with on-board video)

I was using a 19" monitor in it's native resolution and the only fix was to reduce the depth from 24 down to 16 bits in my xorg.conf file.

Like I said, this is a shot in the dark ....

---

### Post by ahaslam on 2006-11-05
You're probably on to something there. Most problems I've encountered are either down to myself or my integrated Unichrome Pro graphics. 
When Firefox/Opera crashes, it only exits the browser & everything else is left unaffected. When a game/screensaver causes a crash, my whole system freezes. Though the symptoms aren't the same, I'll try using 16 bit for a while.

Cheers,

Tony.

---

