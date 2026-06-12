---
title: "Screen flickering Ubuntu 18.04"
date: 2018-08-01
forum: General Help
---

### Post by mickee384 on 2018-08-01
Hey, anyone experience screen flickering in Ubuntu 18.04? Mine started doing this about a month ago. Only fix is to log out or reboot. I don't think it's my video card or it would likely happen more than once a week. My pc stays on 24/7 and I use the open source driver.

---

### Post by mickee384 on 2018-09-17
This is still happening. Any ideas? Need more info from me? Please let me know...

---

### Post by mickee384 on 2018-09-28
any ideas? All are welcome!

---

### Post by davbu on 2018-09-28
> **mickee384 said:**
> Hey, anyone experience screen flickering in Ubuntu 18.04? Mine started doing this about a month ago. Only fix is to log out or reboot. I don't think it's my video card or it would likely happen more than once a week. My pc stays on 24/7 and I use the open source driver.
Hey,
Yes, I experienced this issue too, and the installation of the nvidia drivers solved my problem.

---

### Post by mickee384 on 2018-10-02
Thanks davbu. Where do I get intel drivers? here is some more info. 

```
mickee@mickeymouse:~$ sudo lshw -c video
[sudo] password for mickee: 
  *-display                 
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:34 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
```

---

### Post by mickee384 on 2018-12-23
has no one experienced this?

---

### Post by Jotomicron on 2019-01-21
I am experiencing this as well.

```

  *-display                 
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff

```

---

### Post by mickee384 on 2019-03-22
If I am to update the video drivers where would I find Intel graphics card? It still happens about every 5 days or so. I just log out and log back in, but its annoying. I am hoping to get some ideas from the Graphics experts out there. :)

---

### Post by mickee384 on 2019-03-22
you have a similar video card to me

---

### Post by ubname on 2019-03-22
Intel drivers are already with the kernel, they work out of the box.
Just a couple of ideas for your problem, did you try upgrading to kernel 4.18, it is now supported in Ubuntu 18.04;
also you could try to login using wayland, maybe it will not "flicker".

---

### Post by latenite4 on 2019-04-16
Ubuntu 18.04 desktop onAMD Ryzen 7 2700X Eight-Core Processor . 
NVIDIA GT 710.  My screen  is good for about 10 seconds then it is off for about 1 sec. over and over again.
sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: GK208B [GeForce GT 710]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:80 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:c0000-dffff

I tried 'sudo apt install nvidia-driver-390' and reboot; no help. screen still goes off about every 10-15 sec.
This system was rock solid until about a week ago; I think a recent 'sudo apt-get' brought in the problem.

---

### Post by mickee384 on 2019-04-24
Thanks for the ideas, I will give them a try

---

### Post by mickee384 on 2019-08-08
it is still happening about every five days.

---

### Post by pushbike06 on 2019-08-08
Hi, My screen sometimes pulses "on and off" during boot. The dot bar is static so I suppose boot has been suspended during this event. My solution is to power down and reboot which is successful. Why does this happen? Could be a software problem or a hardware problem, my system is old, 10 years, and has Ubuntu 18.04.2. 64 bit loaded. I have increased my RAM to 4Gb because 2Gb was being almost fully used, 1.9Gb now with 0 swap space, running Firefox and Thunderbird. As others have said elsewhere 18.04 has been written for the latest generation of hardware and there could be conflict with old hardware.
Bought a reserve PC, 4 years old i7 16Gb, in case the HD is failing. I have 3 machines running Ubuntu 18.04.2 64 bit, only one has the screen pulse problem.

Checked my display connections. Thought it may be a RootKit infection and have run rkhunter and chkrootkit several times without finding anything serious.

---

### Post by dragonfly41 on 2019-08-09
Theory: Is there a possibility that PSU is faulty?
One quick test is to swap PSU with another to see results.
Same principle of elimination applies to swapping monitors.

---

### Post by mickee384 on 2019-08-16
oh I hope not! I have an HP Touchsmart all -in -one.

