---
title: "Wake on Lan is disabled when system is put into hibernation and standby(S3)."
date: 2007-07-15
forum: General Help
---

### Post by Doom5 on 2007-07-15
I currently have Wake On Lan functioning after following the WOL How to. I have Ethtool enable Wake on Lan on my Intel e1000 driver on boot up with a script. I'm able to wake on lan if I issue a halt command to the system and shut it down.

However, the problem is, whenever the system is put into standby or hibernation mode, Wake on Lan is disabled. I know this because the Wake on Lan does not function, and when I manually wake the computer with the power button, the WakeonLan setting in ethtool is set to "d", instead g or umbg.

Does anyone know how I can stop the hiberation and standby scripts from bringing down networking or disabled WOL? Anyone know where these scripts would be?

Thanks!

---

### Post by Doom5 on 2007-07-16
Anyone?

---

### Post by Doom5 on 2007-07-19
up

---

### Post by aaahoopy on 2007-09-05
> **Doom5 said:**
> I currently have Wake On Lan functioning after following the WOL How to. I have Ethtool enable Wake on Lan on my Intel e1000 driver on boot up with a script. I'm able to wake on lan if I issue a halt command to the system and shut it down.

However, the problem is, whenever the system is put into standby or hibernation mode, Wake on Lan is disabled. I know this because the Wake on Lan does not function, and when I manually wake the computer with the power button, the WakeonLan setting in ethtool is set to "d", instead g or umbg.

Does anyone know how I can stop the hiberation and standby scripts from bringing down networking or disabled WOL? Anyone know where these scripts would be?

Thanks!

Hello,

I saw your post while trying to fix this problem for myself tonight.  I dont have all the answers, but what I came up with might be of use.

1st I saw bug reports that said WOL for e1000 is broken prior to 2.6.17.  I do not know if that is correct or not, but ethtool was not returning WOL information in my 2.6.16 Xen kernel.  So check this.

Next, you may have to do one or all of the following.  I was shotgunning towards the end, so I don't know if the last is necessary:

1. setup the ethernet card to wake on magic packets (bonus - make this happen every boot), (also when I used umbg, my machine would sleep and then wake up instantly, so you might want to think about what you set):
sudo ethtool -s eth0 wol g
2. fix acpi not to unload the driver for e1000 (and messing up your hard WOL work) by adding e1000 to MODULES_WHITELIST in /etc/default/acpi-support
3. Set the machine to not (?) hard power off on hibernate by changing HIBERNATE_MODE=platform in /etc/default/acpi-support

I could not get a magic packet to wake the machine without an IP address, whereas when I was first playing with WOL and getting it to work by unplugging the power supply and letting the BIOS setup the ethernet card I think it worked.  so my wakeonlan command looked like the following (i also have static ips, dont know if that matters...)
wakeonline -i 192.168.xxx.xxx aa:bb:cc:dd:ee:ff

Good luck

---

### Post by Doom5 on 2007-12-28
> **aaahoopy said:**
> Hello,

I saw your post while trying to fix this problem for myself tonight.  I dont have all the answers, but what I came up with might be of use.

1st I saw bug reports that said WOL for e1000 is broken prior to 2.6.17.  I do not know if that is correct or not, but ethtool was not returning WOL information in my 2.6.16 Xen kernel.  So check this.

Next, you may have to do one or all of the following.  I was shotgunning towards the end, so I don't know if the last is necessary:

1. setup the ethernet card to wake on magic packets (bonus - make this happen every boot), (also when I used umbg, my machine would sleep and then wake up instantly, so you might want to think about what you set):
sudo ethtool -s eth0 wol g
2. fix acpi not to unload the driver for e1000 (and messing up your hard WOL work) by adding e1000 to MODULES_WHITELIST in /etc/default/acpi-support
3. Set the machine to not (?) hard power off on hibernate by changing HIBERNATE_MODE=platform in /etc/default/acpi-support

I could not get a magic packet to wake the machine without an IP address, whereas when I was first playing with WOL and getting it to work by unplugging the power supply and letting the BIOS setup the ethernet card I think it worked.  so my wakeonlan command looked like the following (i also have static ips, dont know if that matters...)
wakeonline -i 192.168.xxx.xxx aa:bb:cc:dd:ee:ff

Good luck

2. fix acpi not to unload the driver for e1000 (and messing up your hard WOL work) by adding e1000 to MODULES_WHITELIST in /etc/default/acpi-support
3. Set the machine to not (?) hard power off on hibernate by changing HIBERNATE_MODE=platform in /etc/default/acpi-support

