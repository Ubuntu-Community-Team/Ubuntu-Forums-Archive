---
title: "Feisty won't start (or: nvidia driver trouble)"
date: 2007-04-22
forum: General Help
---

### Post by ike on 2007-04-22
I have used Ubuntu since the 4.10, i believe it was called the Warty Warthog, and I have had little problems with my computer ever since. But, upgrading to Feisty yesterday left my computer unusable. I first tried to do an upgrade, but since the desktop effects didn't work i just thought I'd reinstall the whole thing. I booted off my Feisty CD and everything looked fine.

Then, the installer hanged while I was setting up the partitions (manually). I restarted, and again it hanged and I tried a few times until it finally worked. I also noticed that the partitioning tool confuses the partition sizes sometimes. If i choose to edit a partition, the default new size (which should be the actual size) is equal to the space left on the partition. Pressing ok without changing it didn't resize the partition, however.

I tried installing nvidia-glx and enabling desktop effects. I got the spinning cube and wobbling windows  alright, but the window borders where missing. I turned it off and tried to use the nvidia-glx-new instead, but that just made X crash at boot.

I have tried so many combinations now that I don't really know what I'm doing anymore. At the moment my computer won't event come to the login screen. I get a low-res brown screen with a mouse pointer, and it just sits there forever. I can't even go to another console (tty) by pressing ctrl+alt+F1.

I tried running
dpkg-reconfigure -phigh xserver-xorg
from the recovery console, trying both the nv and vesa driver, but that didn't help me.

I have read a bunch of threads here in the forum about similar problems, but none of the solutions mentioned seem to help me.

