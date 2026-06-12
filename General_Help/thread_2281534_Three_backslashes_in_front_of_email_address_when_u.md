---
title: "Three backslashes in front of email address when using mailto."
date: 2015-06-07
forum: General Help
---

### Post by Garchomps on 2015-06-07
[COLOR=#111111][FONT=Ubuntu]In opening an email address with mailto in Chromium three backslashes appear in front of it in the recipient field that I have to manually remove before sending. I use Xubuntu 15.04, and Chromium opens Thunderbird with the mailto address using xdg-open, which I set to detect the default desktop as Gnome for compatibility reasons. How would I fix it so these back slashes don't appear in the first place? Attached is a screenshot. Thanks! :D
[/FONT][/COLOR][ATTACH=CONFIG]262478[/ATTACH]

---

### Post by timgood on 2015-06-08
I have this problem as well. Any ideas?

---

### Post by Traumflug on 2015-06-08
Looks like this is a pretty old bug: [https://bugs.launchpad.net/do-plugins/+bug/304533](https://bugs.launchpad.net/do-plugins/+bug/304533)

---

### Post by Traumflug on 2015-06-08
In case you guys use Python, here's a reasonable workaround: [https://github.com/Traumflug/Teacup_Firmware/commit/7095c63af01a23ee67f2015418585998c1d047df](https://github.com/Traumflug/Teacup_Firmware/commit/7095c63af01a23ee67f2015418585998c1d047df) Might help with other languages, too, it's not too difficult to read.

---

### Post by Garchomps on 2015-06-10
Seem like a good fix, how to apply it is the only question I have about it.

---

### Post by Garchomps on 2015-06-10
> **Traumflug said:**
> In case you guys use Python, here's a reasonable workaround: [https://github.com/Traumflug/Teacup_Firmware/commit/7095c63af01a23ee67f2015418585998c1d047df](https://github.com/Traumflug/Teacup_Firmware/commit/7095c63af01a23ee67f2015418585998c1d047df) Might help with other languages, too, it's not too difficult to read.
Looks like a good fix, how to go about applying it is my question.

---

### Post by Garchomps on 2015-06-10
Can anyone here with python experience make sense of this?

---

