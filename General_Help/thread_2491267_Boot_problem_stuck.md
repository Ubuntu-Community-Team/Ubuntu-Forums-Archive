---
title: "Boot problem: stuck"
date: 2023-10-02
forum: General Help
---

### Post by DocHotzenplotz on 2023-10-02
Running ubuntu 20.04 from usb ssd vx500, today morning the Boot process halted with these lines:

ACPI Error Needed type Reference...
ACPI Error AE AML operand type..
ACPI Error Aborting method PR.CPU0 PDC...
Blacklist Problem blacklisting g hash -13
5x
/dev/sda2: clean ...
Bluetooth hci0 unexpected event formopcode 0c0000

What can I do?

---

### Post by #&amp;thj^% on 2023-10-02
Have you tried to boot again, those are just warnings not errors.
But you need to run now:
```
sudo apt update
sudo apt upgrade
```
If you can boot to your desktop.

If any unusual returns from the upgrade command post them back here.

---

### Post by DocHotzenplotz on 2023-10-04
- The boot process is stuck there
- It happens everytime like this when I powercycle
- can't enter anything

---

