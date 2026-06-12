---
title: "Modify startup script to run last"
date: 2017-07-12
forum: General Help
---

### Post by blwegrzyn on 2017-07-12
I installed the virtual box scripts via:
update-rc.d virtualbox defaults 99 01
update-rc.d virtualbox-vm1 defaults 99 01

The first scrpt s the original virtualbox script tha comes with virtualbox package.
I just removed it and modified the arguments so it starts late.

Although the script arguments are 99 01, the scripts are setup to run early.
Rc3.d directory shows both as
S01virtualbox
S01virtualbox-vm1

Because of it virtualbox headless start fails.

How can i force those scripts to start at the end of the boot?

---

