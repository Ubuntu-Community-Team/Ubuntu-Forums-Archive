---
title: "light-locker-settings didn't start"
date: 2014-05-09
forum: General Help
---

### Post by jensmaucher on 2014-05-09
Starting light-locker-seetings gives following message

[https://bugs.launchpad.net/ubuntu/+source/light-locker-settings/+bug/1313838](https://bugs.launchpad.net/ubuntu/+source/light-locker-settings/+bug/1313838)

```

Traceback (most recent call last):
  File "/usr/share/light-locker-settings/light-locker-settings/light-locker-settings.py", line 552, in <module>
    main = LightLockerSettings()
  File "/usr/share/light-locker-settings/light-locker-settings/light-locker-settings.py", line 97, in __init__
    self.init_settings()
  File "/usr/share/light-locker-settings/light-locker-settings/light-locker-settings.py", line 240, in init_settings
    use_light_locker = settings['light-locker-enabled']
TypeError: 'NoneType' object has no attribute '__getitem__'


```

Has somebody an idea?

Regards
Jens

---

### Post by jensmaucher on 2014-05-11
Ok, if nobody has an idea :D is there a workaround? eg. alternative of a program

---

### Post by Toz on 2014-05-12
Have you tried re-installing light-locker?
```
sudo apt-get install --reinstall light-locker
```

> **jensmaucher said:**
> Ok, if nobody has an idea :D is there a workaround? eg. alternative of a program

You can install and use xscreensaver instead. Xubuntu just replaced xscreensaver with light-locker.

---

### Post by jensmaucher on 2014-05-12
Yes, i did a reinstall but without success

---

### Post by pqwoerituytrueiwoq on 2014-05-12
well this is odd i can't open it eigther, but i am using xscreensaver on this system
i know it worked the other week

maybe it cant be started cause I disabled it for xscreensaver, maybe the guest account can open it (edit: works in guest session)
and why is switch user not working (under action-buttons in the xfce4-panel)?

---

### Post by jensmaucher on 2014-05-14
Deleted ~/.config/autostart/light-locker.desktop and it works now.

---

### Post by harayz on 2014-11-29
thank you - this worked for me

---

### Post by eldudorinio on 2015-08-15
> **jensmaucher said:**
> Deleted ~/.config/autostart/light-locker.desktop and it works now.

Thanks for that jensmaucher! Just what I was looking for.

---