I'm going for a reinstall again, and then I need to get the nvidia driver working somehow. I read that the proprietary software manager is broken (it tells me that I don't need any proprietary drivers, which is not true), so I guess I'll have to use another method. Afaik, these methods are available:
* downloading and installing drivers from nvidia.com
* using envy
* nvidia-glx (which doesn't do the trick for me since Feisty)

Which one is preferred? In edgy I had to reinstall the nvidia driver (downloaded from nvidia.com) every time the kernel was updated (or else X wouldn't start), which I would really much like to avoid with Feisty.

Ok, now that I tried to boot off the Feisty CD it tells me "BUG: soft lockup detected on CPU#0!" and then it crashes. Yes, I have checked my cd for defects. Could it be a problem that I burned my Feisty CD on a (intel) mac?

---

### Post by tictacman on 2007-04-22
> BUG: soft lockup detected on CPU#0!" and then it crashes.

Are you using wireless network card by any chance? I used have this error a lot before I managed to configure my card properly.

---

### Post by ike on 2007-04-22
> **tictacman said:**
> Are you using wireless network card by any chance? I used have this error a lot before I managed to configure my card properly.

Yes, I do (PCI). What was the problem with your card?

---

### Post by tictacman on 2007-04-22
My card is an edimax with a rt61 chip (also a pci card).  Its all fixed now, but its a bit of a long story.  You can read all my threads about it by clicking on my name and selecting the appropriate option.  Have you tried removing your card temporarily and trying to boot up? This might rule out other reasons why your having problems starting your machine.

By the way I'm using nvidia-glx with a GeForce FX 5900XT and its working ok

---

### Post by ike on 2007-04-22
> **tictacman said:**
> My card is an edimax with a rt61 chip (also a pci card).  Its all fixed now, but its a bit of a long story.  You can read all my threads about it by clicking on my name and selecting the appropriate option.  Have you tried removing your card temporarily and trying to boot up? This might rule out other reasons why your having problems starting your machine.

By the way I'm using nvidia-glx with a GeForce FX 5900XT and its working ok

Ok, so I'm back in edgy again. Don't think I will try Feisty until Canonical says the Nvidia driver troubles are fixed. I managed to install nvidia driver (with envy) without too much hassle. I don't care about the desktop effects stuff right now, I just want a usable computer (other that this mac and my vista laptop). And that means I have to get my wireless card working. lspci says it's a RaLink RT2561/RT61.

Before Feisty, I tried for weeks to get the wireless card working in Edgy, but without any success at all. I was thinking there was a problem with my router, but now I have a shiny new wireless dsl modem which works just fine with OSX and Vista.

I will continue banging my head in the wall for a while, and maybe I'll start a new thread on the wireless network problem later..

---

### Post by tictacman on 2007-04-22
I'd imagine that you've already seen these threads, but if not have a look at

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

lots of info for getting the card working properly.  One post suggests that cpu lockup can arise if you use network manager to configure you network.  I've steered cleared of it, haven't had any problems.  I've not tried the wireless cad in feisty yet, as its still running on a different edgy box.  I will probably have a go next week.

Just a thought: your not using an old nvidia card are you? I think old cards are not supported by nvidia-glx.  You have to use the nvidia-glx-legacy deb.

---

### Post by ike on 2007-04-22
> **tictacman said:**
> I'd imagine that you've already seen these threads, but if not have a look at

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

lots of info for getting the card working properly.  One post suggests that cpu lockup can arise if you use network manager to configure you network.  I've steered cleared of it, haven't had any problems.  I've not tried the wireless cad in feisty yet, as its still running on a different edgy box.  I will probably have a go next week.

Just a thought: your not using an old nvidia card are you? I think old cards are not supported by nvidia-glx.  You have to use the nvidia-glx-legacy deb.

lspci says it's a "nVidia Corporation GeForce 6200 (rev a1)", and nvidia-glx has worked before and now works again in edgy, so that shouldn't be a problem.

Thanks for the links, will check them out right away!

---

### Post by frogotronic on 2007-04-22
Your video driver's problems could be a problem of conflicts between the nvidia kernels, restricted modules and nvidia-glx and nvidia-glx-new.

According to the Nvidia website your card is supported in the new 9755 driver, so you should use that.

I would first edit your xorg.conf file and chose "nv" rather than "nvidia" (can be done from command line CNTL-ALT-F1)

```
sudo pico /etc/X11/xorg.conf

sudo apt-get remove nvidia-glx nvidia-glx-new nvidia-kernel-common nvidia-kernel-source
```

At this point it will want to remove restricted drivers and other parts of LINUX, answer YES (it's perfectly safe to do so) and when its done, reboot.

After rebooting, (I'd use Synaptic), reinstall the restricted drivers appropriate for your kernel

```
uname -r
```

BUT don't install nvidia-glx or nvidia-glx-new.  Then using the Restricted Drivers Manager, the restricted drivers should  be able to intelligently download, install and configure the correct (appropriate) nvidia drivers for your card.  Before rebooting to use the nvidia driver, change the "nv" to "nvidia".

```
sudo pico /etc/X11/xorg.conf
```

I've attached my working xorg.conf file as a "example.txtf" text file - you can use it as a guide.

Let us know how it goes...I'll monitor this post

- CH

---

### Post by ike on 2007-04-22
Well, I have finally gotten my wireless card to work, thanks to the link provided by tictacman, 
[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

I'm not in an adventurous mood right now, so I think I'll wait a while with the nvidia thing.. After all, right now I have both nvidia drivers and wlan working, and I'm very happy with that for the time being :)

I will try the nvidia-glx-new stuff out someday though!

Thanks for the help!

---

### Post by frogotronic on 2007-04-22
cool...I had the same problem you described (with an older card) and the (my) above solution worked.

- CH

---

### Post by moopoo on 2007-04-22
Well, thank you cement_head!

I head the exact same problem, ike had described, on my Geforce3 Ti 200. I wanted window borders when using desktop effects and switched to glx-new. I didn't work, so i went back to glx and then... you know the rest.

I did as your guide told me, and everything worked fine again! The hours before I did not use the restricted drivers manager but synaptic to install glx.

---

