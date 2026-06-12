---
title: "Boot logging 19.04"
date: 2019-07-07
forum: General Help
---

### Post by habana on 2019-07-07
I am trying to sort out a few problems on my system. Here is the partial output of ```
journalctl -b

```
```
Jul 08 06:53:15 computer2 kernel: input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Jul 08 06:53:15 computer2 kernel: ACPI: Power Button [PWRB]
Jul 08 06:53:15 computer2 kernel: input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul 08 06:53:15 computer2 kernel: ACPI: Power Button [PWRF]
Jul 08 06:53:15 computer2 kernel: ACPI: Invalid passive threshold
Jul 08 06:53:15 computer2 kernel: thermal LNXTHERM:00: registered as thermal_zone0
Jul 08 06:53:15 computer2 kernel: ACPI: Thermal Zone [TZ10] (17 C)
Jul 08 06:53:15 computer2 kernel: thermal LNXTHERM:01: registered as thermal_zone1
Jul 08 06:53:15 computer2 kernel: ACPI: Thermal Zone [TZ00] (28 C)
Jul 08 06:53:15 computer2 kernel: Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled

```
Here is a section of the /var/log/dmesg file

```
[    1.524706] kernel: input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.525463] kernel: ACPI: Power Button [PWRB]
[    1.525809] kernel: input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.526537] kernel: ACPI: Power Button [PWRF]
[    4.650463] kernel: ACPI: Invalid passive threshold
[    6.698413] kernel: thermal LNXTHERM:00: registered as thermal_zone0
[    6.698925] kernel: ACPI: Thermal Zone [TZ10] (17 C)
[    6.758554] kernel: thermal LNXTHERM:01: registered as thermal_zone1
[    6.759067] kernel: ACPI: Thermal Zone [TZ00] (28 C)
[    6.759630] kernel: Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
```

Note the 5 second delay shown in the dmesg file but not in the journalctl output. Can somebody please explain why these are different. Even better if someone can suggest where to look for the delay!

---

### Post by fragglebliss on 2019-07-07
I think a reasonable response to your query would be to ask you what precisely is your problem and what are you trying to solve?

---

### Post by habana on 2019-07-08
> **fragglebliss said:**
> I think a reasonable response to your query would be to ask you what precisely is your problem and what are you trying to solve?

Sorry if I didn't make myself clear. My problem is I don't understand why the two logs have different timing if they are looking at the same process. What I am trying to solve is what is causing the 5 second delay indicated in dmesg around the 'invalid passive threshold' line.

---

### Post by habana on 2019-07-10
bump

---

### Post by fragglebliss on 2019-07-10
Ok, I understand what you mean. Yes, it is an oddity. But personally, I'd put that one in my 'who cares' basket. If there isn't a specific problem with the system caused by the delay then I see no real reason as to why you'd waste your time trying to figure it out.

Sorry I couldn't be more help.

---

### Post by habana on 2019-07-10
> **fragglebliss said:**
> Ok, I understand what you mean. Yes, it is an oddity. But personally, I'd put that one in my 'who cares' basket. If there isn't a specific problem with the system caused by the delay then I see no real reason as to why you'd waste your time trying to figure it out.

Sorry I couldn't be more help.

I take your point. A 5 second delay isn't too much time out of my day. I'm really more concerned about the discrepancy between the two results. I have been led to believe that the journalctl command is _the_ way to analyse this sort of problem and it seems to give misleading results. It's not a waste of _my_ time because I am interested. I apologize if I am wasting anybody else's time!

---

