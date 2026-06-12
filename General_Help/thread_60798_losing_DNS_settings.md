---
title: "losing DNS settings"
date: 2005-08-29
forum: General Help
---

### Post by dannemil on 2005-08-29
I am running Ubuntu on my laptop. I use an ethernet connection when I have my laptop at work, and a wireless connection when I use it at home. The wireless connection gets the DNS servers from Roadrunner, but at work I have a static IP. Every time I switch to the static IP at work, it loses the DNS server settings that I typed in the day before. Instead it seems to just inherit the DNS servers that the wireless connection used the night before. Any way to get it to save the DNS servers for the ethernet connection instead of having to type them in each time I switch connections?

---

### Post by arnieboy on 2005-08-29
[QUOTE=dannemil]I am running Ubuntu on my laptop. I use an ethernet connection when I have my laptop at work, and a wireless connection when I use it at home. The wireless connection gets the DNS servers from Roadrunner, but at work I have a static IP. Every time I switch to the static IP at work, it loses the DNS server settings that I typed in the day before. Instead it seems to just inherit the DNS servers that the wireless connection used the night before. Any way to get it to save the DNS servers for the ethernet connection instead of having to type them in each time I switch connections?[/QUOTE]
did u try saving you home config as eth1 and your office conn as eth2 or something. u can try this stuff in system-->administration--> network

---

### Post by dannemil on 2005-08-30
[QUOTE=arnieboy]did u try saving you home config as eth1 and your office conn as eth2 or something. u can try this stuff in system-->administration--> network[/QUOTE]

Thanks. That worked. I just didn't see that location option as a way of saving different connection configurations.

---

### Post by arnieboy on 2005-08-31
[QUOTE=dannemil]Thanks. That worked. I just didn't see that location option as a way of saving different connection configurations.[/QUOTE]
glad to know u are all set :)

---

