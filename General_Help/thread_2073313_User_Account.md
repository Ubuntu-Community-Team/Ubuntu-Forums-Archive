---
title: "User Account"
date: 2012-10-19
forum: General Help
---

### Post by Gotlieb on 2012-10-19
Hello Everyone,

Been a user of Linux for a while but for some strange reason I upgraded to 12.04 - How can I remove the Guest account?

Please help,

Thanks!

---

### Post by zombifier25 on 2012-10-19
Open /etc/lightdm/lightdm.conf as root and add this line to the end of the file, in the SeatDefaults section:
```
allow-guest=false
```

---

### Post by Gotlieb on 2012-10-19
> **zombifier25 said:**
> Open /etc/lightdm/lightdm.conf as root and add this line to the end of the file, in the SeatDefaults section:
```
allow-guest=false
```

Can you do it step by step? Completely confused.

---

### Post by kc1di on 2012-10-19
> **Gotlieb said:**
> Hello Everyone,

Been a user of Linux for a while but for some strange reason I upgraded to 12.04 - How can I remove the Guest account?

Please help,

Thanks!

Hi,
This [link]("http://www.ubuntugeek.com/ubuntu-tiphow-to-disable-guest-account-in-ubuntu-12-04precise.html") should help it's written for 12.04 but should work in 12.10 also.

---

### Post by Wim Sturkenboom on 2012-10-19
> **Gotlieb said:**
> Can you do it step by step? Completely confused.Do you know what an editor is ;) And how to use it :D

In a terminal youc an edit the file using the following command
```

gksudo gedit /etc/lightdm/lightdm.conf

```
The content looks like this
```

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
[COLOR="Red"]allow-guest=false[/COLOR]

```
Find the line that looks like the one marked in red. It is either non-existing (in which case you add it) or it ends with true (in which case you modify it).

---

