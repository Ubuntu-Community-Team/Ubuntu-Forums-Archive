---
title: "Possible to use upstart in dapper?"
date: 2006-11-09
forum: General Help
---

### Post by Tommerz on 2006-11-09
Hey everyone,

Does anyone know if there is a way to use upstart in dapper? Or to install some of the key new packages from edgy into dapper?

I'm guessing that just using the .deb files from edgy in dapper will lead to numerous incompatibilities and dependency problems, does anyone have any idea if this so?

---

### Post by bsussman on 2006-11-09
> **Tommerz said:**
> Hey everyone,

Does anyone know if there is a way to use upstart in dapper? Or to install some of the key new packages from edgy into dapper?

I'm guessing that just using the .deb files from edgy in dapper will lead to numerous incompatibilities and dependency problems, does anyone have any idea if this so?

I am not purposly trying to be cranky, but:

Upstart integration is tricky since it messes with some very basic   linux system bits.

(not specific to upstart):
1.  You would be running untested (integration testing is close to the most important kind) code so all bets would be null as to whether you might have a problem and reporting it would be tricky, since your environment is not a well known one.

2.  You would be well on your way towards running 6.10 anyway so what's the point?  Except maybe distributing something called tommerzbuntu ?  :)

3.  I suspect that backports is a term you want to learn about.

---

### Post by Tommerz on 2006-11-09
> 2. You would be well on your way towards running 6.10 anyway so what's the point? Except maybe distributing something called tommerzbuntu ?

Having used 6.10 a bit, I found it fairly buggy, and at the time also had a problem with ndiswrapper.

I also once tried a dist-upgrade and it broke the system :(

There's also the added advantage of dapper being lts, the only feature in edgy that really attracts me is upstart.

However, judging by what you said in your previous post, upstart in dapper would be buggier than a dist-upgraded edgy, so maybe to get upstart I'll just have to bite the bullet and upgrade. :( 

> 3. I suspect that backports is a term you want to learn about.

I know what backports are, I'm sure you'll agree the chances of upstart being backported to dapper are very slim.

---

### Post by bsussman on 2006-11-09
> **Tommerz said:**
> 
However, judging by what you said in your previous post, upstart in dapper would be buggier than a dist-upgraded edgy, so maybe to get upstart I'll just have to bite the bullet and upgrade. :( 

Maybe not buggier, but a significant challenge ( = to the edgy development work in this area).

I do not think the representations regarding 6.10's fitness for the general user community are very accurate.  They released it as a general release and warn that it is not as reliable as a general release.  When you go to ubuntu.com, you see 6.10 with no disclaimers.  In my world, general release is general release.  Based on the traffic in the forums, 6.10 shouldn't be.  So I think twice about using 6.10 for production.  Although I installed on my wife's (very plain firefox/openoffice/email) system, I am nervous.
> 
I know what backports are, I'm sure you'll agree the chances of upstart being backported to dapper are very slim.:) None is more like it...

I see and understand that theoretically upstart is better than init but I am having trouble seeing a compelling reason to hurry to install it.

---

### Post by Tommerz on 2006-11-10
I suppose what I want are the benefits of dapper, with the enhancements of edgy :) unlikely to happen, I suppose :(

One of the main reasons I want to use upstart is that booting takes so long on my laptop - otherwise, everything is hunky-doory, but the huge wait at start up is a real show stopper (especially waiting for wireless to configure itself, something I've heard won't work in edgy).

I could try initNG, although I'm unsure as to how reliable it is, I assumed upstart would be better being an official ubuntu package.

---

