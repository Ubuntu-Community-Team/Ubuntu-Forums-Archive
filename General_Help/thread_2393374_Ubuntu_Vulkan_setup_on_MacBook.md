---
title: "Ubuntu Vulkan setup on MacBook"
date: 2018-06-02
forum: General Help
---

### Post by bastianblokland on 2018-06-02
Hi everyone,

I've been trying trying to setup my mid 2015 macbook for vulkan development under Ubuntu. I have vulkan running on osx using the MoltenVK library but that unfortunately doesn't support the debug layer which hinders development. So i was naive and thought i could just dual boot linux and run native vulkan there.

The gpu in the macbook is a AMD R9 m370x (as far as i know of the GCN 1.0 generation)

Installing Ubuntu 18.04 was of-course no problem, but it was running on the 'radeon' drivers without Vulkan support. First i ventured into the proprietary amd driver direction, amd does have a driver listed for the m370x but only for Ubuntu 14.04. I tried to install that anyway but it resulted in allot of flashes and it refused to boot into ubuntu. Log was saying something like 'Amdgpu does not export dri extension'. Then i did some researching into the opensource amdgpu driver which some people say supports the GCN 1.0 cards. But when i tried to force that driver by blacklisting the radeon driver i only got stuck on a purple screen while booting.

So i'm a bit lost, is it just impossible to run Vulkan in linux on a m370x or am i missing something?

Thanks in advance.

---

