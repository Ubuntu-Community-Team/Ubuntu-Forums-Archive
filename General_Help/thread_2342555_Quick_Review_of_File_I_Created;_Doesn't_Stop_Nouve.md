---
title: "Quick Review of File I Created; Doesn't Stop Nouveau--mistake?"
date: 2016-11-07
forum: General Help
---

### Post by SciGuy1872 on 2016-11-07
Hi.  I am trying to stop Nouveau from auto-starting so I can manually try getting my Nvidia to work.  I have made this file:

```

/etc/modprobe.d/disable-nouveau.conf
     blacklist nouveau
     options nouveau modeset=0
```

Still, Nouveau automatically starts--I was just wondering if anyone could tell me why Nouveau still starts and how to stop it.
Thanks,
     Anthony

---

### Post by gordintoronto on 2016-11-08
If you have an Nvidia video adapter, and an Nvidia driver, you don't need to use such a file.

Perhaps you could describe your hardware? Do you have an Optimus laptop?

[http://ubuntuhandbook.org/index.php/2016/04/switch-intel-nvidia-graphics-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/04/switch-intel-nvidia-graphics-ubuntu-16-04/)

And I'm pretty sure the first line of your file has a syntax error.

---

### Post by SciGuy1872 on 2016-11-09
Hi--thanks for the reply.  This is from my phone, so please bear with me; I'm currently locked out of the GUI.  I have an Nvidia GeForce 8200 onboard-- it's an Acer Aspire x1200, dual-core at 2.3 GHz with 4 GB of memory.  
  I tried to manually install driver Nvidia 340--I think I should have gone with the 304 legacy (that's the version in Additional Drivers that used to work).  After manually installing (I got around the Nouveau being used by selecting the legacy driver in A.D. and rebooting, then pressing ctl-alt-F1 to get around the login loop and using terminal to do sudo sh Nvidia-*-340), the display never showed after reboot--no login screen, so I couldn't access TTY.  I pressed shift key after reboot to enter root terminal to purge Nvidia, which goes to a login screen now.
  I have the 4.4.0--45-generic kernel on x86 architecture.  I think the reason the legacy stopped working is that I'm running 16.04.1-- Precise was this way; I had to download the original 12.04 OS to get the Nvidia working with the original kernel.  I didn't mean to upgrade, if that's the problem; how did the upgrade happen?--I thought I installed the original 16.04 (I was shy of repeating my 12.04 mistake).  What should I do to get back into the desktop?  Like I stated, I can only access the TTY at the login screen.
Thanks again,
      Anthony

---

### Post by gordintoronto on 2016-11-09
I'm sorry, my suggestion is the nuclear option. Boot from a Live CD or USB, back up all your data to an external device, then do a fresh install.

I would also suggest Xubuntu or Ubuntu Mate, 64-bit 16.04.

Or maybe even, moving on. This was a "budget desktop" eight years ago. Where I live, I can buy an off-lease used computer for less than $150, which will run circles around your Acer.

---

### Post by SciGuy1872 on 2016-11-09
Hi-- I'm going to take your advice.  I have one question; I have a 32-bit computer-- what OS is best for my dual-core 2.3 GHz, 4 GB computer?  Lubuntu, Xubuntu, or Mate?
     Thanks,
        Anthony

---

### Post by cariboo on 2016-11-09
> **SciGuy1872 said:**
> Hi-- I'm going to take your advice.  I have one question; I have a 32-bit computer-- what OS is best for my dual-core 2.3 GHz, 4 GB computer?  Lubuntu, Xubuntu, or Mate?
     Thanks,
        Anthony

Are you sure your system is 32-bit? Most dual core systems I've seen are all 64-bit. Also why install video drivers manually, when they are available from the repositories. If you have synaptic installed, go to Settings->Repositories->Additional Drivers.

---

### Post by SciGuy1872 on 2016-11-10
Hi, Cariboo.  Thanks for asking about the processor--I now realize I have a 64- and 32-bit- capable processor.  I got this computer from Craig's List and didn't think I'd be lucky enough to wind up with a 64-bit computer.  Now on from Chromium to Chrome!
    Regarding the driver, I had an Nvidia legacy and after awhile it got stuck in a login loop (probably when I went to 16.04.1)--I got the driver from Additional Drivers; wouldn't Synaptic been the same?
     I am going to Ubuntu Mate 16.04 because the other guru recommended I switch.  Should I download the original version, or will 16.04.1 have an HWE issue like 12.04.1, where the Nvidia driver broke after the kernel upgraded?
     Thanks again,
                Anthony

---

### Post by gordintoronto on 2016-11-10
It's more a matter of personal taste than which is better for your computer. I've used each of them on low-spec computers, and I'm currently leaning toward Mate. If my memory is working, I removed one of the two panels on my netbook, which doesn't have many vertical pixels.

The best part of your computer is that you have lots of memory. You could run Ubuntu itself, but it might be a bit slow.


> **SciGuy1872 said:**
> Hi-- I'm going to take your advice.  I have one question; I have a 32-bit computer-- what OS is best for my dual-core 2.3 GHz, 4 GB computer?  Lubuntu, Xubuntu, or Mate?
     Thanks,
        Anthony

---

