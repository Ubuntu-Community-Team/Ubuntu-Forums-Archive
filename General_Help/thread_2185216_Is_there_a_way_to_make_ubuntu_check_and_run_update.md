---
title: "Is there a way to make ubuntu check and run updates at a set time every day?"
date: 2013-11-01
forum: General Help
---

### Post by enderwalker97 on 2013-11-01
I have a two ubuntu computers one connected to domain at school and one at my desk that I use for whatever, what i'm wanting to do is get ubuntu on our schools old computers and i know how to connect them to the domain and have admins on the domain able to use sudo, the only thing left i want to do is have the ubuntu computers update after hours when the web filter goes down so the computer won't pester them during the day about updates, so is there anyway i can have ubuntu update at set times or am I out of luck?

---

### Post by sandyd on 2013-11-01
> **enderwalker97 said:**
> I have a two ubuntu computers one connected to domain at school and one at my desk that I use for whatever, what i'm wanting to do is get ubuntu on our schools old computers and i know how to connect them to the domain and have admins on the domain able to use sudo, the only thing left i want to do is have the ubuntu computers update after hours when the web filter goes down so the computer won't pester them during the day about updates, so is there anyway i can have ubuntu update at set times or am I out of luck?

You can automate security upgrades with 
```

sudo apt-get install unattended-upgrades
dpkg-reconfigure unattended-upgrades
```
and auto-install upgrades (not reccomended) with apt-cron

Both are cron jobs so you can adjust their run time

---

