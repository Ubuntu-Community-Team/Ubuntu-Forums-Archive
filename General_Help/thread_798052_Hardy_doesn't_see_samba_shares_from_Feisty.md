---
title: "Hardy doesn't see samba shares from Feisty"
date: 2008-05-17
forum: General Help
---

### Post by arbulus on 2008-05-17
I have a file server that I recently had to downgrade back to Feisty because of printing issues.  This server serves up two samba shares.  Well, once I got my printers all set up and working well, I set up the samba shares.  My wife's Mac sees them just fine and dandy.  But my Hardy lappy can't see them.  I go to Places>Network>Windows Network>My Workgroup Name but then it doesn't show me the file server so that I can mount the shares. It doesn't see anything at all.  I previously had Hardy on the fileserver and everything worked just fine. I would go to Places>Network>Windows Network>My Workgroup Name>fileserver>Share and there it was.  But it's not showing the machine now.  

Is anyone else experiencing this or know how to fix it?  Why is it that my wife's Mac can browse the shares just fine but my Hardy lappy can't?

---

### Post by arbulus on 2008-05-21
Bump

---

### Post by arbulus on 2008-05-23
bump

---

### Post by arbulus on 2008-05-24
Ok, so i just installed openSUSE on my server, and Hardy STILL cannot browse the shares.  It's still doing the exact same thing that it was when the server was running Feisty.

So something is seriously wrong with Hardy's samba service, obviously.

---

### Post by Iowan on 2008-05-24
Just so you're not talking to the wall...
can you connect to the server via IP address?

---

### Post by arbulus on 2008-05-25
> **Iowan said:**
> Just so you're not talking to the wall...
can you connect to the server via IP address?

Yeah, I have connectivity to the server in other ways: I have a jabber server running, which I can use just fine, I can print to the shared printers that the server hosts and I can ping it. The only thing that doesn't work is browsing the samba shares.

---

