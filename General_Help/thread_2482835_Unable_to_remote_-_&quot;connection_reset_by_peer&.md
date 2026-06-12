---
title: "Unable to remote - &quot;connection reset by peer&quot;."
date: 2023-01-11
forum: General Help
---

### Post by username2758 on 2023-01-11
Hello,

I am trying to remote control a computer on my local network running Ubuntu 22.04.1 LTS (Jammy Jellyfish) but Remmina is giving me the following error message:

**"read (104: Connection reset by peer)"**.

This error message appears only when attempting to connect via VNC protocol when the Ubuntu existing session has been locked. If the Ubuntu session hasn't been locked, I can remote control just fine using the VNC protocol.

What can I do?

---

### Post by HermanAB on 2023-01-12
Don’t use VNC between Linux machines.  Use SSH instead - it is secure and much easier to get to work.

---

### Post by mIk3_08 on 2023-01-12
> **HermanAB said:**
> Don&#8217;t use VNC between Linux machines.  Use SSH instead - it is secure and much easier to get to work. I agree, SSH is the very most secure for remote connections. Linux wont use any GUI remote apps they discourage using it. Regards and cheers.

---

### Post by ActionParsnip on 2023-01-13
What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

