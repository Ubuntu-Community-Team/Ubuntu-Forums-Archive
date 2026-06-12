---
title: "Ubuntu 16.04 LTS - Black Terminal, Black Borders - Intel onboard graphic card"
date: 2017-01-15
forum: General Help
---

### Post by na3um on 2017-01-15
For whatever reason I recently added this repository in order to update graphics driver: 
```
ppa:oibaf/graphics-drivers
```

After updating and rebooting all signs show that a false graphics  driver is now installed: Completely black terminal and drop-down-menus  everywhere, black borders arround every window, etc.
  Luckily "XTerm" still shows, so I can punch in commands. I want now to just go back to the **default graphics driver**  which was installed beforehand. Seems easy enough, but I am not able to  do so. Or I'm missing the point of the problem, I don't know.
  Purging the repository via
```
ppa-purge ppa:oibaf/graphics-drivers
```

as described in the readme of this ppa didn't change a thing. I also tried the "Intel Graphics Update Tool for Linux", but running it  just gave me a fully black window once again, so I couldn't tell if it  did something or not. 
  I've browsed a lot of already asked questions but most refer to older  ubuntu versions or refer to different problems (e.g. nvidia bugs). And  I'm now hesitant to try anything without being sure this is right for my  system, as I'm afraid to break it even more. 
  Does anyone have an idea how to fix this without reinstalling Ubuntu in its entirety? Maybe it's just a Unity-tweak I'm missing?
  Maybe this will help: running
```
lspci -vnn | grep -i VGA -A 12
```

prints out
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Process or Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
Subsystem: Lenovo 4th Gen Core Processor Integrated Graphics Controller [17aa:501e]
Flags: bus master, fast devsel, latency 0, IRQ 28
Memory at f0000000 (64-bit, non-prefechtable) [size=4M]
Memory at e0000000 (64-bit, prefetchable) [size=256M]
I/O ports at 5000 [size=64]
Espansion ROM at <unassigned> [disabled]
Capabilities: <acces denied>
Kernel driver in use: i915
Kernel modules: i915

00:03.0 Audio device [...]
```

And
```
lshw -c video
```

prints out
```
*-display
desciption: VGA compatible controller
product: 4th Gen Core Prosessor Integrated Grphics Controller
vendor: Intel Corporation
physical id:2
bus info: pci@0000:00:02.0
version: 06
width: 64 bits
clock: 33Mhz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:28 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000/size=64)
```

Thank you for your help!

---

### Post by speartip on 2017-01-15
Silly question, but have you installed the ppa-purge package?
Also you need to run:
```
[COLOR=#ff0000]sudo[/COLOR] ppa-purge ppa:oibaf/graphics-drivers
```
to reverse the process.

---

### Post by na3um on 2017-01-15
Thanks for your answer. Yes, of course, I did exactly that. And "apt-get update" and reboot. Don't know what it printed out then, but when I do it now it prints: (sorry for the large picture; couldn't crop, because Gimp's drop down menus are black and unreadable due to my problem...)


[IMG]http://yuyay-records.de/misc/Screenshot%20from%202017-01-15%2017-05-40.png[/IMG]

---

### Post by speartip on 2017-01-16
It appears from that output, that your sources list is screwed up.
We need to have a look at that. Post the output of:
```
cat /etc/apt/sources.list
```
Please post everything in the code tags, it makes it easier to read, rather than Gimp photo's.
Also what is the content of your /etc/apt/sources.list.d folder? The picture you sent indicates you may have duplicates or problems there.
You may have to add that as a screenshot attachment.

---

### Post by na3um on 2017-01-16
[yeah, sry for the screenshot, didn't want to type out everything again and wasn't able to copy from XTerm before, due to missing Right-Click-menu; or so I thought - now I know how to copy ;-) ]

Ok, "cat /etc/apt/sources.list" prints out
```
jay@Leno:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xeal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial universe
deb http://de.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://de.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ xenial-backports main restricted univse multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ xenial-backports main restricteuniverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb http://mp3splt.sourceforge.net/repository trusty main
# deb-src http://mp3splt.sourceforge.net/repository trusty main

```

And the folder "/etc/apt/sources.list.d" contains the files
```
/etc/apt/sources.list.d/leolik-ubuntu-leolik-xenial.list
/etc/apt/sources.list.d/leolik-ubuntu-leolik-xenial.list.save
/etc/apt/sources.list.d/moka-ubuntu-daily-xenial.list
/etc/apt/sources.list.d/moka-ubuntu-daily-xenial.list.save
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list.save
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-xenial.list
/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-xenial.list.save
/etc/apt/sources.list.d/opera-stable.list
/etc/apt/sources.list.d/opera-stable.list.save
/etc/apt/sources.list.d/steam.list
/etc/apt/sources.list.d/steam.list.save
/etc/apt/sources.list.d/tiheum-ubuntu-equinox-xenial.list
/etc/apt/sources.list.d/tiheum-ubuntu-equinox-xenial.list.save
/etc/apt/sources.list.d/tualatrix-ubuntu-ppa-xenial.list
/etc/apt/sources.list.d/tualatrix-ubuntu-ppa-xenial.list.save
/etc/apt/sources.list.d/vertex-theme.list
/etc/apt/sources.list.d/vertex-theme.list.save
```
My experience is definitely too limited for this; don't know what to look for here.

---

### Post by speartip on 2017-01-16
OK. You have a lot of 3rd party ppas added there, and judging by your original post, Steam appears to be the problem.
My advise would be to use Synaptic. Install it if you haven't got it. Open it. Go to Settings/Repositories/Other Software, & untick all the ppas you have added, except the oibaf graphics driver one.
Then run:
```
sudo apt-get update
``` in a terminal, & see if it throws out any warnings or errors. If so post them here, if not then try ```
sudo ppa-purge ppa:oibaf/graphics-drivers
```
again, & see if that works.

---

### Post by na3um on 2017-01-16
Thanks a lot mate! This did the trick. Purging the oibaf/graphics-drivers "downgraded" 28 mesa-related thingies and after a reboot everything is back to normal.

So the lesson to be learned here is to keep 3rd party ppas to a minimum, right? 
I guess now I need to have a look at what ppas I had there in the first place and see if they were relevant, and decide whether to remove some or carefully activate others if I feel that's necessary. 

Thanks again.

---

### Post by speartip on 2017-01-16
You could re-tick the ppas one by one in synaptic & click the reload button, to see which one is causing the problem.
You are correct though, best keep 3rd party repos to a minimum, & as needed.

---

