---
title: "Timedatectl Error"
date: 2017-06-07
forum: General Help
---

### Post by eastofsorrow on 2017-06-07
Hi
I am running ubuntu 17.04. When I enter the timdedatectl in terminal I get the following error:

[B]Assertion 'xstrftime: a[] must be big enough' failed at ../src/timedate/timedatectl.c:105, function print_status_info(). Aborting.

[/B]What should I do?

---

### Post by again? on 2017-06-08
> **eastofsorrow said:**
> Hi
I am running ubuntu 17.04. When I enter the timdedatectl in terminal I get the following error:

[B]Assertion 'xstrftime: a[] must be big enough' failed at ../src/timedate/timedatectl.c:105, function print_status_info(). Aborting.

[/B]What should I do?
Tell us more about your specific environment that may be relevant.
Works fine here on my Ubuntu-gnome Desktop install.
```
glen@GU17:~$ **lsb_release -a**
Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

glen@GU17:~$ **timedatectl**
      Local time: Thu 2017-06-08 12:25:35 AWST
  Universal time: Thu 2017-06-08 04:25:35 UTC
        RTC time: Thu 2017-06-08 04:25:35
       Time zone: Australia/Perth (AWST, +0800)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no

```

---

### Post by ssmns on 2017-10-26
for my sysytem :

```

ssmns@baran:~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu5-amd64:core-9.20160110ubuntu5-noarch:printing-9.20160110ubuntu5-amd64:printing-9.20160110ubuntu5-noarch:security-9.20160110ubuntu5-amd64:security-9.20160110ubuntu5-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty
ssmns@baran:~$ timedatectl
Assertion 'xstrftime: a[] must be big enough' failed at ../src/timedate/timedatectl.c:105, function print_status_info(). Aborting.
Aborted (core dumped)



```

---

