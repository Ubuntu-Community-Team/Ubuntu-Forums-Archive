---
title: "12s till login, after login 45/60s to get environment ready to use"
date: 2021-01-28
forum: General Help
---

### Post by alain.roger on 2021-01-28
Hi,

i'm trying to improve the time computer needs to be ready to work. For some people it can funny, but when you start/shutdown computer several times a day, you can appreciate when it's fast.

I have 1 laptop and 1 desktop computer. Both use Ubuntu 20.10 with KDE 5.20 as DE.
To improve boot time i replace HDD booting disk by SSD. This reduce by 4 my booting time.

Next step i checked with systemd-analyze how it is:

```
[FONT=monospace][COLOR=#000000]Startup finished in 2.528s (kernel) + 10.352s (userspace) = 12.881s  [/COLOR]
graphical.target reached after 7.785s in userspace[/FONT]
```

However, once i log in i need to wait 45/60s to have my desktop ready to use (so to appear and be usable).
What can i do to check the bottleneck place ?

The systemd-analyze blame does not show a particular long process, how can i find what's going on ?
thx

---

### Post by Autodave on 2021-01-28
Can you give us some specs on your equipmentr or at least a model?

---

### Post by alain.roger on 2021-02-08
I reinstalll Ubuntu 20.10 with KDE and not it seems fast.

To answer to your question, i understood you want to know graphic card: RTX 2060

---

### Post by CelticWarrior on 2021-02-08
> [COLOR=#000000]graphic card: RTX 2060[/COLOR]

Make sure the Nvidia drivers are installed and running -> disable Secure Boot in UEFI.

---

