---
title: "[SOLVED] Limewire Setup Wizard Always Loads at Startup"
date: 2008-02-09
forum: General Help
---

### Post by alsamman on 2008-02-09
For some reason, every time I open Limewire, the setup wizard keeps coming up asking for what internet connection I have, Enabling Content Filering, etc. How can I have it save my settings and stop the wizard from coming up every single time I start up Limewire?

---

### Post by alsamman on 2008-02-14
bump

---

### Post by Rhubarb on 2008-02-14
Are you using limewire with wine?
If you want access to the same p2p network, consider using **gtk-gnutella** from the ubuntu repositories.
```
sudo aptitude install gtk-gnutella
```

---

### Post by alsamman on 2008-02-14
im not using it with wine i downloaded it from limewire website and it has a .deb version of limewire

---

### Post by Rhubarb on 2008-02-14
Oh, ok then.
I can't help you with limewire, as don't have any experience with it.
If you don't get any help here, try out gtk-gnutella.

---

### Post by hazelnutz18 on 2008-03-20
I just installed Ubuntu on my desktop. I had it installed on my laptop and never got this issue but for some reason on the desktop each time I start LimeWire it goes through the setup. It most likely is a problem with file permissions - limewire doesn't have access to write to the file that tells it that the setup has been completed before. I'm trying to figure it out too so I'll let you know - good luck...

---

### Post by enigmaniac23 on 2008-04-24
Same issue here.  Has anyone figured this out yet?

---

### Post by alsamman on 2008-04-25
> **enigmaniac23 said:**
> Same issue here.  Has anyone figured this out yet?

i installed hardy heron yesterday and hoped that it would fix this issue but it still came back to haunt me. The only time this wasnt an issue for me was when i had feisty

---

### Post by locky28 on 2008-05-10
I was having this problem with limewire as well as an extra java embedded frame opening whenever I opened it so I gae gtk-gnuttela a go and it's very good. Bit daunting at first but you can get more info out of it, I particularly like the way it tells you what country the downloads being sourced from :D .

---

