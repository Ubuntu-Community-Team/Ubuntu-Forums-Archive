---
title: "vmlinuz changed after fresh install 12.04.3 on secure boot enabled system"
date: 2013-09-01
forum: General Help
---

### Post by Founder_Fang on 2013-09-01
i just install 12.04.3 on a secure boot enabled system, after installation i run debsums, it is quite strange to find out that /boot/vmlinuz-3.8.0-29-generic has been changed. does it means my system already compromised?

---

### Post by Bashing-om on 2013-09-01
Founder_Fang; Hi !

Let this be food for thought ... vmlinuz-3.8.0-29-generic is the latest kernel .. on a fresh install it would not have been installed with that kernel.
Did you update the system between times running "debsums" ???

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by Founder_Fang on 2013-09-02
Bashing-om, Hi !
I select "install updates during installation" when install the system, after install finished and system reboot, [COLOR=#000000]3.8.0-29 is the selected kernel. i am sure vmlinux-3.8.0-29-generic exist before run debsums.[/COLOR]

---

### Post by Bashing-om on 2013-09-02
Founder_Fang; Hello once more.

I am at a loss to explain why there would be a change in the kernel. The likely hood of compromise is very low due to the nature of how the linux file system is built, and the verifications of files from ubuntu's repositories/file system management. The system will not install an altered file (md5sums).

I remain open to continued education; I know of no outside source that can gain access to alter the kernel.

[INDENT][INDENT]security in linux is #1
[/INDENT][/INDENT]

---

### Post by Dennis N on 2013-09-02
Relevant?

From the release notes:
> By default, the 12.04.3 point release will ship with a newer 3.8 Ubuntu kernel from Ubuntu 13.04

---

### Post by Founder_Fang on 2013-09-02
new findings - install a fresh system in virtualbox, use ubuntu-12.04.3-desktop-amd64.iso, debsums also report /boot/vmlinuz-3.8.0-29-generic changed.

in my secure boot enabled system, there is also a /boot/vmlinuz-3.8.0-29-generic.efi.signed, how can i check which kernel is actually used? does it improve security if only boot from signed kernel?

---

