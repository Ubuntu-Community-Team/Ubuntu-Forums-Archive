---
title: "Dell inspiron N5110 overheating"
date: 2013-04-02
forum: General Help
---

### Post by Raja narayan on 2013-04-02
I'm using ubuntu 12.10. Whenever i am working in ubuntu laptop gets overheated. But its not the same in Windows os. I am using Dell inspiron N5110. Nvidid graphics card, i5 processor.CPU temp is around 72 deg. so how to solve this problem!!

---

### Post by eminemix on 2013-05-12
Hello.

I have the same issue as you. On Ubuntu, for some reason, the dedicated gpu will work on load. Disable it.

You must disable the GPU after booting into linux.
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

Before you shut down your laptop you should enable it again
echo ON > /sys/kernel/debug/vgaswitcheroo/switch

I have put a bug report about this. A bot answered. =)

Please star it (This affects me on top). Will help us, N5110 users..

[https://bugs.launchpad.net/ubuntu/+bug/1176322](https://bugs.launchpad.net/ubuntu/+bug/1176322)

---

