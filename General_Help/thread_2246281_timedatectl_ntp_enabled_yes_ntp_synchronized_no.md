---
title: "timedatectl ntp enabled yes ntp synchronized no"
date: 2014-09-29
forum: General Help
---

### Post by Dana_Carter on 2014-09-29
Hello All,
On Ubuntu Server 14.04 when I run
```
$ timedatectl
      Local time: Mon 2014-09-29 12:24:17 MST
  Universal time: Mon 2014-09-29 19:24:17 UTC
        Timezone: America/Phoenix (MST, -0700)
     NTP enabled: yes
NTP synchronized: no
 RTC in local TZ: no
      DST active: n/a
```

Why does it say NTP synchronized no and not yes?
Is this a problem I need to concern myself about?

Thank you all for your time.

---

### Post by nerdtron on 2014-09-29
Have you setup NTP for syncing time? The correct way to check is:
```
ntpq -c lpeer
```

An * on the beginning of an entry means the machine is currently syncing time to this NTP server. Delay, offset and jitter columns should also not be zero.

---

### Post by Dana_Carter on 2014-09-29
Thank you... I feel stupid
I thought ntp was installed because when I ran ntpd it worked.
i ran sudo apt-get install ntp
and now I am synching


thanks again.

---

