---
title: "New Transmission is blocking standby"
date: 2008-05-27
forum: General Help
---

### Post by frediE on 2008-05-27
I am running the new version of Transmission Bittorrent client (version 1.21 from getdeb) and it is very nice except it is blocking me from going into standby (suspend) until I close the application.  I did not see anything in the preferences to disable this.

This is the message I get in a little pop-up window.
"Request to do policy action Transmission Bittorrent Client has stopped the policy action from taking place: BitTorrent Activity."

Any suggestions would be great.

---

### Post by frediE on 2008-09-22
Looks like it is still happening in Transmission version 1.34.

---

### Post by adamorjames on 2008-09-30
I am using Arch Linux with GNOME 2.22.3, and am having the same problem and using version 1.34.

---

### Post by C0d3Runr on 2008-10-05
This has been reported as a Transmission bug; see [http://trac.transmissionbt.com/ticket/1317](http://trac.transmissionbt.com/ticket/1317)

---

### Post by jmjohn on 2008-11-05
Does anybody know any command-line voodoo or otherwise to prevent Transmission from blocking sleep?

Thanks much,
glass.dimly

---

### Post by frediE on 2008-11-05
you see, if enough of us get together... you might spark something... what a concept... haven't tried it yet but... i found the following in the transmission config file (~/.config/transmission).

```
inhibit-hibernation=true
```

try changing it from true to false and see what happens.  :-)

---

### Post by zain3000 on 2008-11-17
> **frediE said:**
> you see, if enough of us get together... you might spark something... what a concept... haven't tried it yet but... i found the following in the transmission config file (~/.config/transmission).

```
inhibit-hibernation=true
```

try changing it from true to false and see what happens.  :-)

Wow, thanks for the tip! I was having the same problem, and your suggestion worked like a charm. I guess in Ubuntu where there's a will, there's a way :)

---