---

### Post by joris_donders2 on 2019-08-16
I would suggest to check the Bios first before you start swapping PSU and mon's

---

### Post by mickee384 on 2019-09-28
Thanks for your reply joris. What would I be looking for in the BIOS?

---

### Post by mickee384 on 2020-01-14
I can find nothing in the BIOS that would cause this issue approximately every 5 days. Also since a logout on ubuntu fixes it, it seems to me to be an OS issue, or am I wrong in that? It's very consistent... I am on 18.04.3

---

### Post by mickee384 on 2020-06-03
Weird - this issue is still plaguing me. Every 5 days or so, the entire screen flickers. I just log out/in and that fixes it but it is still happening... If I am at the computer it starts flickering, if I log on - doesn't flicker until I unlock the computer - login screen does not flicker then or when I go to log out, just when logged in and running.

---

### Post by mickee384 on 2020-08-16
I will see if this continues after upgrading to ubuntu 20.04 and report back

---

### Post by mickee384 on 2020-08-23
so far so good. I think I've run more than 5 days with out the flicker. I'll double check and post my results

---

### Post by mickee384 on 2020-08-29
been 6 days with no flicker. I will wait a few more before closing this thread

---

### Post by mickee384 on 2020-09-06
ok, so this still happens. Since its been with me for the last 2 LTS versions, I am going to assume its hardware related. Still not sure why logging out/in or rebooting fixes it, but I guess this is not solvable.

---

### Post by dragonfly41 on 2020-09-06
Reading back through the posts this effect seems to kick in every 5 or 6 days.
One wild theory (10% chance) is that there could be interference on the mains power supply getting through.
Any locals doing repair works? There are power adapters which filter out such interference such as lightning strikes.
But it is a long shot.  If you had a battery only laptop you could try running battery only.
In an earlier post I suggested try swapping your PSU.

---

### Post by mickee384 on 2020-09-10
Swapping PSU would be hard as Its an HP all in one PC. Thanks for looking in and offering suggestions. There is no electrical work being done around here and I am guessing it could maybe be lack of power. I will try to plug the computer into a dedicated outlet to test. Keeping in mind that logging out/in fixes the issue until the next 5 or 6 days. It is this reason I think hardware may not be the issue. There is a different display manager between login (GDM) and Desktop (X), no? Or am I wrong - like what happens after GDM loads and logging into the desktop? I ask this because logging out fixes the problem. This issue is a conundrum. Weird for sure.

---

### Post by dragonfly41 on 2020-09-10
Puzzling indeed. Any cron jobs which might be kicking in? It is the consistent 5/6 day gap which is puzzling .. and suggests looking for time based jobs.

---

### Post by mickee384 on 2020-09-10
I can't seem to view the crontab. I tried looking in crontab -e and choosing nano, but I think this may be to deep for me. Is there a way to view the logs that cron initiates?

---

### Post by mickee384 on 2020-12-16
anyone have any idea? Do you think this is hardware related?

---

### Post by vmpx on 2020-12-17
After installation of
```
sudo apt install libdvdnav4 libdvd-pkg gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg
sudo apt install ubuntu-restricted-extras
```
I got the same problem.

---

### Post by vmpx on 2020-12-17
I did:
```
sudo apt remove gstreamer1.0-plugins-ugly
```

---

### Post by mickee384 on 2020-12-29
OK, so some new information. It appears the time between the onset of the flickering is also when the gnome-shell process is at a high use of RAM. I shall endeavour to see how much RAM use happens at the time of the incident. I found out by doing ```
Alt+F2  r
``` enter. This effectively restarts the 6 day countdown again. Prior to this I only figured out a reboot or a log out/in fixed the issue. Currently my uptime is 17 days and no issue. I will wait until it happens again then note the RAM use at that time by gnome-shell. Any ideas appreciated! I have tried stopping all extensions with no impact in Gnome-Shell RAM usage as well.

---

