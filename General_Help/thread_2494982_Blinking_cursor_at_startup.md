---
title: "Blinking cursor at startup"
date: 2024-02-03
forum: General Help
---

### Post by Joel_Schrock on 2024-02-03
Ubuntu Mate 22.04.
I installed some updates this afternoon but I did not look closely at them, since I generally don't have any trouble. I forgot to restart but I shut down, took my computer home and started up again. When I start it, it gets to the point where there is the logo with the advancing dots underneath. Then it goes to a blank screen with a blinking cursor. There it sits. How would I begin to try to recover my install?

If I power down at this point it briefly shows several error messages along the lines of:
"UBSAN: array-index-out-of-bounds in /var/lib/dkms/virtualbox/6.1.48/build/vboxdrv/SUPDrvGip.c:2191:20
index 1 is out of range for type 'SUPGIPCPU [1]'

MacBook Pro 15, 2013.

---

### Post by guiverc on 2024-02-03
Ubuntu MATE 20.04 LTS is a LTS release, meaning there are kernel stack choices.

With Ubuntu-MATE being a *flavor*, the 22.04 & 22.04.1 media installed the GA kernel stack; which doesn't change... Ubuntu-MATE 22.04.2 & later media however installed with the HWE kernel stack, where the kernel upgrades every ~six months using kernels from the later releases. 

My suspicion (*and critical here is how often you apply upgrade**s*) is you upgraded from the 6.2 kernel (from 23.04) to 6.5 kernel (from 23.10) and your issue relates to that.

You can prove this by switching to a text terminal (Ctrl+Alt+F4) & logging in, then the command

```

uname -r

```

will show a 5.15 if you're using a GA kernel stack, which means I've guessed wrong, and your issue is something different to what I'm suspecting.  If however it responds 6.5 then you're using the HWE kernel stack, and maybe that was your upgrade.

FYI:  `uname` gives  more detail beyond the numbers I'm wanting; as the first two numbers are all I'm interested in here;

I'd have expected that upgrade to hit your box almost a week ago, however depending on mirror used, and how often you apply upgrades, that maybe your issue.

To get around this issue, reboot & at GRUB enter the ADVANCED options, and select a 6.2 kernel.  If your issue is what I suspect, I'm betting your machine will boot normally & allow login.

This is what I'd try anyway... (*where to go from here is multiple options, but I won't go into them given I don't know if the kernel stack upgrade applies to your install (ie. what media you used to install your system) nor if it was a later upgrade.. You can explore apt logs to see what was upgraded; they're found in /var/log/apt/history.log*)

---

### Post by Joel_Schrock on 2024-02-03
Thank you Guiverc. 
It was exactly the 6.5 HWE kernel that did it. Once I figured out how to find the advanced options at boot I booted into 6.2, removed all 6.5, and I seem to be up and running again. This machine doesn't update very often, but I will definitely be more careful about kernel updates until a later version.

---

### Post by guiverc on 2024-02-03
The 6.2 HWE kernel was from Ubuntu 23.04, which is now EOL & thus that kernel no longer gets security fixes from Ubuntu; which is why your system upgraded to the 6.5 kernel from Ubuntu 23.10.

Using the 6.2 kernel is a *work around* but not a long term security option; given its *unsupported* and thus doesn't get security patches from Ubuntu.

There is a known dkms issue with 22.04 & the 6.5 kernel, which impacts some users with certain video cards; users of virtualbox etc...  That will be resolved in time I'm sure.

One safe option is to revert to the GA kernel stack, ie. use 5.15 was was the default for Ubuntu-MATE 22.04 & 22.04.1 installs.  For clues on understanding the kernel stack options & what is available I'll refer you to [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Search for "To downgrade from HWE/OEM to GA kernel:" for clues as to installing the GA kernel stack.. 

Please also note that the *doc* tells you to test it BEFORE removing the unwanted stack(s) (being HWE and/or OEM).. with this removal optional.  

ie. If you add the GA stack to your existing HWE, you'll have both 6.5 and 5.15 kernels available for you to run, both of which will have all security fixes installed. Yes for the next while you'll still have 6.2 listed, but that will get removed in time.  

( If you decide to keep 6.2; you can put a HOLD on it so it won't get autoremoved; but I'll still suggest using the GA or 5.15 kernel is the safer option given it is getting security fixes )

---

### Post by MAFoElffen on 2024-02-05
The suspect is if you have NVidia Graphics...

RE: [https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

Another work=aroud is going back to the non-HWE kernel as guiverc mentioned.

Where when your install updated to 6.5.0, then modules stopped building because the 6.5.0 kernel was compiled with compiler gcc-12 and 22.04.3 has gcc-11...
RE:   [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2051457](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2051457)
You might want to join that bug report as "I am affected also".

---

