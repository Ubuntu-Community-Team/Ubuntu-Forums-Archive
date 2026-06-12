---
title: "[SOLVED] Girlfriend lags me up badly :("
date: 2008-03-27
forum: General Help
---

### Post by Tomatz on 2008-03-27
I have a dilemma :(

I like to play quake wars online of an evening. The trouble is my girlfriend has an eeepc which lags me up badly while playing etqw online on the desktop. Both run gutsy the eeepc connects wirelessly and the desktop is connected via Ethernet to the to the same router.

Can i throttle the bandwidth on the eeepc so my girlfriend doesn't keep causing me to (embarrassingly) die???    

:confused:

---

### Post by MONODA on 2008-03-27
you could try to use the internet at different times...

---

### Post by Tomatz on 2008-03-27
> **MONODA said:**
> you could try to use the internet at different times...

Hilarious :mad::mad::mad:

---

### Post by Jameo on 2008-03-27
I have the same problem playing COD4 online lol, you could try swapping her for a girl on second life I guess :)

---

### Post by Tomatz on 2008-03-27
> **Jameo said:**
> I have the same problem playing COD4 online lol, you could try swapping her for a girl on second life I guess :)

Dang you should have said that 4 children ago :(

:lolflag:

---

### Post by Tomatz on 2008-03-27
Anyone?

---

### Post by p_quarles on 2008-03-27
This depends entirely on the functionality of your router. Look at the configuration interface and see if it includes any throttling functions.

---

### Post by Tomatz on 2008-03-27
[edit]

---

### Post by Tomatz on 2008-03-27
> **p_quarles said:**
> This depends entirely on the functionality of your router. Look at the configuration interface and see if it includes any throttling functions.

No the router doesn't its a cheap belkin. I was hoping that i could do this via software/commands on the eeepc so i could eaisly throttle more or less bandwidth.

---

### Post by fsmithred on 2008-03-27
Look into traffic shaping with dd-wrt or openwrt, and see if your router is supported. There may even be some QoS settings in your current router firmware that will do what you want.

---

### Post by Tomatz on 2008-03-27
I'll look into that thanks :)

It would be nice if i could just do this on the eeepc though.

---

### Post by p_quarles on 2008-03-27
> **Tomatz said:**
> I'll look into that thanks :)

It would be nice if i could just do this on the eeepc though.
You might be able to do that, but it would depend on the wireless card's capabilities. It would also require you to familiarize yourself with iwconfig, as none of the GUI network managers I've used are able to do this.

Basically, you would connect to the router using the "rate" option in iwconfig. This may not work, though, as even many cards that support multiple rates may not support a rate that is low enough to effectively restrict the Eee's broadband consumption.

---

### Post by olejorgen on 2008-03-27
Look into shaper or trickle

---

### Post by Tomatz on 2008-03-27
[SOLVED]

I suppose this is only a partial fix as its not a system wide solution. It was only firefox on my GFs computer that was hogging all the bandwidth so this fix only applies to firefox (but could be easily changed to work with other apps).

Here goes:

**sudo apt-get install trickle**

**sudo gedit /usr/bin/tricklefirefox**

Add the following to the file:

**trickle -d 30 firefox**

Save

**sudo chmod a+x /usr/bin/tricklefirefox**

Then add a launcher/menu launcher with the command **tricklefirefox**

This will start firefox throttled down to 30kbps when you click the launcher. Tweak to your hearts content :)

---

### Post by forrestcupp on 2008-03-27
I'll bet she's not too happy about that.

---

### Post by Tomatz on 2008-03-27
She'll never know muhhhaha!

:lolflag:

---

