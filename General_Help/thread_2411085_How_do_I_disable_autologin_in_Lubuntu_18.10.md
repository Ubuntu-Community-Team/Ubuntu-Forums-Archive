---
title: "How do I disable autologin in Lubuntu 18.10?"
date: 2019-01-24
forum: General Help
---

### Post by soldiercore on 2019-01-24
There was a setting I unchecked some time ago where I removed the need to enter my password on every login; but I want it back now and I can't find it anywhere. Where it is?

Also, since I'm here, why is the lockscreen (Xscreensaver) so outdated? Can I change it?

---

### Post by Frogs Hair on 2019-01-24
The option for auto login should be the user settings.

[https://manual.lubuntu.me/](https://manual.lubuntu.me/)

---

### Post by soldiercore on 2019-01-24
Can you be more specific? I have looked all over the LXQt Configuration Center and did not find it. I wouldn't be here otherwise.

EDIT: I just remembered. It was an option from the Lubuntu installer! Right after setting up your user account there was a checkbox with "Log in automatically". Found this with a quick search: [http://i55.tinypic.com/2dlpv10.jpg](http://i55.tinypic.com/2dlpv10.jpg) . Why it isn't in the settings is beyond me.

---

### Post by Dennis N on 2019-01-24
Edit the file **/etc/sddm.conf**
Remove your user name from Autologin section.

---

### Post by Frogs Hair on 2019-01-24
The option may not appear in users and groups unless change password is selected.

---

### Post by soldiercore on 2019-01-25
> **Dennis N said:**
> Edit the file **/etc/sddm.conf**
Remove your user name from Autologin section.

Thank you!

---

