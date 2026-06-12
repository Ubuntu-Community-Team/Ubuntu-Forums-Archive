---
title: "Share keyboard over network (Console)"
date: 2006-07-28
forum: General Help
---

### Post by SigmaX on 2006-07-28
Yo;

I just setup a couple of old boxes without GUI's (Debian and FreeBSD) next to my Ubuntu system.  I've used synergy in the past to share keyboard and mouse over various GUI's and OS's.  I'd like to use something similar with the getty's, so I don't have to keep three keyboards sprawled out.

Know anything that'll accomplish this?  

SigmaX

---

### Post by OpsVentus on 2006-07-28
Can't you just use ssh?
If it hasn't got GUI anyway.

Cheers,
Bart.

---

### Post by it.henrik on 2006-07-28
I know there is something similar .. had a friend how got his three boxes next to each other and the mouse flowed seamlessy over them ... 

One thing you can do is to set up all monitors to one box and then use VNC to get the other desktops on different screens etc etc .. im doing that with my laptop and servers right now

---

### Post by SigmaX on 2006-07-28
I think I miscommunicated.

SSH is grand for remote access, GUI and console, but the idea is to use all three boxes *and* all three of their monitors.  VNC is similarly defeated by this facet.

Synergy is the app that allows sharing of keyboard and mouse with *GUI*, but I'm talking console.  I suppose it's even more complex then that, though: One box is using X, the other two aren't :-P.

A KVM-like solution isn't easily available either, as each system has a different type of keyboard port (One's an old Mac, in fact).

SigmaX

---

### Post by it.henrik on 2006-07-29
ok... but Im back to connecting all three monitors to the computer that is running X. get the two other connected over SSH and just maximize the gnome terminals on one monitor each... 

Sounds like a working solutions to me :)

---

### Post by SigmaX on 2006-07-30
> **it.henrik said:**
> ok... but Im back to connecting all three monitors to the computer that is running X. get the two other connected over SSH and just maximize the gnome terminals on one monitor each... 

Sounds like a working solutions to me :)

Mmkay, so I go out and buy two extra graphics cards?

That defeats the purpose.

I guess I'll just juggle three keyboards for now.

SigmaX

---

### Post by OpsVentus on 2006-07-31
You could make a kind of box to switch the keyboard physically to the 3 computers.
Eather a simple switch for 4 wires or, if you are able to solder some parts together, some relays.
Put 3 buttons in front of your keyboard to control the relays behind it.
I can draw a electric drawing if your interested.

Cheers,
Bart.

---

### Post by SigmaX on 2006-08-01
That would be feasable, except each keyboard has a different connector.  One is AT, one is PS/2, and one is the old Apple 4-pin miniDIN.  If somebody can provide me a schematic that includes conversion to PS/2, that'd be grand, but I'm pretty accustomed to juggling three keyboards, so in light of no software solution I suppose I'll give up and stick with SSH and/or juggling.

SigmaX

---

