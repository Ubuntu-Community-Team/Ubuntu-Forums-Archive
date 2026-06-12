---
title: "General questions on updating components"
date: 2006-10-15
forum: General Help
---

### Post by pentarinfosys on 2006-10-15
Linux user for over 6 years, 3 of those professionally, but new to Ubuntu. I just bought a 64-bit Gateway laptop, and SUSE (my previous distro of choice) won't load on it due to a hardware issue surrounding the onboard sound, a problem Ubuntu can get around. There are, however, two significant issues that I've been trying to work through.

The first is the internal wireless, which is a broadcomm 4311 chip. I've tried ndiswrapper, and have the driver that's appropriate for the card, but it's not working due to an "ntoskrnl" error. The suggested solution is to upgrade to the latest version of ndiswrapper, which is 1.25. The installed version is 1.8.

The sound is still a problem of course. The problem is that the SigmaTel 9250 chip isn't responding the way it should, resulting in a flood of **hda_codec: invalid dep_range_val 0:7fff** on autoprobing. This is what brought SUSE down, and the problem Ubuntu developers fixed back in March. Or, at least, they fixed it enough so I can boot. Anyway, the suggested solution here is to upgrade to the lastest alsa packages, which would be 1.0.13. The installed version is 1.0.10.

In both cases, I would like to try getting these updates, to prevent myself from having to take this laptop back to Windows to get this stuff to work. However, I'm a little leary of just ripping pieces out of Ubuntu; it's a Debian-based system, and I've always worked with either SUSE- or RedHat-based systems. I'm aware it shouldn't matter. I'm also aware that it often does.

When I've tried to remove the alsa-1.0.10 packages, for example, it wants to remove ubuntu-base and ubuntu-minimal. Without know what those are, and how it will impact the system, I'm hesitant. So I'd like some advice from the more experienced among us. What hurdles am I looking at to get these two updated safely? It'd be great if there were some apt repositories that had the latest and greatest of both of these, so I could count on apt doing to the job right. Anyone know of some?

Thanks.

---

