---
title: "Unmount order"
date: 2013-03-03
forum: General Help
---

### Post by Vitsliputsli on 2013-03-03
Hello,

can I change unmount order when system is shutting down?

In fstab I have these strings:
```

[COLOR=#000000][FONT=dejavu sans mono]none    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]/root/user_rw  [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]tmpfs    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]rw,size=128M,uid=1001,gid=1001           [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]0 [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]none    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]/home/user     [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]aufs     [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]rw,dirs=/root/user_rw:/root/user_ro=ro   [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]0 [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]0
[/FONT][/COLOR]
```
It unmount /root/user_rw first, but this directory used by aufs in /home/user. So /root/user_rw can be unmount only after /home/user.

I have error when shut down system: /root/user_rw is busy. How can I solve this problem?

---

