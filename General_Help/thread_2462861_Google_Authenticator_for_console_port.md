---
title: "Google Authenticator for console port"
date: 2021-05-28
forum: General Help
---

### Post by tc2020 on 2021-05-28
I would like to use Google Authenticator as 2FA to help secure login to Ubuntu server 20.04 LTS running on Raspberry Pi 4B via its serial/console port (Google Authenticator for SSH already set up and works on this platform).

Any help would be appreciated. Thank you!.

---

### Post by scorp123 on 2021-05-30
> **tc2020 said:**
>  Google Authenticator for SSH already set up and works on this platform.

Good. 

> **tc2020 said:**
>  I would like to use Google Authenticator as 2FA to help secure login to Ubuntu server 20.04 LTS running on Raspberry Pi 4B via its serial/console port ().

Two things to consider here:
[LIST]
[*]Is there even a login process listening on that serial port? :-k
[*]If someone who is not authorized has physical access to this Raspberry (... or why else are you worried about the serial port? ...) then this won't stop them from getting into the server!!
[/LIST]

2FA will not stop an intruder if that intruder has physical access to the server!! Whatever mechanism you put in place can be circumvented by physical access, e.g. insert USB stick with a Live OS and then boot from that, access the file system and then copy away / steal any valuable data on the server. Or just simply steal the whole Raspberry given how small they are, analyze what to do with it later ...

Or what exactly is the scenario here? Why the serial port?

---

### Post by tc2020 on 2021-06-15
We have decided not to pursue Google Authenticator for serial port but instead have developed our 2FA version. 

RPi device is actually housed in a 19" rack mount enclosure and yes, when someone has physical access to the device that person can do a lot of things to the device. This 2FA comes into play when users want to access this serial port via some external IP-serial device for remote out of band administration. This 2FA provides that extra protection under this scenario.

---

### Post by scorp123 on 2021-06-16
> **tc2020 said:**
> This 2FA comes into play when users want to access this serial port via some external IP-serial device for remote out of band administration. This 2FA provides that extra protection under this scenario.

Makes sense.

---

