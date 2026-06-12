---
title: "WebGL stopped working in chromium"
date: 2013-10-31
forum: General Help
---

### Post by seb_stein on 2013-10-31
These days, WebGL stopped working in chromium, but it is still working in Firefox. On the command line, I can see the following error messages while trying to open get.webgl.org in chromium:

```

libGL error: open uki failed (Die Operation ist nicht erlaubt)
libGL error: reverting to (slow) indirect rendering
libGL error: open uki failed (Die Operation ist nicht erlaubt)
libGL error: reverting to (slow) indirect rendering
libGL error: open uki failed (Die Operation ist nicht erlaubt)
libGL error: reverting to (slow) indirect rendering
```

I'm running kubuntu 13.10 with all updates and fglrx-updates. WebGL already worked in chromium when I set up the system a few days ago.

Here the output from fglrxinfo for my system:

```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series 
OpenGL version string: 4.2.12337 Compatibility Profile Context 13.101
```

I also tried the official chrome browser with the same result.

I also tried resetting my X configuration without success via:

```
sudo aticonfig --initial --force
```

Any ideas what could have changed? Any pointers?

---

