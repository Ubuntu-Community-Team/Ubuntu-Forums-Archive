---
title: "security question: open ports"
date: 2008-07-09
forum: General Help
---

### Post by weissnich on 2008-07-09
hi,

i did a quick port scan with the tool included in ubuntu and sometimes only port 631 is open (ipp), but several times there a some other ports open.
Somtimes it is 38805, 54369 and then 46716 or 33204, 56708 and so on.
Any clue why there are these changing open ports?
I am behind a firewalled router.

---

### Post by unoodles on 2008-07-09
try this to see what is accessing ports and whether they are local or not.
sudo netstat -tupl

---

### Post by brian_p on 2008-07-09
> **weissnich said:**
> hi,

i did a quick port scan with the tool included in ubuntu and sometimes only port 631 is open (ipp), but several times there a some other ports open.
Somtimes it is 38805, 54369 and then 46716 or 33204, 56708 and so on.
Any clue why there are these changing open ports?
I am behind a firewalled router.

My guess would be processes related to printing, which will be printer dependent.

sudo lsof -i :<port number>

will tell you.

---

### Post by weissnich on 2008-07-09
I don't get any information about those ports,
seem to be unknown.
Netstat doesn't say anything about those open ports, so I don't know what this is.

---

