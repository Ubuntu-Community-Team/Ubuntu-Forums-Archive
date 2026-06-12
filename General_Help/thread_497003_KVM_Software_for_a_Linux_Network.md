---
title: "KVM Software for a Linux Network"
date: 2007-07-09
forum: General Help
---

### Post by NeghVar on 2007-07-09
Hello,

I am back using Ubuntu again and need a software based KVM for use on my network. The computers involved will both be Ubuntu, however I plan on only using the Server install on my File Server with no GUI since it won't be needed. Any ideas on this, including what programs are around, i can't find any in the repos, would be greatly appreciated.

Thanks,
Len

---

### Post by chalewa on 2007-07-09
synergy works great


im quite sure that there is a tutorial on this site for how to use it.

---

### Post by NeghVar on 2007-07-09
Thank you for your information, Synergy appears to be an interesting solution however doesn't seem to cover video. What I have is a laptop and a headless server, I'll look into the synergy idea further, I have a monitor that I can run the server with however what I would really like is to be able to sit in one room and control the server in another.

Once again thank you for your input.
Len

---

### Post by rhodry on 2007-07-09
> **NeghVar said:**
> Thank you for your information, Synergy appears to be an interesting solution however doesn't seem to cover video. What I have is a laptop and a headless server, I'll look into the synergy idea further, I have a monitor that I can run the server with however what I would really like is to be able to sit in one room and control the server in another.

Once again thank you for your input.
Len

Have a look at vnc4 - server and client.  It is in the repos and is used for virtual network control.

Cheers,
Paul.

---

