---
title: "Ubuntu 22.04.3 LTS Screen goes blank after wake up"
date: 2024-01-16
forum: General Help
---

### Post by 7-webmaster on 2024-01-16
Starting a few weeks ago after applying regular maintenance to 22.04.3 LTS one of my two displays, an LG 22MP47HQ-P connected to my tower by a D-Sub cable, blinked multiple times immediately after wake up.  By wake up I mean an action, such as pressing a key on the keyboard, that causes the computer to arouse out of hibernation after it has been unused for several hours.  My second display which is connected using HDMI works normally.  This, of course, was merely a mild annoyance because after a few seconds it stopped.  However in the past week that same display flashes on, and then goes black.  I power the display off and back on and again it flashes on for a fraction of a second and then goes black.  After several power cycles it stays on, so again this is only a mild annoyance.  Is this a known issue with a recent update?  I cannot find anywhere on the web where the location of the Wayland settings file is described.  For example [https://github.com/theophilusx/wayland-config](https://github.com/theophilusx/wayland-config) discusses the configuration files but does not say where they are on a Debian or Ubuntu system.  In any event that page is five years old.  Would installing Ubuntu 23.10 Mantic Minotaur be advisable, or should I wait until April?

"Yesterday, upon the stair, I met a man who wasn't there.
He wasn't there again today.  I wish, I wish he'd go away."
[I]Hughes Mearns
[/I]
lshw -C video
  *-display                 
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:31 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff

/var/log/apt/history.log

Start-Date: 2024-01-02  16:01:30
Commandline: aptdaemon role='role-commit-packages' sender=':1.7295'
Upgrade: thunderbird:amd64 (1:115.5.0+build1-0ubuntu0.22.04.1, 1:115.6.0+build2-0ubuntu0.22.04.1), thunderbird-locale-en:amd64 (1:115.5.0+build1-0ubuntu0.22.04.1, 1:115.6.0+build2-0ubuntu0.22.04.1), thunderbird-locale-en-gb:amd64 (1:115.5.0+build1-0ubuntu0.22.04.1, 1:115.6.0+build2-0ubuntu0.22.04.1), thunderbird-locale-en-us:amd64 (1:115.5.0+build1-0ubuntu0.22.04.1, 1:115.6.0+build2-0ubuntu0.22.04.1), thunderbird-gnome-support:amd64 (1:115.5.0+build1-0ubuntu0.22.04.1, 1:115.6.0+build2-0ubuntu0.22.04.1)
End-Date: 2024-01-02  16:01:33

Start-Date: 2024-01-03  16:57:04
Commandline: /usr/bin/unattended-upgrade
Upgrade: libsqlite3-dev:amd64 (3.37.2-2ubuntu0.1, 3.37.2-2ubuntu0.3), libsqlite3-0:amd64 (3.37.2-2ubuntu0.1, 3.37.2-2ubuntu0.3), sqlite3:amd64 (3.37.2-2ubuntu0.1, 3.37.2-2ubuntu0.3)
End-Date: 2024-01-03  16:57:05

Start-Date: 2024-01-03  16:57:08
Commandline: /usr/bin/unattended-upgrade
Upgrade: openssh-client:amd64 (1:8.9p1-3ubuntu0.5, 1:8.9p1-3ubuntu0.6), openssh-server:amd64 (1:8.9p1-3ubuntu0.5, 1:8.9p1-3ubuntu0.6), openssh-sftp-server:amd64 (1:8.9p1-3ubuntu0.5, 1:8.9p1-3ubuntu0.6)
End-Date: 2024-01-03  16:57:10

Start-Date: 2024-01-03  16:57:13
Commandline: /usr/bin/unattended-upgrade
Upgrade: libnode72:amd64 (12.22.9~dfsg-1ubuntu3.2, 12.22.9~dfsg-1ubuntu3.3), nodejs:amd64 (12.22.9~dfsg-1ubuntu3.2, 12.22.9~dfsg-1ubuntu3.3), libnode-dev:amd64 (12.22.9~dfsg-1ubuntu3.2, 12.22.9~dfsg-1ubuntu3.3)
End-Date: 2024-01-03  16:57:14

Start-Date: 2024-01-03  16:57:16
Commandline: /usr/bin/unattended-upgrade
Upgrade: nodejs-doc:amd64 (12.22.9~dfsg-1ubuntu3.2, 12.22.9~dfsg-1ubuntu3.3)
End-Date: 2024-01-03  16:57:17

Start-Date: 2024-01-09  20:43:19
Commandline: aptdaemon role='role-commit-packages' sender=':1.9514'
Install: php8.3-xml:amd64 (8.3.1-1+ubuntu22.04.1+deb.sury.org+1, automatic), php8.3-mbstring:amd64 (8.3.1-1+ubuntu22.04.1+deb.sury.org+1, automatic), php8.3-common:amd64 (8.3.1-1+ubuntu22.04.1+deb.sury.org+1, automatic), php8.3-intl:amd64 (8.3.1-1+ubuntu22.04.1+deb.sury.org+1, automatic)
Upgrade: php-common:amd64 (2:93+ubuntu22.04.1+deb.sury.org+3, 2:94+ubuntu22.04.1+deb.sury.org+1), software-properties-common:amd64 (0.99.22.8, 0.99.22.9), python3-software-properties:amd64 (0.99.22.8, 0.99.22.9), php-intl:amd64 (2:8.2+93+ubuntu22.04.1+deb.sury.org+3, 2:8.3+94+ubuntu22.04.1+deb.sury.org+1), php-mbstring:amd64 (2:8.2+93+ubuntu22.04.1+deb.sury.org+3, 2:8.3+94+ubuntu22.04.1+deb.sury.org+1), software-properties-gtk:amd64 (0.99.22.8, 0.99.22.9), python3-distro-info:amd64 (1.1ubuntu0.1, 1.1ubuntu0.2), distro-info-data:amd64 (0.52ubuntu0.5, 0.52ubuntu0.6), linux-firmware:amd64 (20220329.git681281e4-0ubuntu3.23, 20220329.git681281e4-0ubuntu3.24), php-xml:amd64 (2:8.2+93+ubuntu22.04.1+deb.sury.org+3, 2:8.3+94+ubuntu22.04.1+deb.sury.org+1), distro-info:amd64 (1.1ubuntu0.1, 1.1ubuntu0.2)
End-Date: 2024-01-09  20:45:50

Start-Date: 2024-01-10  21:58:10
Commandline: /usr/bin/unattended-upgrade
Upgrade: libc6:amd64 (2.35-0ubuntu3.5, 2.35-0ubuntu3.6), libc6:i386 (2.35-0ubuntu3.5, 2.35-0ubuntu3.6), libc-dev-bin:amd64 (2.35-0ubuntu3.5, 2.35-0ubuntu3.6), libc6-dbg:amd64 (2.35-0ubuntu3.5, 2.35-0ubuntu3.6), libc6-dev:amd64 (2.35-0ubuntu3.5, 2.35-0ubuntu3.6)
End-Date: 2024-01-10  21:58:28

Start-Date: 2024-01-10  21:58:35
Commandline: /usr/bin/unattended-upgrade
Upgrade: libc-bin:amd64 (2.35-0ubuntu3.5, 2.35-0ubuntu3.6)
End-Date: 2024-01-10  21:58:51

Start-Date: 2024-01-10  21:58:55
Commandline: /usr/bin/unattended-upgrade
Upgrade: locales:amd64 (2.35-0ubuntu3.5, 2.35-0ubuntu3.6)
End-Date: 2024-01-10  21:59:22

Start-Date: 2024-01-10  21:59:25
Commandline: /usr/bin/unattended-upgrade
Upgrade: libc-devtools:amd64 (2.35-0ubuntu3.5, 2.35-0ubuntu3.6)
End-Date: 2024-01-10  21:59:26

Start-Date: 2024-01-15  13:06:55
Commandline: /usr/bin/unattended-upgrade
Upgrade: libbinutils:amd64 (2.38-4ubuntu2.4, 2.38-4ubuntu2.5), binutils-x86-64-linux-gnu:amd64 (2.38-4ubuntu2.4, 2.38-4ubuntu2.5), libctf0:amd64 (2.38-4ubuntu2.4, 2.38-4ubuntu2.5), binutils-common:amd64 (2.38-4ubuntu2.4, 2.38-4ubuntu2.5), binutils:amd64 (2.38-4ubuntu2.4, 2.38-4ubuntu2.5)
End-Date: 2024-01-15  13:07:03

Start-Date: 2024-01-15  13:07:06
Commandline: /usr/bin/unattended-upgrade
Upgrade: gir1.2-javascriptcoregtk-4.0:amd64 (2.42.3-0ubuntu0.22.04.1, 2.42.4-0ubuntu0.22.04.1), gir1.2-webkit2-4.0:amd64 (2.42.3-0ubuntu0.22.04.1, 2.42.4-0ubuntu0.22.04.1), libjavascriptcoregtk-4.0-18:amd64 (2.42.3-0ubuntu0.22.04.1, 2.42.4-0ubuntu0.22.04.1), libwebkit2gtk-4.0-37:amd64 (2.42.3-0ubuntu0.22.04.1, 2.42.4-0ubuntu0.22.04.1)
End-Date: 2024-01-15  13:07:07

Start-Date: 2024-01-15  13:07:09
Commandline: /usr/bin/unattended-upgrade
Upgrade: libctf-nobfd0:amd64 (2.38-4ubuntu2.4, 2.38-4ubuntu2.5)
End-Date: 2024-01-15  13:07:10

Start-Date: 2024-01-16  15:56:12
Commandline: /usr/bin/unattended-upgrade
Upgrade: xwayland:amd64 (2:22.1.1-1ubuntu0.9, 2:22.1.1-1ubuntu0.10)
End-Date: 2024-01-16  15:56:17

Start-Date: 2024-01-16  15:56:20
Commandline: /usr/bin/unattended-upgrade
Upgrade: xserver-common:amd64 (2:21.1.4-2ubuntu1.7~22.04.5, 2:21.1.4-2ubuntu1.7~22.04.7)
End-Date: 2024-01-16  15:56:38

Start-Date: 2024-01-16  15:56:44
Commandline: /usr/bin/unattended-upgrade
Upgrade: xserver-xorg-legacy:amd64 (2:21.1.4-2ubuntu1.7~22.04.5, 2:21.1.4-2ubuntu1.7~22.04.7)
End-Date: 2024-01-16  15:56:56

Start-Date: 2024-01-16  15:56:59
Commandline: /usr/bin/unattended-upgrade
Upgrade: xserver-xephyr:amd64 (2:21.1.4-2ubuntu1.7~22.04.5, 2:21.1.4-2ubuntu1.7~22.04.7)
End-Date: 2024-01-16  15:57:07

Start-Date: 2024-01-16  15:57:10
Commandline: /usr/bin/unattended-upgrade
Upgrade: xserver-xorg-core:amd64 (2:21.1.4-2ubuntu1.7~22.04.5, 2:21.1.4-2ubuntu1.7~22.04.7)
End-Date: 2024-01-16  15:57:15

---

### Post by 7-webmaster on 2024-01-20
I have now upgraded to Ubuntu 23.10 and the problem still occurs.  I would really appreciate some suggestions of how to get this to work.

---

