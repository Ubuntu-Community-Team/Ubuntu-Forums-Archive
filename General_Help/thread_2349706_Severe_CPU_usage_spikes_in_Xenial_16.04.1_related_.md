---
title: "Severe CPU usage spikes in Xenial 16.04.1 related to Firefox/plugin-container/kworker"
date: 2017-01-17
forum: General Help
---

### Post by alexam on 2017-01-17
My distro is 16.04.1 LTS (Xenial Xerus), it uses Gnome as DE. Long story short, I upgraded to it from Trusty and had worked for a long time without issues until lately. I don't update my system too often, as updates often create issues, while rarely provide enhancement, imo. That's what happened this time too. I decided it's time to apply all those ~700mb of patches accumulated so far, which also included some kernel patches. Several days later my system started to freeze constantly.

Here is a brief overlook of my usage habits. I run Ubuntu as a vmware virtual machine with windows 7 as a host. I never shutdown both, unless I'm forced to, before I put my PC into standby I suspend this vm and continue to work with it the next day.

Here is what the issue now. After each vm restart it works fine for several days (2-4), there are some slowdowns sometimes, but it's bearable. Then it suddenly worsens, severe freezes start to happen first once per 10 mins, then once per 5 mins, then even more often. It ranges from really irritating slowdowns to a complete halts for up to 5-30 seconds, and affects both host and the vm. When this happens, in windows task manager I see that vmware process consumes almost all of CPU  (which is quad core i5 ticking at 4,5GHz, more than enough for a bunch of vms), load jumps to 100%; in my single Ubuntu vm "top" shows that Firefox, plugin-container, upstart and kworker processes take extreme amounts of CPU (100+) for the duration of this spike.

Restarting Firefox helps to mitigate it for a couple of hours, but then those "seizures" start to happen again and usability quickly - much quicker than after a complete restart of the vm - degrades again.

When this start to happen that virtual machine - and the host machine too - effectively become unusable for me. I need to restart this vm to get another several days of issue-free work. I never saw something like that for years of using ubuntu 14 and 6 months of using xenial, prior to this update.

What can I do to fix it, or report it?

---

