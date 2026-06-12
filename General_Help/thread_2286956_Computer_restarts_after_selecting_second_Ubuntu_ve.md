---
title: "Computer restarts after selecting second Ubuntu version in GRUB"
date: 2015-07-15
forum: General Help
---

### Post by enginerd22 on 2015-07-15
Hello all,

Background: I just bought a new hard drive and installed Ubuntu 14.04.2 LTS on it. I decided it might be nice to have a backup partition incase the config on this one got messed up, so installed Ubuntu again on another partition. This created a problem where grub gave a filesystem not found type error, which I solved by [reinstalling grub]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") from the live USB drive. So far so good. Both OSs show up in the boot list under GRUB. If I try to boot from the second one, though, the computer just restarts. No error message I can see which makes this real hard to look up on google. Anybody have any ideas what's happening?

I've attached a screenshot of partition structure (second install is on /dev/sda5). I don't mind any solution which involves blowing away /dev/sda5 (the second install), but would prefer not to reformat the whole drive. Thank you all.

---

