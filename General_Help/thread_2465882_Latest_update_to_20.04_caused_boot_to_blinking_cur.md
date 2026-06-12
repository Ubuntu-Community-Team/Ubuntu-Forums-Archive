---
title: "Latest update to 20.04 caused boot to blinking cursor"
date: 2021-08-13
forum: General Help
---

### Post by WB0HYQ on 2021-08-13
I booted up a laptop I haven't used in a month or so. It runs Xubuntu 20.04. Booted up just fine and I did a few things on it before the Software Update dialog popped up. I didn't note anything unusual, so I let it update. Needed a restart so I did that as well.


When it rebooted, I got the whirling Xubuntu logo, followed by a subliminal flash of text whizzing up the screen, followed by a blinking cursor. Nothing else.


I brought up a TTY terminal (Alt-F4) and logged in. When I tried to update grub, It appeared to update properly, finding everything it should. Then I issued a grub-install on /dev/sda. This also appeared to work correctly. However, a reboot command brought up the same chain of events as before. Nothing had changed.


Gave up after trying a few other things I found using Google (I am very wary of those types of things) before trying a Ubuntu Live CD.


Booted up and tried to reinstall GRUB, but kept telling me it couldn't find the canonical address of /cow. Cow? Why would Ubuntu need a cow?


After an hour of frustrating attempts at setting things right, I've pretty much resigned to the fact my system is totally messed up.


Sine I've tried so many commands, I don't think I can list them all here, but I'd accept any suggestions on how to get my system back. It has a ton of stuff I need. Most of it is backed up externally, but the programs themselves will all have to be downloaded and installed again.


Bill

---

### Post by guiverc on 2021-08-13
I wonder if you're using the GA kernel or HWE kernel of Ubuntu 20.04 LTS, also how often you upgrade your system.

From terminal (you mention text terminal login, the command `uname -r` will show your kernel; which will be a 5.4 kernel if using the GA stack, but it'll show 5.11 on a fully updated system using the HWE kernel stack).  The switch from 5.8 to 5.11 occurred only days ago (*in last week anyway*) and that has created issues for some users (why the GA stack is treated as most-stable)

In grub, I'd look in *Advanced* options and see if what options you have available; if you have an older 5.8 option available; selecting it will likely boot normally.  If this is the case (ie. you're using the HWE stack), if it was my box; I'd add the GA stack onto your system and use the 5.4 kernel until the HWE issue you have with 5.11 gets resolved.

Note as I don't know what you're using; this is guess.  Your installation media may have dictated which stack you have installed, but I don't know what media you used (*20.04, 20.04.1, 20.04.2 or an upgraded from a prior release*).

