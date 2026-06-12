---
title: "Changing services boot order."
date: 2013-06-13
forum: General Help
---

### Post by kleenex on 2013-06-13
Hi. Is there some way to change services boot order? For now it looks something like;

```
* Starting ACPI daemon [ OK ]
* Starting anac(h)ronistic cron [ OK ]
* Starting save kernel messages[ OK ]
* Stopping restore sound card(s') mixer state(s)[ OK ]
* Starting LightDM Display Manager
* Starting kleenex_service
(...)
```

I would like to achieve situation when **kleenex_service** is started at the beginning. As you can see this service is almost at the end. So is there any method to change this?

---

### Post by Toz on 2013-06-13
What is "kleenix_service"? What does its startup file look like? (should be in either /etc/init.d or /etc/init).

[This]("https://help.ubuntu.com/community/UbuntuBootupHowto") might be helpful.

---

### Post by kleenex on 2013-06-13
Hi Toz. **kleenex_service** is a simple script placed in **/etc/init.d/** directory. Thank you for the link, but it seems, that I've tried almost everything from that HowTo. However, I look one more time at this HowTo and try to solve my question. If I did not achieve a solution, I will writing here.

---

### Post by Toz on 2013-06-13
If you look at /etc/rc2.d (runlevel 2 is the default runlevel for ubuntu), you will see a number of files linked back to files in /etc/init.d. Hopefully there is one there for kleenix_script. Scripts that start with S are startup scripts. The next 2 digits indicate the order that the script is executed in that directory (the lower the number, the earlier the execution). Does the kleenix_script link exist there and what is its name?

---

