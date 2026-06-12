---
title: "Some things I can and can't do on Edgy"
date: 2006-11-02
forum: General Help
---

### Post by dxdemetriou on 2006-11-02
hi,
the problem I have now on Edgy is with the Synaptic and Software Updates. There are times that when it makes install, it goes out of memory, the disk works full, and I can't even move the mouse. I saw somehow that kills programs because the system is out of memory and I don't know how to fix it. I will try maybe with command line the updates if there is no solution now. I have seen a thread in forums that the edgy is for developers and persons that knows how to fix some problems, but no in the main site I downloaded the cd.

Other problem I had is when I pressed the sleep button from my keyboard, it goes to suspend but doesn't work on my pc and turns off immediatelly. I fix it from Configuration Editor->apps/gnome-power-manager and unchecked the can_suspend.

Other is that I moved my installed edgy from k7 1800 to 2200. I had problem with alsamixer, and I fixed it with removing the ~/.asoundrc. The other is that I tried to move from the nvidia to onboard card without success. Then I tried with another nvidia but also didn't work. Then I make sudo --purge remove nvidia-glx-legacy, and wants to remove packages for X11 that are in synaptic, but not in repos, so I didn't. Then I just add the nvidia-glx, and reconfigure it. That I want to do is to can work the onboard card that normally worked with VIA, but didn't work on edgy.

Is there any place that can I find the changes on commands on Edgy? I used to use the shutdown -F -r now, but don't work with Edgy.

Other problem is the modify during the upgrade of fstab, and I haven't swap. I try to re-enable it.
thanks

---

### Post by an.echte.trilingue on 2006-11-02
not quite sure what you are looking for with a lot of that, but my prefered command to shut down is sudo init 0

---

### Post by girishv on 2006-11-02
sudo halt -n works well for me on my laptop
g

---

### Post by dxdemetriou on 2006-11-02
I mean that I want to make force check the root partition after some power lost. I used the "shutdown -F -r now", to reboot and before mount the root partition to make fsck.

---

