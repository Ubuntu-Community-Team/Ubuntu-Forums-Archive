---
title: "Auto start Boinc in 7.04?"
date: 2007-07-16
forum: General Help
---

### Post by jonant on 2007-07-16
How do I go about getting BOINC (5.8.16) to auto start at bootup?
Thanks!

---

### Post by dreadlord_chris on 2007-07-16
are you talking about the BOINC client or the BOINC manager? Because the client should be set to start at boot when you install it. BOINC manager you don't want starting at boot.

---

### Post by jonant on 2007-07-16
This pc is in another location subject to power interruptions and while it is on a UPS I would like BOINC to start if the pc reboots... it is a dedicated BOINC machine on 24/7...

---

### Post by dreadlord_chris on 2007-07-17
> **jonant said:**
> This pc is in another location subject to power interruptions and while it is on a UPS I would like BOINC to start if the pc reboots... it is a dedicated BOINC machine on 24/7...

That didn't answer the question I asked....
I'm gonna assume you are talking about the BOINC client - since it's the one that is supposed to start at boot.
So, now, are you certain it's not starting at boot?

---

### Post by Indefual on 2007-07-18
I think I might be having the same problem for the last couple days, and I think I've figured out what the problem is.  I think the original poster and my self assumed we installed BOINC but DIDN'T.

I typed in BOINC in the Add/Remove program and installed BOINC Manager and the K Spy application.  I assumed with the BOINC Manager would include the install of BOINC, but that may not have been the case.  But I can't find the BOINC core client.

So, is the BOINC core client seperate from those two packages I installed?  How do I find it? Is it in the Add/Remove program at all, because I can't find it!

In System Monitor I find nothing called "boinc" running.  So it's not running and probably not installed.  Should I download it from the BOINC website and install it from the script?

---

### Post by dreadlord_chris on 2007-07-19
> **Indefual said:**
> I think I might be having the same problem for the last couple days, and I think I've figured out what the problem is.  I think the original poster and my self assumed we installed BOINC but DIDN'T.

I typed in BOINC in the Add/Remove program and installed BOINC Manager and the K Spy application.  I assumed with the BOINC Manager would include the install of BOINC, but that may not have been the case.  But I can't find the BOINC core client.

So, is the BOINC core client seperate from those two packages I installed?  How do I find it? Is it in the Add/Remove program at all, because I can't find it!

In System Monitor I find nothing called "boinc" running.  So it's not running and probably not installed.  Should I download it from the BOINC website and install it from the script?

Huh.... it's not in Add/Remove Programs.....
It is available in the repositories though. Either open Synaptic and search for boinc - you'll see the boinc-client listed - or from the command line:
```

sudo apt-get install boinc-client

```

---

### Post by Indefual on 2007-07-19
Synaptic worked perfectly.  Thanks.

---

