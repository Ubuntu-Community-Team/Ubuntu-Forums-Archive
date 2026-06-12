---
title: "Feisty DHCP problem"
date: 2007-04-28
forum: General Help
---

### Post by vladimiroane on 2007-04-28
Here is what happens. I have my wired connection set up to dhcp.
If I start Ubuntu when the network cable is plugged in ..... i have no problem. Ubuntu finds my connection... it gets an IP and Internet works great.
But if Ubuntu starts and then I plug in the network cable.... I get an active connection to the network but I can not connect to the Internet because the system doesn't have an IP. If I restart Ubuntu everything is fine.
Any idea?

---

### Post by myjess on 2007-04-28
Well, I do know from my limited experience, that you can run sudo dhclient, and a new ip address should be available to you.

Otherwise there is a network management tool in Feisty that installs by default and will auto do that for you I think.

---

### Post by vladimiroane on 2007-04-28
well that tool doesn't work as it should I guess.

---

### Post by zvacet on 2007-04-28
```
pon dsl-provider
```

Did you look in DNS tab?It should be your nameserver there.If it is not add it and delete everything else.

```
sudo pppoeconf
```

This should keep your connection with resolv.conf

---

### Post by fragos on 2007-04-28
I've noticed that on my box, for DCHP to work, from boot up, I need to power down the system at my power strip or my system will continue to use the last IP and DNS that it had.  Shutdown really isn't fully powered down.  This isn't quite the same as what you're doing but perhaps it will give you a clue.

---

