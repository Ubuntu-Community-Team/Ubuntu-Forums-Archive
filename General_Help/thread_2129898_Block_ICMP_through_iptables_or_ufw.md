---
title: "Block ICMP through iptables or ufw?"
date: 2013-03-27
forum: General Help
---

### Post by daKoolaid on 2013-03-27
What is the better of the two?

[FONT=FreeMono][SIZE=2]iptables -A INPUT -p icmp -m icmp --icmp-type echo-request -j DROP[/SIZE][/FONT]

or 

gedit /etc/ufw/before.rules 

[COLOR=#333333][FONT=FreeMono][SIZE=2]-A ufw-before-input -p icmp --icmp-type echo-request -j [/SIZE][/FONT][/COLOR][COLOR=#333333][FONT=FreeMono][SIZE=2]DROP[/SIZE][/FONT][/COLOR]
 
I've read that ufw can overwrite iptables rules sometimes on updates, is this true?

Thanks!


Edit: I can find no difference other than that the iptables line enterend into terminal is not permanent. Also I find that REJECT is better to use than DROP.

---

### Post by jonobr on 2013-03-27
> Also I find that REJECT is better to use than DROP. 
It depends what you want.
A reject indicates to the source that there is a device there with an IP stack.
A drop will discard and not inform the source.

I would prefer if I was securing my network not to let a ping inform the source and just drop, but again, you mayu be doing things differently

---

### Post by daKoolaid on 2013-03-27
I'm not doing anything particular where I would need reject over drop. I only say that because I found two links on the forum here which explain why reject would be the better choice. ICMP drop still lets someone pinging you know that there's someone there, it just takes longer and ties up network and system resources longer.

[URL="http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/"]http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/
[/URL][http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

---

