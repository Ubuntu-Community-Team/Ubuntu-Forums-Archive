---
title: "with -EEXIST, don't try to register things with the same name in the same directory."
date: 2013-05-01
forum: General Help
---

### Post by clubbing80s on 2013-05-01
Hi.

I have an Ubuntu workstation that has a tendancy to crash a couple of times a week. In the process of investergating I have found these messages :

root@nzaklwks0081:/var/log# cat dmesg.0 | grep -i fail
[    0.000000] Fast TSC calibration failed
[    1.754913] kobject_add_internal failed for SlotPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.755114] kobject_add_internal failed for FrontUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.755299] kobject_add_internal failed for RearUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.755489] kobject_add_internal failed for InternalUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[   33.318520] init: failsafe main process (945) killed by TERM signal
root@nzaklwks0081:/var/log# cat dmesg.1.gz | grep -i fail
root@nzaklwks0081:/var/log# zcat dmesg.1.gz | grep -i fail
[    1.750800] kobject_add_internal failed for SlotPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.750990] kobject_add_internal failed for FrontUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.751189] kobject_add_internal failed for RearUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.751380] kobject_add_internal failed for InternalUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[   32.394307] init: failsafe main process (951) killed by TERM signal
root@nzaklwks0081:/var/log# zcat dmesg.2.gz | grep -i fail
[    0.000000] Fast TSC calibration failed
[    1.755089] kobject_add_internal failed for SlotPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.755288] kobject_add_internal failed for FrontUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.755479] kobject_add_internal failed for RearUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.755662] kobject_add_internal failed for InternalUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[   42.201540] init: failsafe main process (952) killed by TERM signal
root@nzaklwks0081:/var/log# zcat dmesg.3.gz | grep -i fail
[    1.768128] kobject_add_internal failed for SlotPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.768325] kobject_add_internal failed for FrontUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.768510] kobject_add_internal failed for RearUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.768697] kobject_add_internal failed for InternalUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[   31.679023] init: failsafe main process (956) killed by TERM signal
root@nzaklwks0081:/var/log# cat dmesg | grep -i fail
[    1.759163] kobject_add_internal failed for SlotPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.759350] kobject_add_internal failed for FrontUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.759548] kobject_add_internal failed for RearUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[    1.759734] kobject_add_internal failed for InternalUsbPresent-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9 with -EEXIST, don't try to register things with the same name in the same directory.
[   28.009737] init: failsafe main process (930) killed by TERM signal
root@nzaklwks0081:/var/log# uname -a
Linux nzaklwks0081 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
root@nzaklwks0081:/var/log#

Any ideas as what may cause this ?

Thanks

G

---

