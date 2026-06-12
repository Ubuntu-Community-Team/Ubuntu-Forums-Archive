---
title: "Laptop Asus X51SE doesn't work sleep mode, the battery too fast uncharge"
date: 2023-07-22
forum: General Help
---

### Post by vefire on 2023-07-22
Hello everyone!
This year I bought the laptop Asus X51SE (begginer level) and installed Ubuntu 22.04.2 LTS (Desktop).
Almost all works fine (as far I can guess), except battery when I close the laptop lid.
Battary uncharges like when laptop lid is open (aproximately 2.5 hours for full uncharge). I have no any of powerfull background services like docker or else.
I tried to set differents of energy modes, but it didn't bring any sense.
I tried to edit file /etc/systemd/logind.conf and set next value (instead default suspend)
[B]HandleLidSwitch=hibernate
[/B]and also it didn't help for me.
I will appreciate for help. 

ps
I asked tech support Asus for that problem, they answered that recommended OS for laptop is Windows 11, for another OS's they can't give any guarantees.

---

