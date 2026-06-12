---
title: "Ubuntu 16.04 libvirt-guests.sh [6917] - running guests under URI address default: no"
date: 2017-07-07
forum: General Help
---

### Post by Jedrek30 on 2017-07-07
[COLOR=#111111][FONT=Ubuntu]I have upgraded from Ubuntu 15.04 Vivid to 16.04.02 LTS Xenial and everytime I shutdown the system, the system hangs at the screen saying: "libvirt-guests.sh [6917] - running guests under URI address default: no running guests" and never shuts down. I have to manually shut it down everytime, which obviously is a pain. How can I fix this?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have done some investigation and here's what I've found.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have uninstalled libvirt, kvm and qemu:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**sudo apt-get purge libvirt* kvm qemu***[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Reboot the computer and the error message is no longer there, however I noticed some error messages at boot saying something that "FAILED Qemu .... It flashes so quickly and I am not able to read what exactly it says. I installed libvirt again to get rid of the errors at boot:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**sudo apt install qemu-kvm libvirt-bin**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]and the problem is back![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So is this script trying to shutdown my virtual machines? It looks like it does but since it does not find any it hangs? I don't have any virtual machines, though. I used to have one, but I removed it. What is interesting, my PC hangs at shutdown randomly, that is sometimes it hangs for like 15 seconds and it shuts down but in most cases it hangs forever. So this happens randomly.

[COLOR=#222222][FONT=Verdana]I contacted **virsh support** and one supported told me he's got virsh installed on his laptop and he runs exactly the same Ubuntu as I do and he does not have this problem. So there must be something else then... 

[B]uname -a
[/B][/FONT][/COLOR]Linux Home 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

[B]lsb_release -a
[/B][COLOR=#222222][FONT=Verdana]No LSB modules are available.[/FONT][/COLOR][/FONT][/COLOR]
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

**virsh --version**
[COLOR=#111111][FONT=Ubuntu]1.3.1[/FONT][/COLOR]

---

### Post by farrinux on 2017-07-07
One thing you could try is to purge qemu-kvm libvirt-bin again.  Then upon reboot have your finger on the pause button.  When the error comes up push the pause button so you can read it.  Another would be just to go to the boot log, how ever that being said you would have to google for it. I think it is in /var/log/ somewhere. My guess is there is something in the system boot that points to qemu-kvm libvirt-bin and you will probably have to manually remove it.  If your system boots even with the error and shuts down correctly, you could ignore it.  But that being said I could not, so I understand.

---

### Post by Jedrek30 on 2017-07-07
I unexpectedly received a reply from virsh support saying that I could actually disable libvirt-guests, which I didn't realize was possible.

[B][FONT=arial]systemctl disable libvirt-guests

[/FONT][/B][FONT=arial]&#8203;Works like a charm!!!

I still however do not know the root cause but at least I can now reboot without any issues.[/FONT]

---

