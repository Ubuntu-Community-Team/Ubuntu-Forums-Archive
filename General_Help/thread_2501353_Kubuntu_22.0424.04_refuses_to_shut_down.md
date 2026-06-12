---
title: "Kubuntu 22.04/24.04 refuses to shut down"
date: 2024-10-03
forum: General Help
---

### Post by rauti on 2024-10-03
Hello,

I have a recently installed Kubuntu 22.04 along a recently installed Windows 11 system.
Both systems are installed in their own drive.
In Windows, fast startup is disabled, in BIOS, secure boot is disabled.

When shutting down via any normal method; power button, UI button or "sudo shutdown", the computer restarts after a few seconds in black screen state. The "journalctl --boot -1" log does not show anything interesting, however it is uploaded here: [https://pastebin.com/Tyr3dh6W](https://pastebin.com/Tyr3dh6W) .

The same thing happened consistently also when trying Kubuntu 24.04 and Ubuntu 24.04 live USB.
Also interestingly, Windows 11 sometimes has the same issue lately.

Another thing is, something within Ubuntu seems to cause corruption to the Windows drive.

---

