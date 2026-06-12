---
title: "[x64] FGLRX in Raring causes crashing X-server"
date: 2013-04-26
forum: General Help
---

### Post by jadus on 2013-04-26
hi guys, i installed Raring yesterday and tried to use fglrx from repos...
but unfortunately I expected troubles

Firstly, fglrx-updates from repo fails on: 
"X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12"

Just FGLRX from repo fails on: "No supported device found"
And FGLRX 13.4 from AMD sites looks good during installation, but after restart, it fails on "Failed to create display resources".


The other problem is overheating with opensource drivers, 'cause i have that crapy hybrid graphics and my vgaswitcheroo isn's work properly.

Has anyone solved this problem?

EDIT: Oh, it's AMD Radeon HD 6650M, Hybrid card ( i really hate hybrids!)

---

### Post by rechter77 on 2013-04-26
I had the same issue ....

---

### Post by ubik89 on 2013-07-11
Same problem here.

But you can switch off the radeon card with

```
sudo su
echo "OFF" > /sys/kernel/debug/vgaswitcheroo/switch
```

Then it won't overheat.

But fglrx doesn't work for me with Radeon HD 6650M.

---

