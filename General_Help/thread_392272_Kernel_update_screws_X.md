---
title: "Kernel update screws X"
date: 2007-03-24
forum: General Help
---

### Post by shavenlunatic on 2007-03-24
Hi,

Sorry if this is now a "known" issue, but its hard to search round a linux forum using words like "kernel" and "nvidia"without you getting every thread under the sun returned.

Basically, the kernel update from xxxxxx.10 to xxxxx.11 stopsa my X from working.

If i do a clean install of ubuntu edgy, setup nvidia drivers, everything is fine, nvidia config tool works, even the temperature monitor.. woo :)

so I decide to install compiz, which involves running "apt-get dist-update" or whatever the command is.. running that demmands a reboot, so i reboot and grub shows a new kernel version..

now X fails to load, I tried restoring my xorg.conf and re-running the driver serup, but no joy.

Can anyone help please?  I'm having to use windows to post this so its quite urgent :P

---

### Post by FuturePilot on 2007-03-24
Did you happen to use Envy to install the drivers? When you get a new kernel you have to uninstall the driver then reinstall it in order to get the Nvidia module into the kernel.

---

### Post by shavenlunatic on 2007-03-24
No, I didn't use Envy, I manually installed the drivers I downloaded from the Nvidia site.

I have tried re-installing them the way I did initially but it still won't boot.

Is there any way to avoid doing the kernel upgrade? I tried usingthe update manager, installing everything BUT the kernel upddate but it still managed to update it.. god knows how... but regardless, the next time i did an apt-get it would update it anyway.

Help?

---

### Post by jimbob on 2007-03-24
I find that each time they update the kernel I have to go into single user mode and install the corresponding restricted modules to get my nvidia stuff and my X-server back working, ie:

   apt-get install linux-restricted-modules-$(uname -r)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by shavenlunatic on 2007-03-24
i have no idea what that means :(

im fairly new to linux and still finding my feet.

Can I not just either...

a) do the kernel upgrade and THEN install the nvidia drivers?

or

b) not install the kernel upgrade at all? (will this cause any problems and how would I do it?)

---

### Post by FuturePilot on 2007-03-24
Yes, you can install the kernel update and then install the drivers. But the next kernel update that comes down will break X again. That's what I always do on a fresh install of Ubuntu. I install all of the updates before doing anything else. I use Envy though which does a nice job of integrating everything into the kernel.

---

### Post by shavenlunatic on 2007-03-24
i tried envy before and it wouldn't seem to install drivers for me correctly.... 

how often are kernel updates released? if its only 6 monthly i can live with doing a re-install of ubuntu occasionally... if its every other day then I may have to smash something up :D

---

### Post by shavenlunatic on 2007-03-24
well, yeah, everything works fine if i wipe and reinstall ubuntu, then upodate, then install drivers.. then i try to install compiz... i thought it would be good ettiquette to start a new thread on this incase it is a seperate problem.... so it's followed on here:

[http://www.ubuntuforums.org/showthread.php?p=2347316#post2347316](http://www.ubuntuforums.org/showthread.php?p=2347316#post2347316)

:mad:

---

