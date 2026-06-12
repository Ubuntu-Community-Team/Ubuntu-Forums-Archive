---
title: "Wifi really slow in Ubuntu 15.4 sometimes not at all"
date: 2015-08-07
forum: General Help
---

### Post by kapi on 2015-08-07
Just installed 15.4 as 14.4.2 was a disaster, everything seemed to go wrong.

15 seems ok so far, had a couple of teething problems but generally ok so far.

The only thing that seems to persist since I installed last night is the wifi sometimes goes really slow or doesn't connect and I get a message in the browser saying something about ' probe possible'

Apologies if I sound a bit vague. Has anyone else experienced something similar.


Regards

Cobber

---

### Post by Frogs Hair on 2015-08-07
You could check for a proprietary wireless driver in software sources > additional drivers.

---

### Post by monkeybrain20122 on 2015-08-07
What is your wifi card? 
Run
```
lshw -C network
``` 
and paste the output.

---

