---
title: "syncronizing time"
date: 2008-02-01
forum: General Help
---

### Post by jarthel on 2008-02-01
In changing the current time, it is currently configured as manual. If I select ¨Keep sychronize with internet servers¨, it would prompt me if I want to install NTP. I click ok then.

BUT nothing is happening. 

In this site: [http://www.watchingthenet.com/enable-auto-time-synchronization-in-ubuntu-and-kubuntu.html](http://www.watchingthenet.com/enable-auto-time-synchronization-in-ubuntu-and-kubuntu.html),

the screenshot after 4 shows a new selection after ¨configuration¨. I never get this option.

I have rebooted my PC. I checked synaptic and it seems ntpdate is installed though I´m not sure if this is the one required by the adjusting the time.

any ideas?

thank you very much.

PS. I´m using ubuntu 7.10 (newly installed)

---

### Post by nick_h on 2008-02-01
> ntpdate is installed though I´m not sure if this is the one required
You also need the package *ntp*.

---

### Post by jarthel on 2008-02-01
> **nick_h said:**
> You also need the package *ntp*.

thanks. When I searched for the package ¨ntp¨ first, only ntpdate came up. I reload the packages and ¨ntp¨ came up this time.

---

### Post by PinkFloyd102489 on 2008-02-01
ntpd is the package.

---

### Post by nick_h on 2008-02-02
> ntpd is the package.
*ntpd* is the NTP daemon which can be found in the *ntp* package.

---

