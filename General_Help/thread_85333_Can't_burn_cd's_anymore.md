---
title: "Can't burn cd's anymore"
date: 2005-11-02
forum: General Help
---

### Post by Snakey on 2005-11-02
When I try to open cdr's, I get the following error message:
```
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
~$ dmesg | tail
[4295391.552000] attempt to access beyond end of device
[4295391.552000] hdc: rw=0, want=1028, limit=4
[4295391.552000] UDF-fs: No partition found (1)
[4295391.565000] attempt to access beyond end of device
[4295391.565000] hdc: rw=0, want=68, limit=4
[4295391.565000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[4295435.676000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295435.676000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295436.434000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295436.434000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

---

### Post by SirKillalot on 2005-12-09
lol strange, I get the same errors for a week or so now.. normally my drive worked very well.. but I think it is broken, because I even cannot boot CDs from that drive anymore :(

---

