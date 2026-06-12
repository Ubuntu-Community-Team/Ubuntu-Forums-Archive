---
title: "Slow boot time on ssd (~10s dev-sda2.device)"
date: 2021-05-18
forum: General Help
---

### Post by newtonloquito on 2021-05-18
Hi, I have installed xubuntu 21.04 on a new ssd and I have been trying to see how fast can it boot. My pc has a very slow firmware time (nearly 13s, an asus prime a320 motherboard with csm disabled), but the userspace was something like 2 seconds so I still got around 20 secs from pressing the power on button to getting to the desktop. However, I have copied the files that were in my old /home folder from a fedora system that still exists on my secondary drive (an hdd), and after doing that my boot time went up by nearly 10 seconds. When I run systemd-analyze blame it says that the biggest culprit is the "9.438s dev-sda2.device" with sda2 being my root partition on the SSD. I had pretty much the same problem with my hdd, with nearly 10 seconds wasted in mounting the root partition (In neither of both did I separate the home folder onto it's own partition, but if it speeds thing up I might consider doing it). I have disabled fsck for sda2 and the EFI partition since and the boot time even went up, so I will be enabling it again. How can I optimize this? I just have to delete everything and reinstall, create a partition only for the /home folder or should I do something else? Thanks in advance.

---

### Post by HermanAB on 2021-05-18
Well, this is the 21st century.  Don’t reboot.  Use Hibernate and Suspend, same as with a laptop machine.  With a SSD, the machine will awaken instantly.

---

### Post by newtonloquito on 2021-05-18
I think I will, thanks!

---

### Post by newtonloquito on 2021-05-18
Well I runned "systemctl hibernate", the screen glitched and after that i got the same 30 sec boot time as always. Seems like my pc doesn't want to hibernate. I read that for using hibernation I should disable secure boot but my motherboard doesn't have that option (or at least is very hidden). Suspend does work, but with a very unstable power supply I'm not sure that could work for sustained periods of time XD.

---

### Post by newtonloquito on 2021-05-18
I deleted all the stuff I copied from the old hdd and now my boot time  is even worse than before, seems like that wasn't the problem

---

### Post by oldfred on 2021-05-18
Have you updated UEFI firmware and SSD firmware to latest available?

Is system doing a fsck on partition when mounting. 
Years ago, it ran fsck every 40 reboots. Now with ext4, it just should do a check to see if ext4 has issue.

Some things to review:
Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

---

### Post by newtonloquito on 2021-05-18
Problem solved. I just reinstalled the OS, used the default formatting (before I used custom, although I don't think this is what solved the issue).

---

### Post by GhX6GZMB on 2021-05-18
> **HermanAB said:**
> Well, this is the 21st century.  Don’t reboot.  Use Hibernate and Suspend, same as with a laptop machine.  With a SSD, the machine will awaken instantly.

Not quite.
Actually, a resume from Hibernate is a bit slower than a cold boot. Hibernate will do a cold boot and then restore the session. For Suspend, I agree with you.

---

