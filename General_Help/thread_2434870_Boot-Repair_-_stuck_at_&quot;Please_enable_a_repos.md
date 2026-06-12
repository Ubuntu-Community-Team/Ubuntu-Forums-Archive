---
title: "Boot-Repair - stuck at &quot;Please enable a repository containing...&quot;"
date: 2020-01-12
forum: General Help
---

### Post by nosnoop on 2020-01-12
Cloned a failing hard disk with Clonezilla - did not notice any errors displayed.
The cloned disk won't boot.

This is the boot-info from Boot Repair Disk:
[http://paste.ubuntu.com/p/ZhsFSr6tWs/](http://paste.ubuntu.com/p/ZhsFSr6tWs/)

Apparently, the bootloader was absent from the cloned disk.

Tried using Boot-Repair Disk, but got stuck on
"Please enable a repository containing the [grub2] packages in the software sources of Ubuntu 14.04.5 LTS. Then try again"

I checked all the entries in Software & Updates, reload and it seems to be downloading.   But that window keeps popping up.
Maybe most of the repo has 14.04.6 instead of 14.04.5?
How can I add the repo for 14.04.5 (where?) or maybe mount a downloaded iso as source? (tried it without success, though I may not be doing it correctly)

Tried using Boot-Repair live usb, but it has a lot of problems - complaining about no internet (which I do), and I have to go to Advanced Option to turn off check internet.
And the Software and Updates won't reload (Error - Out of pty devices).

Works a bit better with Ubuntu Live USB and install Boot-Repair Disk, but still could not get past the enable a repository error.

Also tried grub-install from Ubuntu Live, but did not work.    Though I am not exactly sure which partition to mount for the grub-install.    Should it be sda1 or sda2?

TIA for any pointers.

---

### Post by CelticWarrior on 2020-01-12
14.04 is End of Life, no repositories are available, and it shouldn't be used due to security concerns.
Cloning was a bad move. What you should have done - and can and should do now - is to backup your personal files and then install from scratch a supported release.

---

