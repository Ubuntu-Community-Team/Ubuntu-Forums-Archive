---
title: "Getting Amarok to recognize my iPod. (Warning: Noob)"
date: 2007-02-24
forum: General Help
---

### Post by Fireblend on 2007-02-24
Hey! I'm a total noob, so bear with me, all I want is to be able to listen to mi iPod while using Ubuntu. So, I downloaded Amarok which seems to be the best application around to do so, also I got gtkpod (got them both from the add/remove... thing).

So, gtkpod works well and detects my iPod, so all seems to work fine. Now, Amarok is asking me to configure my iPod and it asks for a pre-connect and post-diconnect command. What is that supposed to mean? Also, I keep hearing about libgpod or something like that and I just don't know how to install that or if I need it if I already have gtkpod working.

So, I'd be really glad if someone could guide me step-by-step on how to do this, as I just don't know what I'm doing. Isn't there some set of commands I can post on the terminal or something?

Isn't there some easy way to do this? >_<

Also, I realize that I must sound stupid, using all the wrong terms, but this is really different to me; I've been using ubuntu for about a hour now, so you see, I'm new here.

---

### Post by nrune on 2007-02-25
Okay open my copy of amarok go to :
Configure > media devices 

Click add device

Select plugin to use 
change to Apple iPod Media Device

Enter a name for this device
iPod

Enter the Mount Point of the device
/media/ipod

save And you should be good to go

Don't forget to disconnect in amaork when done and then to unmount from desktop before disconecting from ipod.

Enjoy and Have FUN

---

### Post by bhartsock on 2007-02-25
If you get a lockfile error in Amarok, check out this thread:

[http://ubuntuforums.org/showthread.php?p=2212329]("http://ubuntuforums.org/showthread.php?p=2212329")

---

