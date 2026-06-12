---
title: "two machines: one 5.13.0-41-generic another 5.14.0-1036-oem"
date: 2022-05-20
forum: General Help
---

### Post by centguy2 on 2022-05-20
I believe I installed ubuntu on two machine similarly, but after apt upgrade 
one is 5.13.0-41-generic another 5.14.0-1036-oem.

I do not understand this. I thought both should be the same. I believed I have used the same .iso. (or may be not).

---

### Post by guiverc on 2022-05-20
You haven't provided any OS/release details, but I'll assume your 5.13 *generic* kernel implies it's a 21.10 or 20.04 LTS system using the HWE kernel stack; so I'll assume Ubuntu 20.04 LTS Desktop.

Ubuntu 20.04 LTS Desktop defaults to the HWE kernel, which at 20.04.4 is the 5.13 kernel; which would explain one machine.

If a machine is detected as benefiting from an OEM or *specific* kernel (including the older GA kernel), the `ubiquity` installer can replace the default HWE kernel with that kernel stack; the OEM in the 5.14 kernel detail looks like it detected that machine would benefit from the 5.14 OEM kernel.

This reply *may* have been different if you're provided release details (inc. server/desktop/core etc).  Server ISOs default to the GA kernel stack; Ubuntu Desktop defaults to HWE for all 20.04 media; *flavors* vary on ......

---

