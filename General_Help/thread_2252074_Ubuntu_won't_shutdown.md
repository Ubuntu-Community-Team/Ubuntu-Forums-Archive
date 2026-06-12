---
title: "Ubuntu won't shutdown"
date: 2014-11-08
forum: General Help
---

### Post by christian.wansart on 2014-11-08
Hello,

I have an Acer Aspire E13 (ES1-311-P1D5) notebook. It has UEFI and SecureBoot enabled. I installed Ubuntu 14.10 on it, but afterwards I couldn't shutdown or restart the computer. It will only halt and I have to manually power down the notebook.

So far I tried to add
```
acpi=off
```
and
```
acpi=force
```
to the boot parameters.

Is there anything else I can try?

**edit:** I installed Fedora 20 for testing purpose.. Guess what? Shutdown and reboot works out of the box. :/
**2nd edit:** after updating on Fedora it broke... So, it has to be some package...
**3rd edit:** I started with an older Kernel. With Kernel 3.11 it works. Now I gotta find out, what's wrong.

---

### Post by geoaraujo on 2014-11-09
That's interesting because I'm having the same issue. I've already tried to install newer kernels (3.17, 3.17.2, 3.18-rc3) to see if that would solve the problem. It worked flawlessly before upgrading Kubuntu 14.04 (kernel 3.13) to 14.10 (kernel 3.16).

---

### Post by llamabr on 2014-11-09
What method are you using to try to shut down?

---

### Post by christian.wansart on 2014-11-10
I tried shutting down by clicking on the "Shutdown" button in the menu and I tried "shutdown -h now" and "shutdown -P now". I tried it with the 3.13 kernel as well: it didn't work!

---

### Post by kuckunniwi on 2015-08-12
Any progress on this? Have you managed to solve the problem? I have the same exact problem. Have tried to blacklist  blacklist dw_dmac and dw_dmac_core, as mentioned [here]("http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa"), but it made no difference whatsoever.

Am going to try adding backport ppa, see if newer kernels address the issue...Will post anything useful I come across.

---

### Post by kuckunniwi on 2015-11-10
Hi,

I'm using Xubuntu Trusty on an Acer ES1-311 and have this same exact issue. Kernel 3.19.0-32 and the issue still persists...

*sudo shutdown -P* now doesn't work for me either. Have also checked [here]("http://ubuntuforums.org/showthread.php?t=2121288") and none of the proposed solutions helped... 

Did acpi=force work for you? Any other suggestions?

---

### Post by kuckunniwi on 2015-12-20
No news on this front? I've tried different distros, from Xubuntu, Lubuntu, Ubuntu (all of the aforementioned from Trusty to Wily), Mint 17 (Mare, Cinnamon, KDE), Fedora 23, OpenSUSE 13...and this problem exists out-of-the-box (touchpad doesn't work out of the box with many of them either...). Is there anything I can do about this? I've been dealing with this issue for over a year now and have tried everything I've found....Any ideas/help would be enormously appreciated :)

---

### Post by RobGoss on 2015-12-20
Hello and welcome, Is this a new installation of Ubuntu 14.10? depending how you created your installation disk or USB thumb drive it may be worth to do a another fresh install to see if this will fix your problem.

---

### Post by kuckunniwi on 2015-12-20
> **RobGoss said:**
> Hello and welcome, Is this a new installation of Ubuntu 14.10? depending how you created your installation disk or USB thumb drive it may be worth to do a another fresh install to see if this will fix your problem.

Hey, thanks for your reply. I've tried fresh installs of Xubuntu & Kubuntu (14.04, 14.10, 15.04, 15.19), Mint, Fedora, Suse (newest releases as of November '15), so we're talking about at least 10 fresh installs using different distros. Another user had reported that things worked well in Fedora until he updated the kernel and it stopped working. 

I've tried *shutdown -h now* and *shutdown -P now*. I've tried *acpi=off* and *acpi=force* in etc/default/grub. I've also tried to blacklist *blacklist dw_dmac* and *dw_dmac_core* (as suggested [here]("http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa")), and don't have a clue what else to try.

When I first bought the laptop a year ago I also tried backporting kernels, but since we're now at 15.10 I'm guessing current stable kernels would have fixed the issue.

In fact, just went to turn on the laptop, and it appears the hard shutdowns are taking their toll: Now I just got a kernel panic when starting the system: not syncing: VFS: Unable to mount root fs on unknown-block (0,0). Actually, I've gotten 3 in a row and can no longer log into the OS...(not een recovery mode)

Any ideas?

---

### Post by kuckunniwi on 2015-12-21
Guys...I could really use some help...I've been literally asking around the forum for over a year....PLEASE, COMMUNITY, come to my rescue and I'll contribute back tenfold! (to the best of my abilities)

---

