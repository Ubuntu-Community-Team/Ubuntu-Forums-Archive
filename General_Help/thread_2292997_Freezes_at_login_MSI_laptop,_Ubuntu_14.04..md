---
title: "Freezes at login: MSI laptop, Ubuntu 14.04."
date: 2015-09-01
forum: General Help
---

### Post by max-jasper-smiley on 2015-09-01
Hey guys. My first post here, so if I'm doing anything wrong please don't hesitate to let me know. This seemed like the logical subforum for this thread.

I've recently installed Ubuntu 14.04(64 bit) on my MSI G-series MS-1771 laptop.

My current issue is that when I boot, everything works fine until I actually log into an account - and then I get a total freeze. No mouse movement, no response from keyboard commands, nothing. 

I did a quick bit of googling and stumbled upon [this guide]("http://jiakaizhang.com/fix-frozen-after-login-in-ubuntu-14-04/") which was very helpful since I didn't know the alt-ctrl-f2 keyboard shortcut. 

However, when I try to follow the guide's instructions I get a recurring (about every 30 seconds or so) block of text from the system. I'll do my best to transcribe it here:

-------------------------------------------------------------------------------------------------------------------------------------------------------

Computer login: sound hdaudioC1D0: hda-codec: out of range cmd
[48.79] noveau E[DRM] failed to idle channel 0xcccc0001 [DRM]
[72.23] NMI watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [kworker/7:1:259]
[100.25] NMI watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [kworker/7:1:259]
[108.84] INFO: rcu_sched self-detected stall on CPU {7} (t = 15000 jiffies g=649 c=648 q=0)
[136.28] NMI watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [kworker/7:1:259]
         that same message a few times over the next minute
[240.38] INFO: task kworker/u16:3:124 blocked for more than 120 seconds.
[240.38]         Tainted: G                L 3.19.0-26-generic #28~14.04.1-Ubuntu
[240.38] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
          etc, etc.

-------------------------------------------------------------------------------------------------------------------------------------------------------

It's interesting to note that the first time I tried to alt-ctrl-f2 to troubleshoot, the message was MUCH longer and also different in a few ways, notably it was CPU 1 stuck rather than 7. 

If any of you feel like it would be helpful, I'll keep rebooting and transcribing any logs I get that are different. 

Hopefully you guys can help me out here, I'm really over my head and at a loss for what to do. 

Also, I've tried everything I can possibly think of related to the installation - checked installer flash drive for errors, downloaded different ISOs from different mirrors, different versions of Ubuntu. I'm fairly sure the issue lies with the laptop and not the installation. 

[Here's a link]("http://www.msi.com/product/nb/GS70-STEALTH.html#hero-overview") to MSI's page with system specs, etc.

Thanks in advance, friends.

---

### Post by QDR06VV9 on 2015-09-01
[COLOR=#000000]Hi max-jasper-smiley Welcome!
Looks like you have a [/COLOR][COLOR=#D00000][FONT=DINCondMediumRegular]GeForce GTX 765M graphic card with GDDR discrete [/FONT][/COLOR][COLOR=#000000]
[/COLOR]You can try downloading driver from xorg edgers ppa([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)).


Add the ppa


```
sudo add-apt-repository ppa:xorg-edgers/ppa
```


upgrade your system


```
sudo apt-get update && sudo apt-get upgrade
```

Install the driver


```
sudo apt-get install nvidia-352
```

Then a reboot should have you able to login.
Regards

---

### Post by max-jasper-smiley on 2015-09-01
Sorry for my ignorance. How do I execute these commands when I freeze every time I login? I try ctrl-alt-f1 at the login screen but it still forces me to log in via command line interface. Is there a way to boot to simply a command line with super-user access before logging in on my own account?

---

### Post by QDR06VV9 on 2015-09-01
No need to be sorry sometimes  I am an Assume-ing old fart.
Are you dual booting?
There are options in grub like Recovery> Then drop to root shell with network enabled.
How to here [http://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell](http://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell)

---

### Post by max-jasper-smiley on 2015-09-01
Problems beget problems.

When I try to enable networking in recovery, I get this: 

ModemManager[2080]: <warn> Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0': not supported by any plugin

ModemManager[2080]: <warn> Couldn't find support for device at  '/sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0': not supported by  any plugin

this is with a wired network.

---

### Post by QDR06VV9 on 2015-09-01
How very odd?
One more trick to try go ahead and try to login normally again when it fails use this keyboard combo Ctrl+Alt+F1
You may have to to re-login again then type root and then your password and try the above post again.

---

### Post by efflandt on 2015-09-01
Strange, I have an MSI GE60-2OE (with Win7 using BIOS & msdos partitions) with same cpu and gpu's as yours (I think based on a quick web search) and had no trouble installing 64-bit 14.04.1 back in January to a Crucial 512 GB mSATA SSD (sdb). i7-4700MQ, HD 4600, or GTX 765M are not exactly new hardware (I bought mine Oct 2013). I installed **synaptic** with Software Center and used synaptic to install **nvidia-331-updates** which has always worked fine on my laptop (you should not really need xorg-edgers for it).

I read a post somewhere that said someone could not get their hybrid Intel/Nvidia graphics laptop to work properly unless they did NOT use nomodeset kernel boot parameter during install. So I did not use nomodeset for my laptop, but did use it on my desktop where nomodeset is typically required for nvidia.

I did have a strange issue earlier when I installed 13.10 to sda4 and put grub there so I could leave the mbr untouched. If I tried to clear the boot flag on sda2 and set it on sda4, during reboot something kept resetting the boot flag on sda2, and with both sda2 and sda4 set as boot, it booted sda2 to Win7. I thought maybe it was something odd in MSI's mbr, so I backed up the mbr and replaced it with mbr.bin from syslinux, but there was no difference, so I restored the original mbr. I then put SuperGrub on a USB memory stick and after booting Ubuntu installed its grub to the USB stick. So in a way that was sort of a security feature because few people would even know that Linux was on the drive and could not boot it unless they had the USB memory stick with grub as a key.

Note that if you boot recovery mode, enable networking (which also mounts your read-only drive read-write) and get any errors about unidentified hardware, just wait long enough and it should eventually return to the menu, so you can go to the root console.

PS: For some reason I did have trouble running the live/install iso for 64-bit Ubuntu-MATE 14.04.2 on my laptop, it tends to lock up even though I have had no issues with regular 64-bit Ubuntu 14.04.

But Ubuntu-MATE live/install must do something different with graphics than regular Ubuntu, because Ubuntu 14.04 live/install worked fine with the new Maxwell chip in the GTX 750 Ti on my desktop (maybe using vesa framebuffer mode) even though nouveau or nvidia-current did not work with it (nvidia-331-updates worked once that was installed). But graphics (maybe using incompatible nouveau instead of framebuffer) was all messed up trying to boot Ubuntu-MATE 14.04 with the GTX 750 Ti to the point that I could not do anything in it.

---

