---
title: "Xkb Panel Keyboard Layouts Plugin - bug workaround"
date: 2013-03-16
forum: General Help
---

### Post by komarx6 on 2013-03-16
As you all probably know, keyboard layouts plugin has bug. It does not remember some settings after logout/reboot.  
 I alreadly searched for solution in many places and found that I could save file "/home/user/.config/xfce4/panel/xkb-plugin-##.rc" that contains settings. And I could replace that file every time I log in with this command:
```

sh -c "cp /home/user/.config/xfce4/panel/xkb-plugin-19.rc.copy /home/user/.config/xfce4/panel/xkb-plugin-19.rc && pkill xkb"

```
That way I can restore settings, but problem is that this command does not work if I add it to startup applications. I suppose that it is executed before xkb starts so it does not have any effect.
Does someone have any idea how to solve that problem?

This bug is well known (just type "xkb forgets settings" in google and you'll see), it should be fixed already.

Sorry for my bad english. Thanks.

---

