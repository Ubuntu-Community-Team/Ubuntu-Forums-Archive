---
title: "Blank screen on shutdown (it doesn't seem an ACPI problem) on Kubuntu Edgy"
date: 2006-11-17
forum: General Help
---

### Post by Ereza on 2006-11-17
Hi there!

It's my first help request post here, I hope that someone can help ;)

I've been using Kubuntu Dapper and now Edgy without major problems, but three days ago I acquired a Toshiba Satellite A110-180. Edgy works perfectly out of the box, except for one thing (well, two, but the card reader doesn't matter to me): when I go to K Menu -> Logout and choose Turn off, reboot, suspend or hibernate, the system logs out of KDE, and then hangs with a black screen (before even showing USplash). If I wait some seconds, the screen changes to white, then green, and then purple, in a similar way than the one when you push an LCD screen (I even thought it could harm my screen). Then, nothing more. No activity. It hangs, and the only way to turn it off is pushing the power button for some seconds.

Alternatively, if I choose K Menu -> Logout -> End session, and then, in KDM, choose Turn off, it works perfectly, absolutely no problems.

Also, if I run shutdown now -h or reboot, it works OK, but I don't like it since it does a more "hard" shutdown (it doesn't save some KDE settings).

Someone reported this problem in the bug tracker, but noone seems interested in it: [https://launchpad.net/distros/ubuntu/+bug/71678](https://launchpad.net/distros/ubuntu/+bug/71678)

Also, it's very annoying for me since I can't suspend or hibernate using the explained method (KDM).

Has anyone had this problem? Anyone found a solution? Need more info? I'll post it if you ask me ;)

PD: Sorry if some of the menu names are incorrect, my system is not in English, so I have tried to translate them.

EDIT: I just noticed that I can hibernate, but not suspend, poweroff or reboot.

---

### Post by Kryten107 on 2006-11-22
I have the same white/purple/green coloring problem with Gnome/Ubuntu. I'm running Beryl on an XGL server (because of the lack of AIGLX support from ATI), so I can't shut down directly from the session, I have to logout first. But, when I click logout, I get the color fading thing.

I tried the "sudo /sbin/halt -p" script from the bug comments, but it doesn't always work. Sometimes it shuts down fine, other times it instead locks up with vertical purple lines on the screen.

The latest comment on the bug report says that the latest KDE update fixed the problem, but that doesn't help me since I have the same error in Gnome :(

Edit: My error doesn't correspond with that bug report, but I did find this, which sounds like what was wrong with mine: [https://bugz.launchpad.net/distros/ubuntu/+source/usplash/+bug/72216](https://bugz.launchpad.net/distros/ubuntu/+source/usplash/+bug/72216)

Following the suggestion in the bug report, I disabled splash in my GRUB options, and everything works fine now.

---

### Post by Ereza on 2006-11-22
> **Kryten107 said:**
> Edit: My error doesn't correspond with that bug report, but I did find this, which sounds like what was wrong with mine: [https://bugz.launchpad.net/distros/ubuntu/+source/usplash/+bug/72216](https://bugz.launchpad.net/distros/ubuntu/+source/usplash/+bug/72216)

Following the suggestion in the bug report, I disabled splash in my GRUB options, and everything works fine now.
It was me who submitted that bug report, seeing that noone reported the "é" thing, which happens on my new Toshiba and also on my previous laptop, an Acer Extensa 2600, with also Intel 945GM.
As for now, I won't switch to Usplash again, since I prefer seeing what is currently happening (I also disabled the "quiet" option in the kernel) than having no info, and Usplash still has some other bugs.

---

### Post by daradib on 2006-11-23
I might have a different problem, but I'm not sure. I use Kubuntu Edgy 64-bit with fglrx driver for ATI graphics card. I use DVI for my monitor. However, I cannot hibernate, suspend, shut down, log off, end session, restart X server, or reboot. The screen becomes black and I must press the power button and hold. If I use XGL (with Beryl), I only get one option- End Session, which crashes the X server and screen becomes black.

---

### Post by witiwap on 2006-12-18
I´m having the exact same problem that daradib stated, but I´m too new to linux to know how to go about troubleshooting it.

---

### Post by ReyPeste on 2007-01-09
I am also having this problem (the blank screen freeze during shutdown or reboot, before uplash, I dont have that changing colour things) in Kubuntu Edgy on a Dell Dimension desktop.  I am using the propietary fglrx ATI driver (the open source one either doesnt start X or doesnt do DRI with Radeon X300 SE).  Sometimes it does work, but 4 out of 5 times it will freeze and there is nothing left to do except hard boot.  This is a serious problem I think. ... it was suggested in one of the related bug reports ([https://launchpad.net/ubuntu/+source/meta-kde/+bug/70069](https://launchpad.net/ubuntu/+source/meta-kde/+bug/70069)) that this may have something to do with the kernel... I am using the "generic" one, not the 386.

---

### Post by Ckytep on 2007-01-10
Darn, I really hoped to find a solution here.
I have the same problem. Running Kubuntu 6.10 with the opensource Radeon-driver.
No Beryl installed.

sudo shutdown -h now
...works.

But if I try to shutdown it all via "Log out" -> "Shutdown", my monitor (DVI-connected) switches off and that's it.
It doesn't save some of my KDE settings either.

Trying to leave the Windows-world, but there is always some darn problem. Damn! ](*,)

---

### Post by jm2003uk on 2007-01-10
I've just re-installed Kubuntu edgy and am having the same shutdown/reboot problems (screen goes to standby and computer hangs). Will try ending the session first and see if it will at least work that way but it is pretty annoying. Hope a solution comes along soon.


EDIT

Ending the session and then shutting down seems to work ok for me.

---

### Post by cwhitt on 2007-01-11
Don't know if it applies to you, but with my motherboard (Asus P5L-MX with intel chipset and onboard video) I was getting similar logout and shutdown hangs.  The cause turned out to be a bug somewhere causing the X server to not shut down properly, eventually causing a kernel panic.  For me all this was hidden by the splash screens etc so I just saw empty screens.

In my BIOS I changed Advanced->CPU Configuration->Execute Disable Function to ENABLED and that seems to work around the problem.

More info here [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697)

Cheers

---

### Post by jasin on 2007-01-12
I have the same problem, a blank black screen when I restart the computer, it hangs at that blank black screen.

Ubuntu needs to fix acpi, these forums are plagued with posts about problems with acpi.

---

### Post by magic_doc on 2007-01-17
Hallo all,

im just installing an new system with Kubuntu 6.10, the Mainboard is an Aopen 915GMm-HFS with Intel 915GM + ICH6-M Chipsets. I also faced the problem that the screen get´s dark, but the powersupply is not switched off. The suggestions in this tread doesn´t help at all. 
I learned that this behavior happens only when I was not logged in an x-session. Pressing the shutdown-button in the logging screen just after the boot always turns off the machine. I asumed a failure in the x-server or the KDE so I searched the Internet and found [this]("http://bugzilla.kernel.org/show_bug.cgi?id=7195"):

This guy had almost the same problem an described a way that solves my problem. Killing the two offending modules made the machine always to turn off.

I put this script into /etc/init.d/

```
#!/bin/sh
case "$1" in
  start)
        # No-op
        ;;
  restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
  stop|"")
        rmmod -f snd_hda_intel
        rmmod -f snd_hda_codec
        ;;
  *)
        echo "Usage: kill_lame_snd [start|stop]" >&2
        exit 3
        ;;
esac
```

Then make it executable and update the System V style init  script  links:

```
sudo chmod +x /etc/init.d/kill_lame_snd
sudo update-rc.d kill_lame_snd start 80 0 6 .
```
That´s it: now the offending modules are removed at shutdown and my system powers off.
Of course that is only a work-arround until the module is fixed :-\"

Happy ubuntu @ all!

CU Doc

---

