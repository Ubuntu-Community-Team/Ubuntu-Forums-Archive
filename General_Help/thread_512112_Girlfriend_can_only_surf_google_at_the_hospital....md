---
title: "Girlfriend can only surf google at the hospital..."
date: 2007-07-28
forum: General Help
---

### Post by Ripfox on 2007-07-28
My GF's sister had to go to the hospital for a few days. Recently i convinced her to switch from Win to Ubu...everything has been fine, but for some reason she could only surf Google's websites from the unsecured wireless connection at the hospital. I went there and checked it out myself, and yep, it just times out when you click a link outside of google. One thing I tried is to disable the ATI  accelerated driver, and at that point, it stopped showing the hospitals home page and went straight to google (which seemed to hijack her Google homepage when you start Firefox) But as before, no go on anything outside of a google related url.

Here are some specs:

HP DV5000
ATI mobility graphics
Feisty Fawn
wicd manager for wireless (which has worked flawlessly for me on my DV6000 on MANY different wireless networks)

Any ideas? :)

---

### Post by KyleBrandt on 2007-07-28
Are you sure that the hospitals WAP lets people view pages outside of google? They may limit their service to google only, which is strange, but sounds like the most likely explination.  My only other guess would be that google's pages are cached on the machine.

Just for fun: You strange problem reminds me of this: [http://www.ibiblio.org/harris/500milemail.html](http://www.ibiblio.org/harris/500milemail.html)

---

### Post by Ripfox on 2007-07-28
Yes, it surfs fine with a windows OS. This is an Ubuntu problem as far as I can tell. Something is nagging at me telling me it has to do with the ATI card taking up resources or something. I used to have this terrible problem with the synaptic pointing device and figured out that it was a problem related to the wireless driver taking up resources needed by the pointing device or something...only way I cured that was to install a program to control the pointer in gnome and even that hasn't been perfect.

---

### Post by ThrobbingBrain66 on 2007-07-28
If driver conflict was the case, I think the wireless wouldn't work anywhere, not just at the hospital.  Have you tried different browsers on Ubuntu (Opera, flock, etc)?  What if you used the User Agent Switcher for Firefox and pretend to be IE (very unlikely that would work, but just for kicks).

---

### Post by Ripfox on 2007-07-28
I suppose I could try those things...but what good would a different browser do in theory? I understand the agent switcher thing, but I really don't see how that would effect the entire web, maybe just a few choice websites from working...

btw nice avatar throbbingbrain, more cowbell might be the answer to my problem?

---

### Post by ThrobbingBrain66 on 2007-07-28
More cowbell is the answer to everything!

I guess I don't have any concrete reasoning behind my suggestions, but your problem just seems very odd to me.  I'm trying to narrow down the possibilities.

I suppose a bug could be preventing Firefox from surfing the hospitals conifguration (is that even possible?).  Trying a different browser with a different engine may help.  Other than that, they were just ideas that popped into my head :)

---

### Post by DaveAK on 2007-07-28
I work at a hospital and we have a public wifi that's wide open, (but off our network of course!)  I've surfed it just fine with Ubuntu.  However, you might find that the hospital you're at has a different setup and some strange security policy preventing web access.  Not really my area of expertise, just throwing it out there. :)

---

### Post by KyleBrandt on 2007-07-29
Is my second idea, that google is cached in firefox, and firefox is not working at all, still a possibility?  Another idea along the same lines, firefox in ubuntu is set to use a proxy server?  Lastly, try pinging google, and then ping other sites, see what this gets you.

---

### Post by Ripfox on 2007-07-29
I successfully pinged ubuntu website with NO problems...and I have firefox set to delete all cookies ect when firefox exits. Is Firefox set to use a proxy server by default?

---

### Post by Ripfox on 2007-07-29
> **DaveAK said:**
> I work at a hospital and we have a public wifi that's wide open, (but off our network of course!)  I've surfed it just fine with Ubuntu.  However, you might find that the hospital you're at has a different setup and some strange security policy preventing web access.  Not really my area of expertise, just throwing it out there. :)

That's what I was thinking, but it seems weird. It's fine with Firefox and Win.

---

### Post by imdano on 2007-07-29
Can you do stuff like apt-get installs/searches?

---

### Post by rich.bradshaw on 2007-07-29
Probably is the user agent.

---

### Post by Ripfox on 2007-07-29
Can't apt-get anything, and Synaptic won't download any packages, but like I mentioned before, I can ping any site from the terminal.

---

### Post by Ripfox on 2007-07-29
Can't be the user agent. It works with firefox under windows....

---

### Post by DaveAK on 2007-07-29
> **ripfox said:**
> I successfully pinged ubuntu website with NO problems...and I have firefox set to delete all cookies ect when firefox exits. Is Firefox set to use a proxy server by default?
So is it resolving addresses OK?  I.e. it's not a DNS issue?  My FireFox isn't set to use a proxy, (check under Edit | Preferences | Advanced | Network | Settings).

---

### Post by KyleBrandt on 2007-07-29
This is so strange.  Couple more ideas, try a different browser, maybe just lynx or something.  Also, maybe someone has messed around with a firewall / iptables on the laptop?

---

### Post by Ripfox on 2007-07-30
> **DaveAK said:**
> So is it resolving addresses OK?  I.e. it's not a DNS issue?  My FireFox isn't set to use a proxy, (check under Edit | Preferences | Advanced | Network | Settings).

No it is set t "direct connection to the internet"
This is practically a fresh install, no no ne has messed with the settings except me. :confused:

---

