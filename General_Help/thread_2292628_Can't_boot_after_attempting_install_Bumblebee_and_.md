---
title: "Can't boot after attempting install Bumblebee and freezing"
date: 2015-08-29
forum: General Help
---

### Post by thomas60 on 2015-08-29
Hi all,

As with many recent laptops, my laptop has the so-called "NVidia Optimus" technology, meaning it sort of switches between the integrated graphics and the graphics card in order to save power. I was frequently getting a bunch of nouveau errors and I suspected this was the culprit, so I tried installing Bumblebee. I attempted this using the command listed [here]("https://wiki.ubuntu.com/Bumblebee"):

```
[COLOR=#333333]sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic[/COLOR]
```

So far, so good, until it was writing something in a file in /boot/something/...generic (I'm sorry, I really can't remember) and then ubuntu froze completely. No mouse, no keyboard, nothing. So I had to shut down with the power button, after which I couldn't boot into linux anymore (it freezes right after I select it in the dual-boot screen). Thankfully Windows still works so I still have [I]something...
[/I]
I've been trying to get a live session working from my flash disk but that just won't work for some reason (it hangs on the loading screen on my laptop, even though it works fine on any other PC in the house). It took a couple tries before I could even install Ubuntu with it, so idk what's up with that. It's worth noting that I've been fighting with Linux for the past two weeks now. I accidentally deleted my Linux partition at first when trying to add unallocated space back to the windows partition, and that caused a whole load of problems, some of which are probably still not completely solved even after I did a reinstall.

As you can probably tell, I'm pretty much a noob, and this turned more into a bit of a rant than a question, but I hope you can still help me.

---

### Post by oldfred on 2015-08-29
What brand/model system? What nVidia chip?
Newer UEFI or or older BIOS?

I believe the newer nVidia versions do not need bumblebee to work, but may not switch to save power.

---

### Post by thomas60 on 2015-08-30
I have a Lenovo IdeaPad Y50-70-59444967, with a GTX 960M and a newer UEFI.

---

### Post by Vladlenin5000 on 2015-08-30
> **thomas60 said:**
> I have a Lenovo IdeaPad Y50-70-59444967, with a GTX 960M and a newer UEFI.

I think you need *nvidia-prime* instead of *bumblebee*.

---

### Post by mc4man on 2015-08-30
If you can get to a tty from the boot up or if not use recovery option in grub. From a tty just log in & then 
```
sudo apt-get purge nvidia* bumblebee
```

From recovery choose the fsck option to switch to rw vs. ro, then choose the root shell option to do the same apt-get purge.
After either, once apt-get completes go sudo reboot, that should get you back to a usable boot on the Intel gpu.

As far as bumblebee - nvidia-prime cannot be installed when trying to use bumblebee, it's also quite likely that /etc/bumblebee/bumblebee.conf is either wrong as far as KernelDriver= & also bumblebee-nvidia likely installed the nvidia 304 drivers which may not be any good for the 960m 

nvidia-prime & the 346 drivers could be ok, nvidia-prime is a session only deal, either all nvidia or all intel. It's major flaw is there is no vsync possible when using nvidia which can make for a poor Desktop & video playback experience.

bumblebee could be more useful as it's app specific but you'll need to research how to get it working & configured for 346 drivers.

(-slightly ot - I just tested a laptop with a 960m a bit before rma'ing back. It worked ok with nvidia-prime (no vsync so no good for me), bumblebee would not work but didn't really pursue as the laptop was going to be returned because of boot up issues with some distros, ie. - 
14.04.1 - good
14.04.3 - no boot up possible
15.04 - good
15.10 no boot up possible
fedora 22 - no boot up possible

---

### Post by thomas60 on 2015-08-30
> **mc4man said:**
> If you can get to a tty from the boot up or if not use recovery option in grub. From a tty just log in & then 
```
sudo apt-get purge nvidia* bumblebee
```

From recovery choose the fsck option to switch to rw vs. ro, then choose the root shell option to do the same apt-get purge.
After either, once apt-get completes go sudo reboot, that should get you back to a usable boot on the Intel gpu.


Wow, that was so simple! I really thought I was in deep trouble. Thanks so much!

I'll do some more research on what drivers to use. I'm not doing any gaming (yet) on linux so it's not that much of a hurry, I just hope those nouveau errors stopped (haven't seen them yet).

---

### Post by mc4man on 2015-08-30
> **thomas60 said:**
> Wow, that was so simple! I really thought I was in deep trouble. Thanks so much!

I'll do some more research on what drivers to use. I'm not doing any gaming (yet) on linux so it's not that much of a hurry, I just hope those nouveau errors stopped (haven't seen them yet).

Because of the vsync issue with nvidia-prime on my current lenovo (y510p) I just use the Intel gpu for Ubuntu. In that case I've found it didn't hurt & is possibly positive to remove the nouveau drivers as they aren't needed. (maybe for bumblebee, maybe not, certainly not for nvidia-prime

You could ck. with - 
```

sudo apt-get purge xserver-xorg-video-nouveau
```
And see if nouveau 'errors' go away.

---

