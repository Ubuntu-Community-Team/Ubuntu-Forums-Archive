---
title: "[SOLVED] Virtualbox broke my X"
date: 2008-07-08
forum: General Help
---

### Post by blazercist on 2008-07-08
I have 

Ubuntu Hardy 8.04.1 
Nvidia 9600GT (Proprietary Driver)
uname -r = 2.6.24-19-generic

I installed virtualbox from the repos, it didn't work.  It froze when mounting ISO files, but thats not that problem.

I uninstalled virtualbox, all went well.  Then I went to the virtualbox website and downloaded the binary for Ubuntu Hardy 8.04 and installed the installation went fine and I went to reboot my machine.  

Bam! I can only get bulletproofX, I tried 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

It worked, well at least vesa worked, but as soon as I try to 

```

sudo nvidia-xconfig

```

It breaks again, apparently something wrong with the nvidia module.....


I tried to uninstall virtualbox again, but what I've noticed is that even after

```

sudo apt-get remove virtualbox

```

If I alt+f1 during the boot process my box is still loading the virtualbox kernel modules...

So I'm pretty sure that removing virtualbox completely is what I need to do to fix my X, it seems that for some reason or the other the virtualbox modules don't play well with the nvidia module and the nvidia module will not load.

So anyone got any idea how to do this?  **MIND YOU IM TALKING ABOUT X ON THE HOST**

---

### Post by blazercist on 2008-07-08
Oh and if its possible a solution that I could do using SSH would be nice :)

---

### Post by blazercist on 2008-07-08
nevermind, I solved the problem, I don't know why exactly this happened but blacklisting "nv" in /etc/linux-restricted-modules and reinstalling the proprietary nvidia driver seemed to fix the problem.

---

