---
title: "Where can I find Compiz?"
date: 2008-06-12
forum: General Help
---

### Post by the lemming on 2008-06-12
I have come back to Ubuntu after a year of leaving it alone and to help me on my "learning curve" I have decided to remove XP and only have 8.04 on my laptop.

One of my "learning curve" problems is trying to find where Compiz is.  Anybody able to point me in the right direction to find Compiz so that I can configure it?

I have found System, Preferences, Apearance, Visual Effects and chose Extra.
Problem is that I can't find anywhere for Compiz.

Cheers

---

### Post by Grishka on 2008-06-12
if you have visual effects and they work, then you have Compiz as well. it comes preinstalled with new Ubuntu versions. to get a Compiz configurator, install compizconfig-settings-manager. also, installing fusion-icon will make using Compiz as you like much easier.

---

### Post by steveneddy on 2008-06-12
> **the lemming said:**
> 
I have found [COLOR="Red"]**System, Preferences, Apearance, Visual Effects and chose Extra**[/COLOR].
Problem is that I can't find anywhere for Compiz.



That path turns on Compiz.

---

### Post by the lemming on 2008-06-13
> **steveneddy said:**
> That path turns on Compiz.



I've done that but how do I get to the Compiz section where I can adjust everything?

Cheers

---

### Post by Grishka on 2008-06-13
> **the lemming said:**
> I've done that but how do I get to the Compiz section where I can adjust everything?

Cheers

I've answered your question in my previous post. what's the point of asking questions, if you can't even be bothered to read the answers you get?

---

### Post by the lemming on 2008-06-13
> **Grishka said:**
> I've answered your question in my previous post. what's the point of asking questions, if you can't even be bothered to read the answers you get?



I have ticked the extra feature and I get wobbly windows.  However when I use other Distros I get an entire section on Compiz that allows me to do more than just wobbly windows.  I am just looking for that, OK?

Now if you can't be civilised in your replies to my enquiry may I suggest that you don't even bother replying to me?

---

### Post by Grishka on 2008-06-13
> **the lemming said:**
> I have ticked the extra feature and I get wobbly windows.  However when I use other Distros I get an entire section on Compiz that allows me to do more than just wobbly windows.  I am just looking for that, OK?

Now if you can't be civilised in your replies to my enquiry may I suggest that you don't even bother replying to me?

civilisation makes us into robots. :) one can only live his live to it's fullest by embracing the wild aspects of his nature, so to speak. but I apologise, my intention was not to offend. I am too blunt at times. anyway, do this:
from the terminal type:
sudo aptitude install compizconfig-settings-manager fusion-icon
or look for these packages in Synaptic.
then run fusion-icon. eg. press Alt+F2 and type "fusion-icon" in the box. or better yet, put it in your autostart through the Preferences/Sessions menu. you'll get a blue icon on your panel, near the clock. right click it and choose "settings manager". you can also run it by hand. the command for compiz configurator is "ccsm". hope that helps.

---

### Post by the lemming on 2008-06-13
> **Grishka said:**
> civilisation makes us into robots. :) .

Thanks for your help and advice.  I've managed to get the compiz setup to work so all I have to do now is get a few more features to work.

Cheers

---

