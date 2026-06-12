---
title: "No such device and disk hd0 not found"
date: 2019-02-09
forum: General Help
---

### Post by idogrusoz on 2019-02-09
I have been having problems with booting my pc. I don’t have windows on it only Ubuntu 18.04. Before I have updated the grub and everything. Lastly booted through usb stick and ran boot-repair. It came up with the report that boot files are to far away. Thinking that it anyway would work boites the computer and came across with grub rescue screen where ‘ls’ command returns nothing.

---

### Post by oldfred on 2019-02-09
If newer system the far from start of disk is not an issue.
It only was an issue with old IDE drives. Your drive is set for AHCI?
And it has been an issue on some USB full drive installs.

But we normally suggest you have a smaller / (root) of 25 or 30 GB and rest of drive as /home or other data partitions.

UEFI or BIOS install?
What brand/model system?
Post link to the summary report from Boot-Repair.

---

