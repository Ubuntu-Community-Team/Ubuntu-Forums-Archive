---
title: "Running Xorg-dependant programs on ramote machine"
date: 2006-08-07
forum: General Help
---

### Post by lechium on 2006-08-07
Hi,

I have two machines set up -- a NAT router/filerserver/etc that has no I/O hooked up to it, and my main computer that is connected to the internet though the server box. Both run Ubuntu.

The thing is -- my server box has the DVD writer and I am too lazy to put it onto my main comp. I always have a terminal ssh'ed to my server box, so I can maintain it just fine, however I cannot run X-based program though ssh, because it gets error that display is not found. Hence I cannot run my beloved k3B without hooking up monitor/keyboard/mouse to server box...

...there's gotta be a solution to run X programs from the remote PC, especially since the setup is pretty much identical on both. Any suggestions on how I do so?

wbr,
Victor

---

### Post by professor_chaos on 2006-08-07
either use the tunnel option in ssh...
```
ssh -X hostname
```

or use vnc or xdmcp thru "terminal server client"

---

### Post by cantormath on 2006-08-07
> **lechium said:**
> Hi,

I have two machines set up -- a NAT router/filerserver/etc that has no I/O hooked up to it, and my main computer that is connected to the internet though the server box. Both run Ubuntu.

The thing is -- my server box has the DVD writer and I am too lazy to put it onto my main comp. I always have a terminal ssh'ed to my server box, so I can maintain it just fine, however I cannot run X-based program though ssh, because it gets error that display is not found. Hence I cannot run my beloved k3B without hooking up monitor/keyboard/mouse to server box...

...there's gotta be a solution to run X programs from the remote PC, especially since the setup is pretty much identical on both. Any suggestions on how I do so?

wbr,
Victor

there is VNCserver, terminal server/client, hummingbird, FreeNX on linux....and others.

---

### Post by lechium on 2006-08-07
The tunnel option was exactly what I needed, thanks! (I prefere console based approach as much as possible)

wbr,
Victor

---