### Post by vmpx on 2020-12-30
I have the issue if I want to play a video from terminal after a short period of time. On Ubuntu 16.04 and 20.04 I have not this problem.

---

### Post by vmpx on 2020-12-31
I removed
```
sudo apt remove gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```

and make
```
sudo apt autoremove
```

My system looks like now
```

apt list --installed|grep gstreamer

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

gir1.2-gstreamer-1.0/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
gstreamer1.0-clutter-3.0/bionic,now 3.0.26-1 amd64  [Installiert,automatisch]
gstreamer1.0-fluendo-mp3/bionic,now 0.10.32.debian-1 amd64  [Installiert,automatisch]
gstreamer1.0-gl/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
gstreamer1.0-gtk3/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
gstreamer1.0-libav/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
gstreamer1.0-packagekit/now 1.1.9-1ubuntu2.18.04.5 amd64  [Installiert,aktualisierbar auf: 1.1.9-1ubuntu2.18.04.6]
gstreamer1.0-plugins-base/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [installiert]
gstreamer1.0-plugins-base-apps/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [installiert]
gstreamer1.0-plugins-good/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [installiert]
gstreamer1.0-pulseaudio/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [installiert]
gstreamer1.0-tools/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
gstreamer1.0-x/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
libgstreamer-gl1.0-0/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
libgstreamer-plugins-base1.0-0/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
libgstreamer-plugins-good1.0-0/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
libgstreamer1.0-0/bionic-updates,now 1.14.5-0ubuntu1~18.04.1 amd64  [Installiert,automatisch]
libreoffice-avmedia-backend-gstreamer/bionic-updates,bionic-security,now 1:6.0.7-0ubuntu0.18.04.10 amd64  [Installiert,automatisch]

```

I removed totem
```
sudo apt remove totem
```

make
```
sudo apt autoremove
```

and installed it again
```
sudo apt install totem
```

Perhaps is this the solution to remove flickering.

---

### Post by vmpx on 2021-01-01
I also removed
```
sudo apt remove libreoffice-avmedia-backend-gstreamer
```

---

### Post by vmpx on 2021-01-03
As I used the Terminal today the flickering was still there, so I removed also:
```

sudo apt remove ubuntu-restricted-extras ubuntu-restricted-addons
sudo apt remove ttf-mscorefonts-installer
sudo apt autoremove
sudo apt-get purge --auto-remove ttf-mscorefonts-installer

```

---

### Post by mickee384 on 2021-01-08
I got as far as 9 days without rebooting, logging out or restarting Gnome-Shell. Below is the day and the memory usage of Gnome-Shell. If you have any ideas as to how to reduce the amount of RAM being taken by it, that would be great.

Dec  18 789MiB
Dec 22 974MiB
Dec 24 1.05GiB

after which time My computer was basically an unresponsive and crapped out device, finally forcing a reboot. If anyone has any idea here please let me know. Has anyone else seen Gnome-Shell take over a GiB of RAM just sitting there with just Thunderbird open? Anyone know of a Gnome Shell extension that has a memory leak in it, or even if the Extensions actually increase RAM used for Gnome-Shell? How do I se what RAM the individual Extensions take? Keep in mind, this problem has plagued me prior to using the Gnome-Shell extensions... I have trierd disabling the extensions but there was no effect on Gnome-Shell RAM usage.

---

### Post by vmpx on 2021-01-10
The reason for the flickering should be the nouveau driver. One should install the original Nvidia driver.

---

### Post by mickee384 on 2021-01-10
does the nvidia driver work with Intel video cards?

---

### Post by deadflowr on 2021-01-10
> **mickee384 said:**
> does the nvidia driver work with Intel video cards?

No

---

### Post by mickee384 on 2021-05-17
LOL that was a dumb question!

---

### Post by mickee384 on 2021-06-15
The issue appears to have resolved itself...

---

### Post by vmpx on 2021-10-13
Try disable in browser "use hardware acceleration".

---

### Post by coffeecat on 2021-10-13
Back to sleep, ancient and solved thread.

---

