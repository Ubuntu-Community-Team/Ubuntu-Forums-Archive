---
title: "VNC viewer suggestions please"
date: 2007-06-04
forum: General Help
---

### Post by UncleB on 2007-06-04
Hello all,

I used to use UltraVNC on Windows mainly because it could auto-scale the target screen. If I'm not explaining that well I mean that on my small laptop screen I could VNC to computers with a larger desktop resolution and it would be scaled down so that the whole target desktop would fit into the VNC window without any scrolling around.

Is there a similar VNC client for Ubuntu?

---

### Post by mifi on 2007-06-04
> **UncleB said:**
> Hello all,

I used to use UltraVNC on Windows mainly because it could auto-scale the target screen. If I'm not explaining that well I mean that on my small laptop screen I could VNC to computers with a larger desktop resolution and it would be scaled down so that the whole target desktop would fit into the VNC window without any scrolling around.

Is there a similar VNC client for Ubuntu?
Have you tried "Applications/Internet/Terminal Server client" ?
Set the protocol to VNC and connect. Must admit I do not know if it scales...

ciao
mifi

---

### Post by pak33m on 2007-06-04
I have to connect to my Windows PC at work quite a bit and I use rdesktop.  If you are wanting to connect in the same install rdesktop and type the following (in the CLI):

rdesktop -u -p -xm -f 172.x.x.x

I use this command in a script to connect to my Windows PC at work in full screen.  I simply press Ctrl+Alt+Enter to exit full screen.

or you could use Terminal Server Clinet as suggested earlier.

---

### Post by UncleB on 2007-06-04
Ok, that's almost there.

The full screen mode fits the target desktop into the available screen. But I'd ideally like one that could automatically shrink a full screen version into the available VNC window.

---

### Post by ecoxmit on 2007-10-22
krdc from kde will do it.

---

