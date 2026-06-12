---
title: "suspend / hibernate works once then fails"
date: 2007-12-20
forum: General Help
---

### Post by beczka2005 on 2007-12-20
Hi,

I'm joining the Ubuntu ranks migrating from Gentoo (4 years). 

Most of ubuntu works out of the box for me except for suspend. Suspend and hibernate work *ONCE* per boot for me. So I can suspend to ram (or hibernate), and wake up just fine. But if I try and do it again it just hangs on suspend. 

Where do I start debugging this?!

---

### Post by beczka2005 on 2007-12-20
Spent half a day on this and still can't figure it out. I can suspend and resume once after a fresh boot, second suspend hangs. If it helps here is my  /var/log/messages for the working (first) and not working (second) suspend. But they seem pretty useless to me!

In the second case I don't get the "Stopping tasks ... done" and I have to reboot.


**First suspend**
```

  22286 Dec 20 17:45:28 kronos gnome-power-manager: (raf) Suspending computer because the suspend button has been pressed
  22287 Dec 20 17:45:29 kronos kernel: [  801.088000] pccard: card ejected from slot 0
  22288 Dec 20 17:45:30 kronos kernel: [  801.472000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
  22289 Dec 20 17:45:50 kronos kernel: [  804.644000] Stopping tasks ... done.
...

```

**Second suspend**
```

  22359 Dec 20 17:46:55 kronos gnome-power-manager: (raf) Suspending computer because the suspend button has been pressed
  22360 Dec 20 17:46:56 kronos kernel: [  876.856000] pccard: card ejected from slot 0
  22361 Dec 20 17:46:57 kronos kernel: [  877.176000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
  22362 Dec 20 17:48:13 kronos syslogd 1.4.1#21ubuntu3: restart.

```

---

### Post by beczka2005 on 2007-12-21
If I change to the nv driver then I can suspend and resume multiple times without issues. So this must be related to nvidia binary somehow! Anyone know of anything else I can try?

---

