---
title: "Doubleclick.net in browser config?"
date: 2007-03-23
forum: General Help
---

### Post by Jagermaster on 2007-03-23
I typed "about:config" in my browser and one of the lines looked like this.

[COLOR="Red"]network.dns.ipv4OnlyDomains .doubleclick.net[/COLOR]

Can someone help me understand why it's there?
Good? Bad?

Thanks,
B

---

### Post by bettlebrox on 2007-03-23
Google is your friend! :p

[http://kb.mozillazine.org/Network.dns.ipv4OnlyDomains](http://kb.mozillazine.org/Network.dns.ipv4OnlyDomains)
[INDENT]
The default setting for this preference does not mean that Mozilla will ever contact doubleclick.net (an internet ad company) if it is not requested, it just specifies which IP version to use if it is requested. doubleclick.net ads are present on many sites, and removing this entry will delay the loading of those sites. If you not wish to ever connect to doubleclick.net, use an extension such as Adblock - do not change the value of this preference.[/INDENT]

So it's a good thing, and not something to worry about. :)

---

### Post by Jagermaster on 2007-03-23
Hey,
Thanks for that reply!
I see things like that and I break out in hives...:lolflag: 

Good to know it kinda belongs there.
Peace,
B)

---

