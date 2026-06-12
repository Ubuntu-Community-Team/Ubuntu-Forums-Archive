---
title: "[SOLVED] 20.04 - boot splash stops boot process"
date: 2020-04-21
forum: General Help
---

### Post by maestrobwh1 on 2020-04-21
[Edit- this was the fix] For some odd reason, "vt.handoff=7" wasn't being added to my grub.cfg.  I added it to my /etc/default/grub after "splash" and it works now.  I always remember seeing it in grub.cfg, then when I hit "e" to edit my grub configuration while trying to resolve this issue, I noted it was not there.  It used to just get added, and was not part of what I remember seeing in /etc/default/grub.  it is there now, works well.

20.04 worked fine initially.  I know it is supposed to show my machine's logo (UFEI - Thinkpad X1 Carbon, first gen) with Intel graphics card 4000 IVB-GT2 but it never did show "Lenovo", but the little white spinning wheel worked at the bottom up to the login screen, then periodically a few days ago, it would just halt the boot process and just spin, and only holding down the power button (and sometimes it took a few times, as if I turned the machine back on, it would continue from where it was at), and so I would have to reboot and remove "splash" from the kernel opts.  Now it just will not ever complete booting with "splash" enabled so for now, it has been removed from /etc/default/grub.

it is more of an eye candy flaw, and affects no real thing, but it was nice to have.  I don't have a lot of intuition beyond this to help track down the issue.  If anyone replies with where to look for an error log, I might be willing to hit e periodically at the grub boot and add "splash" then reboot and look for where ever the error would be logged.

---

### Post by johnjdailey on 2020-07-30
I had the same issue on my UEFI Thinkpad T430 with intel graphics and this solution worked for me. Thank you very much for sharing. You’re awesome.

---

