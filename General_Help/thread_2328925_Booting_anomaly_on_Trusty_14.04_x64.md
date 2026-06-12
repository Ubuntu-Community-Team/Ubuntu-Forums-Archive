---
title: "Booting anomaly on Trusty 14.04 x64"
date: 2016-06-25
forum: General Help
---

### Post by Tokugawa_Ieyasu on 2016-06-25
Since I updated my Trusty 14.04 x64 about 2-3 weeks ago, it's behaving (in regards to booting only) very strangely. When I try to boot normally, it seems to boot properly, but at the end, when the login screen should appear, nothing happens - the screen stays black. I've already waited a few minutes, but nothing happens anymore. Hitting Esc and watching the bootlog was inconclusive, as I didn't find any errors or anything which could cause this.

 So I tried booting into recovery mode and tried out the option to fix packages (you never know). While it didn't find anything, I still had it resume booting, and it booted just fine. In the hopes that the problem, whatever it is, might be fixed, I tried booting normally, with the same problem - just a black screen, when the login screen should come up.

 So once again, I booted into recovery mode, and this time, I tried the option to resume booting right away, without doing anything. The system booted just fine, the login screen came up, I could login just fine, and the system on the whole is working fine. I've been trying several kernels from the Ubuntu kernel mainline ppa (up to the latest 4.6.2 one) since then, but with all of them, it's the very same anomaly - if I try to boot normally, the system seems to be booting normally, but then the screen stays black, and the login screen never appears. If I however boot into recovery mode, and from there resume booting immediately, without doing anything before, it boots just fine, and the system is running perfectly fine. It has stayed that way since, even though I always install all the updates that become available.

While this is not a serious issue but just a minor inconveniency, it's still very strange. Any idea what could be causing this?

---