Wiki pages on GA/HWE stacks
 - [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

(To add GA stack; use the first link & search for "*To downgrade from HWE/OEM to GA kernel:*" and note you don't need to do the removal step; I'd personally not do it, as you can have both stacks installed & select at boot (ie. grub) which you opt to use.  You can always opt to remove one stack some time into the future too)

---

### Post by WB0HYQ on 2021-08-13
The GRUB menu never comes up. I go from the POST routines directly to the Xubuntu circling icon and then to the blinking cursor, so I can't do anything in GRUB.

uname -r gives me: 5.11.0-25-generic

It's very late here, so I'll have to check out the stack stuff tomorrow.

One puzzling point is the error I get from the command 'SUDO GRUB-INSTALL /DEV/SDA'  (SDA is the drive where I installed Linux). The error tells me "Warning: Sector 32 is already in use by the program 'Flexnet'; avoiding it. This software may cause boot or other problems in future. Please ask its authors not to store data in the boot track. Installation finished. No error reported." Is this normal? I've never seen it before.

That's about it.

Bill

---

### Post by guiverc on 2021-08-14
If your box has only a single OS on it; `grub` may require a keystroke to appear; try ESC (*but note:  hardware the key cannot be pressed too early (during POST) nor too late (once `plymouth` has started it's too late*), so it can take a number of tries unless you boxes are older & slower in my experience.

---

### Post by WB0HYQ on 2021-08-14
Just the one OS. It used to have Windows 7 on it, but I wiped it completely off and installed Ubuntu 18.04 (which was subsequently upgraded to 20.04 a while back). I've tried a lot of different hotkeys on boot, but I'll try the ESC once more. I probably hit it too early or late as the circling Xubuntu logo always appears.

One funny thing, though. Once the spinning logo disappears, there seems to be an attempt to load a video driver (my system used the nvidia-340 drivers, according to the driver command). It sort of "pulses" with an accompanying flash of color bars exactly three times before the blinking cursor appears and I can start a TTY terminal. Is there a way to swap drivers from the command line? Maybe I can bring this back to life by replacing the NVIDIA drivers with the generic Linux drivers.

EDIT: Yes. The ESC did give me the GRUB menu. Trying an older version of the OS.

RE-EDIT: Yes! The older version of Xubuntu booted right up and into my usual desktop. Better yet, it was using the NVIDIA drivers as well. Using linux-5.8.0-59-generic. The -5.11.0- version appeared in the GRUB though. Maybe I should remove it and let the OS try to update once more. perhaps something got messed up the last time.

Bill

---

### Post by tea for one on 2021-08-14
> **WB0HYQ said:**
> RE-EDIT: Yes! The older version of Xubuntu booted right up and into my usual desktop. Better yet, it was using the NVIDIA drivers as well. Using linux-5.8.0-59-generic. The -5.11.0- version appeared in the GRUB though. Maybe I should remove it and let the OS try to update once more. perhaps something got messed up the last time.

There have been a number of forum reports about the 5.11 kernel causing boot problems.

I would not remove it yet because you will be prompted to update again and you'll end up in [COLOR="#0000FF"]Groundhog Day[/COLOR].
There will be another kernel update in the future and then you can remove the troublesome one if needs be.

Have you considered editing Grub so that it always appears when your power on?
You won't have to go through all the effort of making it appear when there is a problematic kernel.

You can also change the default in Grub to always select a specific working kernel?

---

### Post by WB0HYQ on 2021-08-14
Now that I know about the ESC key, I' think I'll just go with that. I'll also change the order so if I forget and just hit the Enter key, I won't get stuck with the bad 5.11 version again.

Thanks,

Bill

---

### Post by WB0HYQ on 2021-08-14
Hmm. I tried to remove the 5.11 version using DPKG. The command ran just fine, removed this version (as far as I could tell) then immediately redownloaded it and installed the 5.11 version once more.

How can I definitely eliminate this version?

Another oddity is that the GRUB initially shows only "Ubuntu" at the top, followed by the line about selecting options. I have to go there and specifically select 5.8 instead of 5.11. I would really like to completely eliminate 5.11 from my computer, but it doesn't want to go.

Bill

---

### Post by WB0HYQ on 2021-08-14
Found grub-customizer. Handy tool. Get my system back up and running with no intervention by me. Just removed the entry in grub for the 15.11 OS so boot never sees it. I also went back to the x-org video driver instead of the NVIDIA hoping it would let the 15.11 OS work properly. Ugh. Got a 600x900 screen that wouldn't change no matter what I did. Went back to 5.8 and x-org driver. Gonna stop messing with it since it works.

Thanks for all the help.

Bill

---

### Post by Impavidus on 2021-08-15
You can edit /etc/default/grub to make the grub menu visible automatically and set a timeout to boot the default entry. If you remove the 5.11 kernel to go back to the 5.8 kernel, you have to remove the metapackage that pulls in the new kernels too. This means you no longer get kernel updates and won't be notified when a new 5.11 kernel, which may fix the issue, is available. You could also use the standard kernel instead of the HWE kernel. That will give you kernel 5.4 on Ubuntu 20.04 and will stay at that kernel.

Maybe grub-customizer is a handy tool. It's also good at breaking grub.

---

### Post by ajgreeny on 2021-08-15
If you have hardware that is not cutting edge it might be worth installing the linux-generic package which will pull in the 5.4.0-80 kernel and keep that series updated automatically like everything else.

You could also use synaptic to remove all packages with ***hwe*** in their name which will mean you get no further upgrades of the 5.8 kernel series which you can remove as well as the 5.11 series.

The ***hwe*** packages can be very useful for very new hardware devices but are usually not needed on older hardware.

---

### Post by WB0HYQ on 2021-08-15
> **Impavidus said:**
> You can edit /etc/default/grub to make the grub menu visible automatically and set a timeout to boot the default entry. If you remove the 5.11 kernel to go back to the 5.8 kernel, you have to remove the metapackage that pulls in the new kernels too. This means you no longer get kernel updates and won't be notified when a new 5.11 kernel, which may fix the issue, is available. You could also use the standard kernel instead of the HWE kernel. That will give you kernel 5.4 on Ubuntu 20.04 and will stay at that kernel.

Maybe grub-customizer is a handy tool. It's also good at breaking grub.

I just removed 5.11 from being visible in grub. It's still there, just not one of the choices visible. I don't plan on using the customizer often, if at all. Just used it this time to change things around. I found a web page telling me how to edit the actual file and will probably use those procedure from her on in. Thanks for the info, though.

Bill

---

### Post by WB0HYQ on 2021-08-15
> **ajgreeny said:**
> If you have hardware that is not cutting edge it might be worth installing the linux-generic package which will pull in the 5.4.0-80 kernel and keep that series updated automatically like everything else.

You could also use synaptic to remove all packages with ***hwe*** in their name which will mean you get no further upgrades of the 5.8 kernel series which you can remove as well as the 5.11 series.

The ***hwe*** packages can be very useful for very new hardware devices but are usually not needed on older hardware.

The laptop in question is an Asus G72-GX, which is fairly elderly now. It's running at the moment, so I'm going to let it run and see what happens. This experience has taught me a lot about various OS's and how to deal with them. Even at 79 there's still room to learn.

Bill

---

