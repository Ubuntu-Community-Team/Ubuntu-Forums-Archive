---
title: "Looong boot time"
date: 2021-01-05
forum: General Help
---

### Post by created-person on 2021-01-05
I am wondering why the laptop I use is so slow to boot with the Ubuntu 20.04.1 LTS installed on my Multicom U731-V2 laptop with Samsung SSD 256 GB.
The windows I replaced was fast....
It is ok to have it like that, but I wonder why.....
48+seconds from pushing the powerbutton to being able to manipulate the software inside.

I wish you all the very best.

---

### Post by ActionParsnip on 2021-01-05
If you reboot, login then run:
```

dmesg -T > /tmp/details.txt && gedit /tmp/details.txt

```
Look for large gaps in time on the left and this will give clues.

---

