---
title: "Ubuntu and Kubuntu won't boot after an update"
date: 2020-03-12
forum: General Help
---

### Post by matovina-mario on 2020-03-12
Hi
I bought a new laptop yesterday, Lenovo IdeaPad L340. I can install ubuntu and kubuntu and everything works fine until it does a first update. Then I get error at boot, it says something like -  problem loading x.509 certificate, and later it says - soft lockup: CPU stuck for 23s.
But the weird part is that I can boot it in recovery mode, and then when I choose -resume normal boot, it starts fine. But I don't want to do that every time I turn on my laptop.

I'm not an expert on linux and I don't have an idea what this is. But I have two computers running kubuntu, both much older, but none of them have problems with it.

And now another problem. I tried to shut it down, but it says - A stop job is running for Make remote CUPS printers available locally (counts seconds)

Ah, yes, this problem occurs with Kubuntu 19, Kubuntu 18LTS and Ubuntu 18LTS

---

### Post by &amp;KyT$0P# on 2020-03-13
> **matovina-mario said:**
> And now another problem. I tried to shut it down, but it says - A stop job is running for Make remote CUPS printers available locally (counts seconds)


I also had this problem recently.  I solved it by running these commands in Terminal -
```
sudo systemctl stop cups-browsed
sudo systemctl disable cups-browsed
```

---

