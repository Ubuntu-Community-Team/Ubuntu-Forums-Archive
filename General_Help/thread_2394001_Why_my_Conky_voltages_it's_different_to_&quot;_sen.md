---
title: "Why my Conky voltages it's different to &quot; sensors &quot; command in terminal ?"
date: 2018-06-11
forum: General Help
---

### Post by henrique-rj on 2018-06-11
Hello !!!

I have the follow problem.

Why my Conky voltages ( +5,0V and +12,0V ) are differents to " sensors " command in terminal ?

In Conky +5,0V show +3,1V and +12,0V show +3,0V.

In terminal ( " sensors " command ) +5,0V show +5,04V and +12,0V show +11,94V.

I have in /etc/sensors.d/sensors the follow script:

> chip "it87-*"

label "Vbat"

compute in3 @*((6.8/10)+1), @/((6.8/10)+1)
compute in4 @*((28/10)+1), @/((28/10)+1)

I too executed the command " sensors-detect " in terminal and reboot my system.

How solve it ?

Thanks very much !!!

---

### Post by henrique-rj on 2018-06-12
I try in conky.conf, " +5V:${hwmon 1 vol 3} ${@*((6.8/10)+1), @/((6.8/10)+1)}V " and others combinations but without results.

---

### Post by henrique-rj on 2018-06-15
eureka !!!

I solved it whit fowlling script in /etc/sensors.d/sensors.conf

```

chip "it87-*"

label in8 "Vbat"
    
compute in3 @*((6.8/10)+1), @/((6.8/10)+1)
compute in4 @*((30/10)+1), @/((30/10)+1)

compute fan1 @/4, 2*@
compute fan2 @/4, 2*@

```

And aditional script in ~/.conkyrc

After

+5,0V:${hwmon 1 vol 3}V

Before

+5,0V:${exec sensors | awk '/in3/ { print $2 }'}V

---

