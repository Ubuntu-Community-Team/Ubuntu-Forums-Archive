---
title: "Chromium doesn't start if Apparmor is enforced"
date: 2015-12-17
forum: General Help
---

### Post by Flacon on 2015-12-17
If I do:
```
[COLOR=#000000]aa-enforce /etc/apparmor.d/usr.bin.chromium-browser[/COLOR]
```
Chromium launcher icon goes bright & fade for sometime and Chromium doesn't start.

However, if I do this:
```
[COLOR=#000000]aa-complain /etc/apparmor.d/usr.bin.chromium-browser[/COLOR]
```
Its starts just fine.

Firefox is starting fine even when I have enforced apparmor on it.

---

