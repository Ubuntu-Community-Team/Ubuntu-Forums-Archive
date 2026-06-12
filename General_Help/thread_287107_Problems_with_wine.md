---
title: "Problems with wine"
date: 2006-10-28
forum: General Help
---

### Post by eantoranz on 2006-10-28
I tried to run wincfg but it feels like it hangs up the computer. I remotely logged in and was able to kill the wine processes and then the computer continued running (music went on, mouse move, keyboard responded, etc).

This is what the console says:
```

$ winecfg
wine: creating configuration directory '/home/antoranz/.wine'...
libGL warning: 3D driver claims to not support visual 0x46

```

After I killed this was left on the console:
```

wine: Unhandled page fault on read access to 0x00000338 at address 0x7e61507d (thread 0009), starting debugger...
Killed
sudwine: wineprefixcreate failed while creating '/home/antoranz/.wine'.

```

This happened on the wine downloaded from the official edgy repositories and with the dapper branch taken from the wan page (no edgy branch yet... according to apt).

Any idea how I can work around this?](*,)

---

