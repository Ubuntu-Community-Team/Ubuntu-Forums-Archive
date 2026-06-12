---
title: "GLib-CRITICAL restart the user"
date: 2019-04-30
forum: General Help
---

### Post by stevenvo780 on 2019-04-30
ubuntu returns this error and I do not find any post about it, I only find related to synaptic and I do not have it installed and if I install it it keeps happening

GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed

in journalctl

It took 2 weeks without being able to solve it please help me :( :( :(

---

### Post by dino99 on 2019-05-01
Relative discussion and solution:
[https://bugzilla.redhat.com/show_bug.cgi?id=1665521](https://bugzilla.redhat.com/show_bug.cgi?id=1665521)

Cant says much as you have not detailed your config; but as the link above says, its harmless.

---

### Post by stevenvo780 on 2019-05-02
[COLOR=#212121][FONT=arial]I closed the user session and it makes me lose all the work, it is not so harmless[/FONT][/COLOR]

---

### Post by stevenvo780 on 2019-05-02
the post has not helped me much since I do not see much relation to the problem that I have or the mentioned files I do not have them

---

### Post by #&amp;thj^% on 2019-05-02
By chance is there an Nvidia Driver installed?

---

### Post by Rubi1200 on 2019-05-02
To help us help you more please do the following:

In a terminal, CTRL+ALT+T

```
sudo apt-get install inxi
```

Once installed, run this and post the output here

```
inxi -FGr
```

---

### Post by stevenvo780 on 2019-05-03
[ATTACH=CONFIG]283161[/ATTACH]

---

### Post by Rubi1200 on 2019-05-03
Hi,

it would be easier for us if you can copy the output and post it here in code tags (Go Advanced >> look for # and paste contents between).

Thanks.

---

### Post by stevenvo780 on 2019-05-03
```
System:    Host: Debian Kernel: 4.18.0-18-generic x86_64 bits: 64 Desktop: Gnome 3.28.3           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: HP product: HP Pavilion Laptop 15-cw0xxx serial: N/A
           Mobo: HP model: 84E7 v: 99.20 serial: N/A UEFI: AMI v: F.24 date: 02/19/2019
Battery    BAT0: charge: 2.2 Wh 5.7% condition: 38.4/38.4 Wh (100%)
CPU:       Quad core AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx (-MT-MCP-) cache: 2048 KB
           clock speeds: max: 2000 MHz 1: 1438 MHz 2: 1409 MHz 3: 2307 MHz 4: 2358 MHz 5: 1503 MHz
           6: 1533 MHz 7: 1524 MHz 8: 1477 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
           Display Server: wayland (X.Org 1.19.6 ) driver: amdgpu
           Resolution: 1920x1080@59.96hz, 1366x768@59.62hz
           OpenGL: renderer: AMD Radeon Graphics version: 4.6.13529
Audio:     Card-1 Advanced Micro Devices [AMD] Device 15e3 driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Device 15de driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.18.0-18-generic
Network:   Card-1: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter driver: rtl8821ce
           IF: wlo1 state: up mac: 
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller driver: r8169
           IF: eno1 state: up speed: 100 Mbps duplex: full mac:
Drives:    HDD Total Size: 1128.2GB (47.1% used)
           ID-1: /dev/sda model: WDC_WD10SPZX size: 1000.2GB
           ID-2: /dev/sdb model: SAMSUNG_MZNLN128 size: 128.0GB
Partition: ID-1: / size: 106G used: 42G (42%) fs: ext4 dev: /dev/sdb2
           ID-2: swap-1 size: 11.99GB used: 0.00GB (0%) fs: swap dev: /dev/sdb3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 67.0C mobo: N/A gpu: 67.0
           Fan Speeds (in rpm): cpu: N/A
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://co.archive.ubuntu.com/ubuntu/ bionic main restricted
           deb http://co.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
           deb http://co.archive.ubuntu.com/ubuntu/ bionic universe
           deb http://co.archive.ubuntu.com/ubuntu/ bionic-updates universe
           deb http://co.archive.ubuntu.com/ubuntu/ bionic multiverse
           deb http://co.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
           deb http://co.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
           deb http://security.ubuntu.com/ubuntu bionic-security main restricted
           deb http://security.ubuntu.com/ubuntu bionic-security universe
           deb http://security.ubuntu.com/ubuntu bionic-security multiverse
           Active apt sources in file: /etc/apt/sources.list.d/amdgpu-pro-local.list
           deb [ trusted=yes ] file:/var/opt/amdgpu-pro-local/ ./
           Active apt sources in file: /etc/apt/sources.list.d/google-chrome.list
           deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
           Active apt sources in file: /etc/apt/sources.list.d/google-earth-pro.list
           deb http://dl.google.com/linux/earth/deb/ stable main
           Active apt sources in file: /etc/apt/sources.list.d/nodesource.list
           deb https://deb.nodesource.com/node_11.x bionic main
           deb-src https://deb.nodesource.com/node_11.x bionic main
           Active apt sources in file: /etc/apt/sources.list.d/playonlinux.list
           deb http://deb.playonlinux.com/ cosmic main
           Active apt sources in file: /etc/apt/sources.list.d/skype-stable.list
           deb [arch=amd64] https://repo.skype.com/deb stable main
           Active apt sources in file: /etc/apt/sources.list.d/teamviewer.list
           deb http://linux.teamviewer.com/deb stable main
           Active apt sources in file: /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-bionic.list
           deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu bionic main
Info:      Processes: 393 Uptime: 5 min Memory: 4056.0/15030.1MB Client: Shell (bash) inxi: 2.3.56 
```

---

### Post by Rubi1200 on 2019-05-03
When does this error appear? What I mean is what are/were you doing that it was generated? Installing software, updating/upgrading...?

Open a terminal and run this command:

```
sudo apt-get update
```

Post back errors, including the one we are discussing, here using code tags please.

Also, check in the terminal and post the results of

```
journalctl | grep GLib-CRITICAL
```

---

### Post by stevenvo780 on 2019-05-07
the error is generated from nothing, only appears and closes the session, tends to happen more when I close the lid of the PC and open it, also when I disconnect a screen and the charger shortly after separation

I have not installed any NVIDIA driver, but I have not seen how I 


have one
```
may 03 21:13:52 Debian gnome-session-binary[2167]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failedmay 03 21:14:12 Debian gnome-session[3019]: gnome-session-binary[3019]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 03 21:14:12 Debian gnome-session-binary[3019]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 03 21:18:04 Debian gnome-session[4523]: gnome-session-binary[4523]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 03 21:18:04 Debian gnome-session-binary[4523]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 04 09:53:58 Debian gnome-session[2451]: gnome-session-binary[2451]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 04 09:53:58 Debian gnome-session-binary[2451]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 04 09:54:34 Debian gnome-session[3490]: gnome-session-binary[3490]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 04 09:54:34 Debian gnome-session-binary[3490]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 04 10:02:01 Debian gnome-session[6293]: gnome-session-binary[6293]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 04 10:02:01 Debian gnome-session-binary[6293]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 04 10:03:23 Debian gnome-session[2321]: gnome-session-binary[2321]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 04 10:03:23 Debian gnome-session-binary[2321]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 05 11:07:50 Debian gnome-session[4546]: gnome-session-binary[4546]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 05 11:07:50 Debian gnome-session-binary[4546]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 05 11:11:05 Debian gnome-session[2264]: gnome-session-binary[2264]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 05 11:11:05 Debian gnome-session-binary[2264]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 05 14:54:42 Debian gnome-session[2274]: gnome-session-binary[2274]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 05 14:54:42 Debian gnome-session-binary[2274]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 10:30:52 Debian gnome-session[2300]: gnome-session-binary[2300]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 10:30:52 Debian gnome-session-binary[2300]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 10:52:27 Debian gnome-session[2297]: gnome-session-binary[2297]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 10:52:27 Debian gnome-session-binary[2297]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 12:32:49 Debian gnome-session[25507]: gnome-session-binary[25507]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 12:32:49 Debian gnome-session-binary[25507]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 12:35:01 Debian gnome-session[2472]: gnome-session-binary[2472]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 12:35:01 Debian gnome-session-binary[2472]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 12:35:55 Debian gnome-session[2284]: gnome-session-binary[2284]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 12:35:55 Debian gnome-session-binary[2284]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 20:31:11 Debian gnome-session[13818]: gnome-session-binary[13818]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 20:31:11 Debian gnome-session-binary[13818]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 20:33:15 Debian gnome-session-binary[2302]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 06 20:33:15 Debian gnome-session[2302]: gnome-session-binary[2302]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:12:38 Debian gnome-session[2274]: gnome-session-binary[2274]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:12:38 Debian gnome-session-binary[2274]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:22:47 Debian gnome-session[2489]: gnome-session-binary[2489]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:22:47 Debian gnome-session-binary[2489]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:29:47 Debian gnome-session[2320]: gnome-session-binary[2320]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:29:47 Debian gnome-session-binary[2320]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:31:55 Debian gnome-session[2325]: gnome-session-binary[2325]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:31:55 Debian gnome-session-binary[2325]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:37:06 Debian gnome-session[2312]: gnome-session-binary[2312]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 00:37:06 Debian gnome-session-binary[2312]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 09:02:47 Debian gnome-session[5832]: gnome-session-binary[5832]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed
may 07 09:02:47 Debian gnome-session-binary[5832]: GLib-CRITICAL: g_child_watch_add_full: assertion 'pid > 0' failed



```

---

### Post by #&amp;thj^% on 2019-05-07
What dose this show then:
```
sudo locate org.freedesktop.problems.applet.desktop
```

---

