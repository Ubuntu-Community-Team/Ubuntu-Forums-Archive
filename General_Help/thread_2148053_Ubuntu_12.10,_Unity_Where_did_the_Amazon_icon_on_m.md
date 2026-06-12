---
title: "Ubuntu 12.10, Unity: Where did the Amazon icon on my desktop come from"
date: 2013-05-23
forum: General Help
---

### Post by ArlieS on 2013-05-23
I found an amazon icon on the bar at the left of the screen. It appeared not to be pinned, so *something* was presumably running. 

Investigation with ps gave me:

ps axlwww | grep -i amazon
0  1000 15414     1  20   0 464664 13956 poll_s Sl   ?          0:00 /usr/lib/libunity-webapps/unity-webapps-context-daemon Amazon [www.amazon.com]("http://www.amazon.com") icon://amazon-store [Invalid UTF-8] ubuntu-amazon-default.desktop

I got rid of it with "kill 15414" - but where did it come from, and how do I make sure it doesn't come back? 

Is this the price I pay for installing security patches to ubuntu 12.10?

Advanced question - how many more of these goodies are part of ubuntu desktop, and is there a convenient way to extirpate the lot of them? If I wanted a PC full of partner shovelware, I'd have bought a windows PC from just about any major vendor. I get really unhappy when vendor-ware runs on my system without an explicit conscious request from me.

[Edit - I just found this piece of suspicious software of unknown purpose. What is it and why is it running on my desktop?

 ps axlwww | grep webapps
0  1000  3206     1  20   0 267520  3404 poll_s Sl   ?          0:00 /usr/lib/libunity-webapps/unity-webapps-service

---

### Post by Frogs Hair on 2013-05-23
I have noticed that the Ubuntu One music icon and Amazon icon tend to reset on the launcher after Unity specific updates. This is not immediate but they appear on the next boot.

---

### Post by ArlieS on 2013-06-03
Bump! The icon and associated unwanted process keeps coming back. I have not found any documented way to turn it off permanently, perhaps because documenting "Unity" is not a priority. Do I need to file a bug?

---

### Post by ArlieS on 2013-06-03
I took my problem to IRC. 

You can get rid of some of the problem with

"sudo apt-get remove unity-lens-shopping"

or the equivalent via the GUI

But basically it's part of the direction Unity is going. See [http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

See also: [http://askubuntu.com/questions/192269/how-can-i-remove-amazon-search-results-from-the-dash?rq=1](http://askubuntu.com/questions/192269/how-can-i-remove-amazon-search-results-from-the-dash?rq=1)

I've got some other notes on how to completely extirpate this misfeature, but I haven't tried them. I'll post them if (a) I turn out to need them and (b) they work for me ;-)

And damn, I love 90% of ubuntu, but this is the kind of thing that pushes me towards looking for an alternate distro.

---

### Post by jefelex on 2013-06-04
it's for this exact reason I'm staying with natty - and if I can't get the repository issue (no support - that's alright, but have to update where the repository went to) I'll probably switch to something else

---

### Post by ahallubuntu on 2013-06-04
~

---

### Post by BBQdave on 2013-06-04
> **jefelex said:**
> it's for this exact reason I'm staying with natty

Ubuntu Unity 12.04LTS does not have expanded web search - *Shopping Lens* - in the Dash.

Unity releases from 12.10 on have the expanded web search built into Dash - Amazon, BBC, Facebook, and others. You can limit the scope of search through Dash - not include web searches - in System Settings > Privacy. The expanded search in Dash is still developing, and I believe it's full function is targeted for the next LTS release.

---

