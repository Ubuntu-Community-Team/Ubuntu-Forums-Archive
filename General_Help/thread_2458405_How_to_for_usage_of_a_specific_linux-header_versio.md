---
title: "How to for usage of a specific linux-header version?"
date: 2021-02-24
forum: General Help
---

### Post by omanidos on 2021-02-24
[using ubuntu 20.04]

After update to linux-image-5.8.0-44-generic the mouse and keyboard do not work in the login screen (they work until the sound comes).

When using grub to boot with the 43 version everything work fine.

How do I force the OS to boot with the 43 version by default?

---

### Post by deadflowr on 2021-02-24
Does this give you a general idea of what you can do: [https://unix.stackexchange.com/questions/198003/set-default-kernel-in-grub]("https://unix.stackexchange.com/questions/198003/set-default-kernel-in-grub")?

Outside that you would probably want to report the issue:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")
Otherwise you'll either have to rely on an outdated, and potentially security averse kernel,
or the Ubuntu kernel developers might never know there's a problem and newer kernels will never resolve it.

---

