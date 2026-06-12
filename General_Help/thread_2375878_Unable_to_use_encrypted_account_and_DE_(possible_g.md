---
title: "Unable to use encrypted account and DE (possible graphical issues)"
date: 2017-10-28
forum: General Help
---

### Post by skiphopjump on 2017-10-28
First, I'm not able to load Ubuntu normally. I will get black screen without any action and monitor will turn off.

I have to use recovery mode, then to escape graphical loader (F8), then resume load.

With these steps I'm able to access login screen.

I'm able to enter wrong password and get an error message, but when I enter correct password I get black screen and then I'm presented with login screen again.

I tried recovery option, every kernel version, every DE variant (I have 3 of them) but none of them work (without extra commands).

My network is functional in guest account, but not video card (driver is enabled but doesn't work really)


I want to restore access or all info from my encrypted account.

---

### Post by ulysses77 on 2017-10-28
I'm having a variant of the same issue. 

[COLOR=#000000]rm -rf /home/ulysses/.config/dconf/user[/COLOR]

[COLOR=#000000]This will get you in, this will give you stock every time, but your files will be there. Can somebody submit this issue to the higher ups?[/COLOR]

---

### Post by ulysses77 on 2017-10-28
Now I'm also using an encrypted medium. From everything I've gathered, this is an issue that came from a recent update.

---

### Post by skiphopjump on 2017-10-29
> **ulysses77 said:**
> [COLOR=#000000]rm -rf /home/ulysses/.config/dconf/user[/COLOR]

[COLOR=#000000]This will get you in, this will give you stock every time, but your files will be there[/COLOR]But how can I get access to my old home? It is encrypted and I cannot remove [COLOR=#000000].config from non-guest account.[/COLOR]


Is it possible to login in with command line mode?

---

