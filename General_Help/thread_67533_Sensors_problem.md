---
title: "Sensors problem"
date: 2005-09-20
forum: General Help
---

### Post by User-007 on 2005-09-20
How to enable gkrellm or KSensors showing also voltages and FAN speeds? I can't enable them anywhere.

Thanks in advance
Pate

---

### Post by KingBahamut on 2005-09-20
I believe thats lmsensors that needs to be installed for that.

---

### Post by User-007 on 2005-09-20
The LMSensors is installed. So CPU is shown but I cannot enable fan speeds or voltages to shown anywhere, My MB is ABIT KV7.... any suggestions?

Pate

---

### Post by User-007 on 2005-09-21
Problem solved!

I only ran

modprobe i2c-viapro

and then

sudo sensors-detect

and then answered for all questions.

And now, all works like a charm.

Pate

---

### Post by antidrugue on 2005-10-05
You're good!

Simple, and works like a charm (after reloading the modules) !

---

