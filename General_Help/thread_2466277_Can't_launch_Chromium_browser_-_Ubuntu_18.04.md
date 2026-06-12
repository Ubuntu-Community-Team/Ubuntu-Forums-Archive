---
title: "Can't launch Chromium browser - Ubuntu 18.04"
date: 2021-08-24
forum: General Help
---

### Post by heatopher2 on 2021-08-24
Hi, this has only just happened. Chromium isn't launching either from clicking on the icon or when I try to start it from the command line. Here's what I get if I try from the command line, with "chromium-browser &"
```
mesa: for the --simplifycfg-sink-common option: may only occur zero or one times!
mesa: for the --global-isel-abort option: may only occur zero or one times!
mesa: for the --amdgpu-atomic-optimizations option: may only occur zero or one times!

[7778:7778:0100/000000.312348:ERROR:sandbox_linux.cc(374)] InitializeSandbox() called with multiple threads in process gpu-process.
[1]  + 7743 trace trap (core dumped)  chromium-browser

```
I tried googling all that, but didn't find anything that seemed especially relevant in this case. Thanks y'all ):P

---

### Post by heatopher2 on 2021-08-28
Well, nobody replied, but I did get it to work again, just by installing it from the Ubuntu software install thingy. That's fine, but now I have two instances of Chromium showing in the applications menu. Not a big deal, but I guess I would like to know how to get rid of the silly duplication. I think I saw that with another application that I must have installed from two different places. What are you supposed to do in such cases?

---

