---
title: "Ubuntu interferes with VOIP?"
date: 2021-05-28
forum: General Help
---

### Post by rsteinmetz70112 on 2021-05-28
I'm not sure what happened but last week one of my VOIP service stopped working the Voice light on the gateway went red and it wouldn't work. Restarting the gateway would allow it to work for a few minutes then it would fail again. The service is through ATT we contacted tech support an the dispatched a technician within a couple of hours. I was out of town trying to help remotely and logging into the gateway (router) and to our Ubuntu computers. All sorts of weird things were happening, pings would work then not work ssh would fail to find a computer with a static IP 10 feet away. Finally I began shutting down the Ubuntu computers and when I shut one of them down  and restarted the gateway it magically worked. After an hour of so I restarted the apparently responsible computer it has been working as usual for nearly a week.

Does anyone have any idea what may have happened to cause this. Since our connection is fiber and there is a media converter that converts the fiber to ethernet I'm not sure what could have caused the issue.
Any speculation?

---

### Post by TheFu on 2021-05-28
Bug/spider inside one of the systems?
Failing hardware?
Lightning strike?
Hiccup on the AT&T side that they didn't admit?

---

### Post by ajgreeny on 2021-05-28
Is there any possibility that your ISP is doing anything to cause this?

It may seem unlikely but I think some ISPs in the past have either throttled or completely banned the use of VOIP, though I've no hard evidence of this, just hearsay from third parties, and I should have thought it was not a problem these days.

---

### Post by rsteinmetz70112 on 2021-05-28
> **ajgreeny said:**
> Is there any possibility that your ISP is doing anything to cause this?

It may seem unlikely but I think some ISPs in the past have either throttled or completely banned the use of VOIP, though I've no hard evidence of this, just hearsay from third parties, and I should have thought it was not a problem these days.

We're paying them to provide VOIP so they shouldn't be doing it on purpose. But we've had some other odd occurrences which could be related to their equipment. For example for several weeks we could not access our bank's online banking from the office, but I could access it from anywhere else. Neither the Bank not ATT could explain it and one day it just started working again, with no changes on our end. It could have been something on their end causing it but I can't tell.

---

### Post by rsteinmetz70112 on 2021-05-28
> **TheFu said:**
> Bug/spider inside one of the systems? 
If I find a bug I'll tape it to the computer.
> Failing hardware?
They swapped out our gateway without solving the problem. It could of course be something further upstream.
We thought at one point it might have been a misbehaving or failing network switch, but it's been working fine since were got it running again.
> Lightning strike?
Not likely - no weather events, it went out in the middle of a clear day. I suppose there could have been an electrical event of some kind but it would have had to get through surge suppressors and backup power and as far as I know nothing else was affected.
> Hiccup on the AT&T side that they didn't admit?
This is my favorite theory, but it would have to be upstream from us. I don't know what they have in the building, and we're only two blocks from 12 story ATT Central Office. 
We've had some other weird occurrences recently.

---

### Post by mikewhatever on 2021-05-28
Yes it does? Ubuntu was maid with the sole purpose - to interfere with VOIP?
:~)?
:lolflag:

---

