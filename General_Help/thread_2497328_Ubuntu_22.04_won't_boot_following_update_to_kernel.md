---
title: "Ubuntu 22.04 won't boot following update to kernel 6.5.0-34-generic"
date: 2024-04-30
forum: General Help
---

### Post by maglin2 on 2024-04-30
As it says in the title a recent update installed a kernel that won't boot.
It stops forever at
    ```
 Loading initial ramdisk...
```
The only way out I can find is long press of the power button.

Any help in finding out what's wrong/fixing appreciated.

The machine will still boot to 6.5.0-27-generic, the only other kernel installed.

Thanks in advance.

(My inclination is to uninstall 6.5.0-34-generic and hope something better comes along - but I'm holding off waiting for advice on the wisdom of that/the existence of better options)

---

### Post by maglin2 on 2024-05-02
Well I followed my inclination and it didn't work (as is often the case).
After some raised blood pressure I spotted that Grub OS prober only operated on the second installed OS on a multiboot disc (which this is). Ran sudo update-grub in the other install and all seems to be working.

---

