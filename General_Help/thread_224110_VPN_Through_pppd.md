---
title: "VPN Through pppd"
date: 2006-07-27
forum: General Help
---

### Post by djcrash1981 on 2006-07-27
Someone know how i can set up this?? Because i want to make it work so i can do a vpn on my workplace.
I found this walkthrough but is for slackware and i was going to give it a try but i thought to give it a try here first

[www.kraftek.com/blog/index.php?/archives/113-Building-a-VPN-with-ppp-over-ssh-within-2-linuxes.html](www.kraftek.com/blog/index.php?/archives/113-Building-a-VPN-with-ppp-over-ssh-within-2-linuxes.html)

If someone know how i can do it please let me know :D

Or if someone know how to do a VPN through a firewall with ssh tunneling or something like that please give me an advice.

---

### Post by gesho on 2006-07-27
your workplace should have some kind of support for that.
at my uni following two links helped:
[http://kb.iu.edu/data/akct.html](http://kb.iu.edu/data/akct.html)
[http://kb.iu.edu/data/akcx.html](http://kb.iu.edu/data/akcx.html)
and there also was a script: 
[http://ussg.indiana.edu/index9181.html](http://ussg.indiana.edu/index9181.html)

most of this are kind doable. pppd options caused me some trouble, eventually I deleted most of the options leaving just a few advised by our support guy.

---

### Post by mbeierl on 2006-07-28
I've used this as a reference many times before:
[http://www.tldp.org/HOWTO/ppp-ssh/](http://www.tldp.org/HOWTO/ppp-ssh/)

VPNs over ssh are kinda erratic (as far as throughput speed goes - that's what happens when you do tcp over tcp) but they are generally reliable.


Happy working from home!

---

### Post by djcrash1981 on 2006-08-07
Its possible to do, what it says on that manual. So you can use it as a reference if your trying to do a VPN through pppd.

---

