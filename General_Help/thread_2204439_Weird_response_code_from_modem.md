---
title: "Weird response code from modem"
date: 2014-02-08
forum: General Help
---

### Post by NickD-NLUG on 2014-02-08
Hi,

Trying to get ncidd ( the Network Called ID sourceforge project ) to hangup on blacklisted numbers, and it recognises them, but this is what I get in the logs:

RING
CIDINFO: *LINE*POTS*RING*2*TIME*18:08:58*
Blacklist Match #01: 00000-123456    number: 00000-123456    name: NO NAME
Sent Modem 4 of 4 characters: 
AT
Modem response: 11 characters in 2 reads:

&#65533;T
OK
Sent Modem 7 of 7 characters: 
AT H1
Modem response: 15 characters in 7 reads:
&#65533;C&#65533;&#65533;%&#65533;I5

I'm perplexed by that last response, any ideas?

---

### Post by xren69 on 2014-02-12
Hi Nick, 

Have you set the modem to the correct country? This is one thing that set me back on my set up. The easiest way I found to do this was to use a windows machine, then select properties and you can then select the correct counry from there. I see that you have also posted this query on the NCID support log, John and Todd on there are very helpful and have already replied to your post, when I had my issues those two, along with other, were very supportive and did fix my errors. If you can tell them/me more about your set up then hopefully we can get you up and running.

Cheers

---

### Post by NickD-NLUG on 2014-02-12
Ah, thanks for the tip - I thought I'd subscribed to updates on that thread but obviously not...

---

