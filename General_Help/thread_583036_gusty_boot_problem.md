---
title: "gusty boot problem"
date: 2007-10-20
forum: General Help
---

### Post by hessiess on 2007-10-20
the live cd runs flawlessly, installed and now get this output

```

starting up....
[19.147328] ..mp-bios bug:8254 timer not connected to io-apic
[19.326114] kernal panic - not syncing : io-acic + timer dusen't work!
```

Compaq presario RF786AA

i installed it in the usaral way to create a dual boot with xp, xp still works normaly

---

### Post by Sef on 2007-10-20
Go into your BIOS and disable apic.  (If it is disabled, then enable it.)  See if that will work for you.

---

### Post by hessiess on 2007-10-20
i cannot see a option for apic in the bios, is it sometimes called somthing else?

---

### Post by sayuki288 on 2007-10-20
set your BIOS to default settings :lolflag:

---

### Post by dabl on 2007-10-20
You probably need to put a "noapic" option in the boot kernel line in /boot/grub/menu.lst.

:)

---

### Post by hessiess on 2007-10-20
> **dabl said:**
> You probably need to put a "noapic" option in the boot kernel line in /boot/grub/menu.lst.

:)

thank you it worked :)

out of curiosaty, what dus apic do? will it affect anything?

and why dusent the wireless adapter witch works perfectly on the live cd, now not work?

---

