---
title: "Ubuntu Livepatch"
date: 2024-02-13
forum: General Help
---

### Post by stevefxp on 2024-02-13
Hello all,

I am new to Ubuntu, as I come from an extensive Windows background. Windows has patch management in the form of WSUS. I noticed that Canonical has Livepatch. I am now taking over reponsibility for a dozen or so Ubuntu server vms. I would like to employ some form of patch management in this space. My goal is to patch production vms on a quarterly basis. Can Livepatch do this? Is there a comprehensive installation/configuration guide to having an on prem Livepatch server or can I just use the cloud Livepatch and do my thing. Is there a GUI to manage all of this?

Thanks,
Steve

---

### Post by deadflowr on 2024-02-13
You're thinking of 2 different things.

What you want is something like Landscape to handle updating multiple systems.
Landscape is a paid service, so you might dig around for alternatives.
[https://ubuntu.com/landscape](https://ubuntu.com/landscape)


Livepatch deals in one thing and one thing only, patching a running kernel to extend the uptime.
Normal kernel patches require a system reboot to apply them.
Livepatch is a function to apply those patches to the running kernel, which allows you to delay a reboot.
Good for systems that you cannot reboot immediately.

---

