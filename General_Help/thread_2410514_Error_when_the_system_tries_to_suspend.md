---
title: "Error when the system tries to suspend"
date: 2019-01-16
forum: General Help
---

### Post by Paddy Landau on 2019-01-16
Lubuntu 16.04 64-bit

When the system tries to suspend after I've been away from the computer, I've recently started to get this error from Power Manager.
[ATTACH=CONFIG]282216[/ATTACH]
```
GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed Action org.freedesktop.login1.suspend is not registered
```

When I go into the XFCE Power Manager, the options for System sleep more have been greyed out.
[ATTACH=CONFIG]282214[/ATTACH]

I have no idea how to fix this problem. Can you help, please?

EDIT: I see that I also no longer have the option to manually sleep.

---

### Post by TheFu on 2019-01-16
Does **sudo pm-suspend** work?

---

### Post by Paddy Landau on 2019-01-17
> **TheFu said:**
> Does **sudo pm-suspend** work?
Yes, it does, perfectly.

---

### Post by Paddy Landau on 2019-01-20
I figured out the problem.

Lubuntu has a recurring error where suspend does not work. Usually the fix is to make a small edit to the file [FONT=lucida console]/usr/share/polkit-1/actions/org.freedesktop.login1.policy[/FONT]. I had mis-edited it, and the error was so small that I missed it.

---

