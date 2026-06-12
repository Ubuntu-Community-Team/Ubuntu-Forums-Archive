---
title: "hotplug errors on system boot"
date: 2004-10-27
forum: General Help
---

### Post by beeldings on 2004-10-27
I installed Ubuntu this morning and everything went off without a problem. Unlike the previous distributions of Linux I used (Mandrake, Slackware, Fedora Core), I receive a hotplug error when during the boot screen. I don't remember the exact message that is posted, but I believe it involves hotplug and also posted a message about PCIE. I use my Linux computer for basic computing (i.e., web browsing, e-mail, word processing, CD burning, etc.) so I do not think I need the hotplug service. Is there a way for me to disable hotplug from being loaded while the system is booting?

Other than that annoyance, I must say that I am very satisfied with the quality of the Ubuntu distribution. Ubuntu has permanently replaced Fedora (which replaced Mandrake) as **the** distribution for this computer. It even passes the "Mom Test". :)

---

### Post by Burgundavia on 2004-10-27
I think there is a bugzilla entry for this. It is simply a matter of too much error reporting, rather than an actual error.

Corey

---

### Post by Burgundavia on 2004-10-27
Here is the bugzilla entry: [https://bugzilla.ubuntu.com/show_bug.cgi?id=1869](https://bugzilla.ubuntu.com/show_bug.cgi?id=1869)

I get the same errors but have no problems with hotplugging.

Corey

---

### Post by jdong on 2004-10-27
It just is a hotplug fluke. Hotplug "thought" that your system needed PCI-Express Hotplug drivers and loaded those drivers. The hotplug drivers couldn't find a PCI-E Hotplug host controller, and started yelling at you. Doesn't break anything; just a minor annoyance. Those should go into the syslog, not terminal output IMO.

---

### Post by beeldings on 2004-10-27
Thanks for the help. I'm just glad to know nothing's broken.

---

