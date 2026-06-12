---
title: "Installing Clang 4.0"
date: 2017-07-27
forum: General Help
---

### Post by ordak on 2017-07-27
Hi,

I installed Clang 4.0 using "Synaptic Package Manager". But running the following command I get:

```
clang --version

clang version 3.8.0-2ubuntu4 (tags/RELEASE_380/final)
Target: x86_64-pc-linux-gnu
Thread model: posix
InstalledDir: /usr/bin

```
How can I use latest Clang compiler ?

---

### Post by ordak on 2017-07-28
I removed clang-3.8 via _Synaptic Package Manager_. It automatically removed clang package too. Now if I want to install clang package, it wants to install version 3.8 packages rather than version 4.0 packages.

---

### Post by mc4man on 2017-07-28
"clang" is just a dependency package. If you want 4.0 then install it specifically, i.e., clang-4.0
> clang-4.0 --version
clang version 4.0.0-1ubuntu1~16.04.1 (tags/RELEASE_400/rc1)
Target: x86_64-pc-linux-gnu
Thread model: posix
InstalledDir: /usr/bin


---

### Post by ordak on 2017-07-28
```
clang-4.0 --version

clang version 4.0.0-1ubuntu1~16.04.1 (tags/RELEASE_400/**rc1**)
Target: x86_64-pc-linux-gnu
Thread model: posix
InstalledDir: /usr/bin

```

Maybe it is because rc1:release candidate 1.

---

