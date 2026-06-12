---
title: "Low Latency Kernels"
date: 2020-04-23
forum: General Help
---

### Post by bionic3epl on 2020-04-23
Are low latency kernels a Light Weight version of the Official kernels?

---

### Post by HermanAB on 2020-04-23
No, the reasons are much more complicated and subtle than that...

The low latency and multiprocessing improvements were made to the Linux kernel at the turn of century by Igor Molnar and others. Amongst other things, they removed all spin locks. The result is that Linux has very low jitter, better than BSD and far better than Windows. This work is why Linux is popular for video processing for example.

Note that the actual reason why Windows and MacOS have long latency and jitter, is because it is required by US and European export law, to prevent mass market operating systems from being used for Sonar and missile video processing.  So the jitter in Windows and MacOS is artificially made to be much worse and will always be so.

When someone states that: "Windows is not a real-time OS". That is actually a Legal statement, not just a technical statement.  You should read the export control laws of your country and look for "Mass Market Operating System Exemption", to understand what it is all about.

---

### Post by CatKiller on 2020-04-23
It's not lighter, and it's likely to perform marginally worse than the generic kernel for generic workloads. What it *does* give you is *consistency*. So your audio latency - as a prominent example - might be 6 ms always (the actual number dependent on your hardware and settings) rather than varying from moment to moment. For real-time audio work that capability is essential; for everything else it's not so important.

---

### Post by haltwo on 2020-06-07
Thank you. Quick reply. Great Info.

---

