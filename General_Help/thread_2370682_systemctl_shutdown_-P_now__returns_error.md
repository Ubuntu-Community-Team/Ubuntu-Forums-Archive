---
title: "systemctl shutdown -P now  returns error"
date: 2017-09-06
forum: General Help
---

### Post by vidtek on 2017-09-06
systemctl shutdown -P now

For some reason it no longer works (it used to before I tried to repair shutdown hang issues, now it just returns an error.

---

### Post by westie457 on 2017-09-06
Hi just tried 'systemctl -P now'  error returned was 'invalid option -P'. Is this the error you got?

Then I tried 'systemctl shutdown' this threw an 'unknown operation shutdown'

According to 'man systemctl' the correct syntax is now 'systemctl poweroff'

Hope this helps.

---

### Post by vidtek on 2017-09-06
Westie-

Just realised-the command is being returned by systemctl, not shutdown as it should be-been working on this too long my old brain can't hack it anymore......

the correct command should be "shutdown -P now"  not "systemctl shutdown -P now"

Doh....

Thanks.

---