Doing this made WOL finally work!!!!!! Thank you so much!

---

### Post by |V|utley on 2008-02-25
I feel that I am sooo close to getting this working as I'd like!

I'm running 7.10.   The PC supports ACPI, and network supports WOL (all worked properly under windows).  The network card (on eth0) seems to be using the 8139too driver by the way.

If I shutdown the PC, I can restart using WOL, which is great.
If I suspend the PC (to RAM, which is what I want to do), WOL doesn't work (but I can restart using the mouse button, which I can't do when shutdown).

I got the shutdown WOL to work but removing "-i" from the halt command.  I wonder if there is something similar i can do for the suspend command?  I'm using "hibernate-ram" by the way, as my suspend command.

I;ve tried forcing the setting of the interface to support WOL (ethtool -s eth0 wol g) in rc.local.  This works well when rebooting.  However, if I use suspend, then resume WOL is no longer enabled....my guess is thats where my problem is, that WOL setting is not sticking when the machine is suspended.

Any thoughts?

---

### Post by NZJon on 2008-06-02
Hi Mutley,

Did you ever get this fixed? I found something similar on my PC (running 8.04 on an AMD64/x86_64 platform). One of the Ubuntu Forum posts mentioned that, in order for some devices, include an ethernet NIC, to wake up a computer that has been suspended, the following file needs to be configured:

```
jon@black:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:06.0
XVR0	  S5	 disabled  pci:0000:00:0f.0
XVR1	  S5	 disabled  pci:0000:00:0e.0
XVR2	  S5	 disabled  pci:0000:00:0d.0
XVR3	  S5	 disabled  pci:0000:00:0c.0
XVR4	  S5	 disabled  pci:0000:00:0b.0
XVR5	  S5	 disabled  pci:0000:00:0a.0
UAR1	  S5	 disabled  pnp:00:07
PS2M	  S4	 disabled  pnp:00:09
USB0	  S4	 disabled  pci:0000:00:02.0
USB2	  S4	 disabled  pci:0000:00:02.1
AZAD	  S5	 disabled  pci:0000:00:06.1
MMAC	  S5	 disabled  pci:0000:00:08.0
MAC1	  S5	 disabled  pci:0000:00:09.0

```

To enable a device, for example a USB controller, I would do the following:

```
jon@black:~$ sudo -s
[sudo] password for jon: 
root@black:~# echo USB0 > /proc/acpi/wakeup
root@black:~# exit
exit
jon@black:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
HUB0	  S5	 disabled  pci:0000:00:06.0
XVR0	  S5	 disabled  pci:0000:00:0f.0
XVR1	  S5	 disabled  pci:0000:00:0e.0
XVR2	  S5	 disabled  pci:0000:00:0d.0
XVR3	  S5	 disabled  pci:0000:00:0c.0
XVR4	  S5	 disabled  pci:0000:00:0b.0
XVR5	  S5	 disabled  pci:0000:00:0a.0
UAR1	  S5	 disabled  pnp:00:07
PS2M	  S4	 disabled  pnp:00:09
USB0	  S4	 enabled   pci:0000:00:02.0
USB2	  S4	 disabled  pci:0000:00:02.1
AZAD	  S5	 disabled  pci:0000:00:06.1
MMAC	  S5	 disabled  pci:0000:00:08.0
MAC1	  S5	 disabled  pci:0000:00:09.0

```

(The "lspci" command might help you map the "system nodes" mentioned in the /proc/acpi/wakeup file to actual devices on your PC.)

Now, once I suspend the machine (I use pm-suspend, as that works for me...), I can wiggle the mouse, and the computer pops back into life. I can also "enable" my NIC, which then allows me to use a WOL packet to wake the machine up again.

(I do have one prblem though--it seems as though waking the machine up from a suspend only works once... I'm trying to figure out hohw to fix that...)

Hope that helps,

   Jon

---

### Post by |V|utley on 2008-06-02
Hi NZJon,

Unfortunately, I never got this to work, everything I did wasn't quite right.  Sometimes it would work, but not consistently.

I finally settled on having WOL working when the machine is shutdown rather than sleeping or hibernating.  This is a pain as it takes a minute for the Ubuntu to start up, but I can live with it.

I had the same problem as you mention - could only get WOL to work once.  I think thats to do the ethernet IF being unloaded when suspending.

I'll have a look at what you've got here, and see if that works - if it does, you're a hero!

Thanks,
Mut.

---

