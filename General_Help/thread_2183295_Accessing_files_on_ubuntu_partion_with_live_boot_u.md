---
title: "Accessing files on ubuntu partion with live boot usb"
date: 2013-10-24
forum: General Help
---

### Post by elendur45 on 2013-10-24
I had to run windows recovery to boot into windows. Now I can't boot into ubuntu. I need to recover some files from the Ubuntu partition and it says I don't have permission to copy them when using live boot disc. Is there a work around for this.

---

### Post by Bashing-om on 2013-10-24
elendur45; Hi !

try: from the liveDVD terminal code:
```

sudo cp -p <the_source_path>/file_name <the_destination_path>/file_name

```
"sudo" - To gain that elevated privilege.

Is there a reason you do not desire to resurrect the ubuntu install ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Samuel_Peters on 2013-10-24
backup your files on a cd-rom, wipe linux with all its partitions and reinstall it. That the only way I can help you.

---

### Post by elendur45 on 2013-10-24
Can I resurrect the ubuntu install with reformatting?

---

### Post by AlexDudko on 2013-10-24
> **elendur45 said:**
> Can I resurrect the ubuntu install with reformatting?

No, all your ubuntu files and directories will be gone, but you can try to recover a bootloader.

---

### Post by Bashing-om on 2013-10-24
elendur45; Hey,

One may (re-)install ubuntu's bootloader (grub) from the liveDVD. If you desire to try this show us what there is to work with,
from the liveDVD; terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
And only if you have GPT as the partitioning scheme show (fdisk returns the advisory):
```

sudo gdisk -l /dev/sda

```

This is a good place to start and better than most.
[INDENT][INDENT]ubuntu:
[INDENT][INDENT][INDENT]all things are possible[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

