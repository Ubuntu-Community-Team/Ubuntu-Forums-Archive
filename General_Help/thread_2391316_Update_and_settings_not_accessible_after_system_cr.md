---
title: "Update and settings not accessible after system crash"
date: 2018-05-08
forum: General Help
---

### Post by walrus8303 on 2018-05-08
Hi all,

After an abrupt system shutdown, I have been experiencing some of the following issues:

When I boot, everything works fine but after a while tehre are long delays or failures to launch the settings, update the system or shut down:

Using the GUI to update, it gets stuck on waiting on authentication. I cancel it but after a long time (say 2 hours) I get the authentication dialogue. Another time I got the message "connection to daemon lost". Using the console works fine though.
I also have the same issues when I launch the settings but in their case they never launch.
Finally pressing the shut down button does not have any effect and in order to shut down the machine I use the console.

I first observed these in 16.04 LTS. Now I have upgraded to 18.04 LTS but I had not luck resolving any of these. 

I suspect that something is corrupted. Any idea  on where to look?

Thanks!

---

### Post by cruzer001 on 2018-05-08
Hello

So your not getting any error reports?  Look through your /var/logs/ and see if you can find anything useful.  Those log reports are long, just look at the last 20 or so lines.

You can skim through this wiki on log info, get some ideas.
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Also what are your system specs?  Post the post the output of:
```
inxi -b
```
This is a problem you brought with you from 16.04, maybe a fresh install is the better way to go.

---

### Post by rsteinmetz70112 on 2018-05-08
Start at the beginning. From the console not a terminal window:
```
#sudo dpkg --configure -a
#sudo apt-get install -f
#sudo upgrade
#sudo update
```

---

### Post by walrus8303 on 2018-05-08
Thank you guys for the replies,

The /var/logs/ does not exist on my machine, here is the output of inxi:

```
System:    Host: walrus-linux Kernel: 4.15.0-20-generic x86_64 bits: 64
           Desktop: Gnome 3.28.1 Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop System: Hewlett-Packard product: HP Elite 7500 Series MT v: 1.00 serial: N/A
           Mobo: PEGATRON model: 2AD5 v: 1.03 serial: N/A
           BIOS: AMI v: 8.21 date: 10/20/2014
CPU:       Quad core Intel Core i7-3770 (-MT-MCP-) speed/max: 1614/3900 MHz
Graphics:  Card: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1200@59.95hz, 1920x1200@59.95hz
           OpenGL: renderer: Mesa DRI Intel Ivybridge Desktop
           version: 4.2 Mesa 18.0.0-rc5
Network:   Card-1: Ralink RT5390 Wireless 802.11n 1T/1R PCIe
           driver: rt2800pci
           Card-2: Qualcomm Atheros AR8161 Gigabit Ethernet driver: alx
Drives:    HDD Total Size: 2000.4GB (5.0% used)
Info:      Processes: 400 Uptime: 4 days Memory: 7311.0/15909.6MB
           Client: Shell (bash) inxi: 2.3.56 



```
[COLOR=#000000]
rsteinmetz70112
what does the -f option do? This is my work PC I can't afford to mess it up for long. [/COLOR]

---

### Post by cruzer001 on 2018-05-08
I see your running "modesetting".  I wonder if this is a possible problem.  Have you found your box will not run without it?

Could be the version upgrade to 18.04 has removed old logs, after you have rebooted a couple three times try this:
```
tail -75 /var/log/kern.log > kernel_log
```
You should now have a file in your home directory called kernel_log, take a look at it for any errors.

Also do the same for xorg log.
```
tail -75 /var/log/Xorg.0.log > xorg_log
```

########

```
sudo dpkg --configure -a
sudo apt-get install -f
```
Will attempt to repair broken packages and safe to run.

```
sudo upgrade
sudo update
```
Are incorrect commands in the wrong order.  Should read:
```
sudo apt update
sudo apt upgrade
```
And do the same thing your update manager does.

This is a handy reference
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by rsteinmetz70112 on 2018-05-08
> **walrus8303 said:**
> 
what does the -f option do? This is my work PC I can't afford to mess it up for long.

From the man page:
> 
-f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dpkg --remove to eliminate some of the offending packages).
           Use of this option together with -m may produce an error in some
           situations. Configuration Item: APT::Get::Fix-Broken.

Sorry about mistyping the commands for apt-get update and apt-get upgrade At least what I did type wouldn't do anything except confuse you.

---

### Post by walrus8303 on 2018-05-15
Hi all,

Thanks for the help. I followed some of your advice, mostly resetting settings on the machine to no avail. The machine got demonised after a couple of days with some wild behaviour so I resorted to a fresh install.

---

