---
title: "Boot only in recovery mode"
date: 2017-04-17
forum: General Help
---

### Post by horvatt on 2017-04-17
Dear All, 

This problem started with 16.10, and in 17.04 I am still stuck with it. With 16.04 everything was all right.

AMD A4-5300 Trinity with built-in Radeon 7480 GPU desktop will not boot in normal mode, but works fine in recovery mode after resume. In normal mode the computer restarts within seconds after starting the boot.

I suspect some issue with the graphics, as the main difference, as far as I know, between normal boot and recovery/resume boot is the graphics driver. The driver in use is Gallium 0.4 on llvmpipe (LLVM 4.0, 128 bits).

All help is appreciated warmly and thanked in advance!

---

### Post by mastablasta on 2017-04-19
my first advice is - use what works for you. if 16.04 works use it. it is supported until 2021.

if you really have to use the latest version, then be prepared to do some troublehsooting. logs in /var/log shoul dhopefully reveal why the reboot was forced. 

newer Radeon chips usually have descent support with the openasource graphics. if you really do think they are the cuplrint then upgrading them via oibaf or x-swap ppa's might be an option. 

but before you do that you should see if they are the cause. another option is you might need to use a certain kind of "switch". but this is hard ot say unless you can troubleshoot what is going wrong. 

also if you do find error messages in logs, you can use them to track down knonw bugs.

finally, do live OS sessions of 16.10 and 17.04 work?

---

