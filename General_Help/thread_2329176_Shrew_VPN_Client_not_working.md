---
title: "Shrew VPN Client not working"
date: 2016-06-28
forum: General Help
---

### Post by cfaj2 on 2016-06-28
Hi 

I installed Shrew Soft VPN  Client to connect to our company IPSec VPN, but whenever I tried to connect it gives me an error as below:

[I]gateway authentication error
tunnel disabled
detached from key daemon

[/I]My Ubuntu is v14.04 LTS and my Shrew Soft VPN Client is v2.2.1[I].

[/I]Any idea why?

---

### Post by QDR06VV9 on 2016-06-28
"gateway authentication error" usually means that the identity 
information or the pre-shared key exchanged between the Shrew client and 
the gateway doesn't match up.
EDIT: If you can, export the Connection configuration from one of the other machines 
and import it into Shrew on your computer.

---

### Post by cfaj2 on 2016-06-28
runrickus thanks a lot.

after exporting and importing, everything just works....

---

### Post by QDR06VV9 on 2016-06-28
Hey that is Good news!:) And Good Job..
Now if you would mark this as Solved to help others looking for a solution.
Thanks and Kind Regards

---

