---
title: "How does logind.conf work?"
date: 2018-05-25
forum: General Help
---

### Post by ericsoderstrom on 2018-05-25
I modified ```
/etc/systemd/logind.conf 
```to include the line

```
HandleLidSwitch=suspend
```



And then restarted logind with ```
systemctl restart systemd-logind.service
```.

And... it works! The laptop suspends on lid close. However, once I restart the laptop, it no longer suspends on lid close. I have to manually restart logind.conf each time after I restart if I want that behavior. Why?

```
systemctl show systemd-logind.service
``` doesn't show anything about HandleLidSwitch, either before or after restarting logind. How can I figure out what's wrong?

---

### Post by kerry_s on 2018-05-26
[ATTACH=CONFIG]279856[/ATTACH]

does the normal way not work?

---

### Post by kazakore on 2018-05-26
```
systemctl enable systemd-logind.service
```

Should tell it to start the service at boot. Maybe it wasn't enabled before....

---

### Post by ericsoderstrom on 2018-05-27
No, it doesn't work using the power management GUI

---

### Post by ericsoderstrom on 2018-05-27
> **kazakore said:**
> ```
systemctl enable systemd-logind.service
```

Should tell it to start the service at boot. Maybe it wasn't enabled before....


It seems systemd-logind.service cannot by enabled this way. `systemctl status systemd-logind.service` shows that the service is running, and logging 'Lid closed' and 'Lid opened' events. Just not suspending (until after `systemctl restart systemd-logind.service`

---

### Post by kerry_s on 2018-05-27
you should post your specs, make, model, etc....

i'm thinking it's hardware related & you need to add a boot switch. but see if anyone else has the same system & knows what to do.

---

