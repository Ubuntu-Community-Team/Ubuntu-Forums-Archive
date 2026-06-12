---
title: "Swapped LGA1150 i5-4570S for i7-4790 in 17.10 and now I'm experiencing freezes"
date: 2018-01-08
forum: General Help
---

### Post by portlandbob2 on 2018-01-08
In the last couple of days I replaced my old i5-4570S with an i7-4790. I've noticed two hard freezes in that time. I didn't experience hard freezes with anywhere near this frequency. Is there something that could have triggered the issue or is this just coincidence?
I do see some ACPI complaints on restart, but they are the same ones I saw with the previous CPU. The new CPU temp hasn't gone above 49C since I've been tracking it.

  Thanks for whatever help you can provide,
  -portlandbob

---

### Post by Yellow Pasque on 2018-01-08
What motherboard is it? If you don't know:
```
sudo dmidecode -t 0,1,2
```

---

### Post by portlandbob2 on 2018-01-08
Base Board Information
    Manufacturer: ASUSTeK COMPUTER INC.
    Product Name: H87-PRO
    Version: Rev X.0x

---

### Post by Yellow Pasque on 2018-01-08
Do you have the latest BIOS (2104)? Asus lists the vague "improve system stability" in their changelog. I would prefer to do the update with the old CPU if it was more stable, but that's me.
I guess you should also make sure you have a sufficient PSU, though the 4790 doesn't take a lot more power than the 4570S.

---

