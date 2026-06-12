---
title: "YouTube crash two days in a row on full screen"
date: 2020-05-01
forum: General Help
---

### Post by iamtheeggman2 on 2020-05-01
Hi,

I upgraded to ubuntu 20.04 last Friday. Things seemed to be working great, however...

Two days in a row YouTube has crashed while on full screen. The video freezes in frame however you can still hear sound for quite some time. I cannot close firefox or exist the freeze framed full screen, the computer is unresponsive for normal function, however, I can use ctrl alt F1 to get to the terminal and can reboot from there however when i type reboot, funnily enough it goes back to showing graphics for the green MATE desktop symbol indication graphics ae working fine. Any ideas?

---

### Post by lvm on 2020-05-01
Is there anything helpful in syslog? Have you tried killing firefox rather than rebooting?  What video drivers are you using?

---

### Post by iamtheeggman2 on 2020-05-02
BTW I had installed MATE desktop . Nothing in /var/crash/ 

System log shows this, the computer crashed at 19:30:

```
 1 May 19:29:13 (sd-pam): pam_unix(systemd-user:session): session closed for user home
 1 May 19:29:13 systemd: Reached target Exit the Session.
 1 May 19:29:13 tracker-miner-f: OK
 1 May 19:29:12 systemd: Stopped Sound Service.
 1 May 19:29:12 tracker-miner-f: Error while sending AddMatch() message: The connection is closed
 1 May 19:29:12 systemd: Stopping Virtual filesystem service - disk device monitor...
 1 May 19:29:12 tracker-miner-f: Error while sending AddMatch() message: The connection is closed
 1 May 19:29:12 systemd: Stopping Virtual filesystem service - Media Transfer Protocol monitor...
 1 May 19:29:12 tracker-miner-f: Received signal:15->'Terminated'
 1 May 19:29:12 systemd: Stopping D-Bus User Message Bus...
 1 May 19:29:12 gvfsd: A connection to the bus can't be made
 1 May 19:29:12 systemd: Stopping Accessibility services bus...
 1 May 19:29:12 pulseaudio: GetManagedObjects() failed: org.freedesktop.systemd1.ShuttingDown: Refusing activation, D-Bus is shutting down.
 1 May 19:29:12 systemd: Started Sound Service.
 1 May 19:29:12 pulseaudio: Stale PID file, overwriting.
 1 May 19:29:12 systemd: Starting Sound Service...
 1 May 19:29:12 dbus-daemon: [session uid=1000 pid=1513] Activating via systemd: service name='org.freedesktop.impl.portal.desktop.gtk' unit='xdg-desktop-portal-gtk.service' requested by ':1.45' (uid=1000 pid=1737 comm="/usr/libexec/xdg-desktop-portal " label="unconfined")
 1 May 19:29:12 pulseaudio: X connection to :0 broken (explicit kill or server shutdown).
 1 May 19:29:11 xdg-desktop-por: xdg-desktop-portal-gtk: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

 1 May 19:17:01 cron: pam_unix(cron:session): session closed for user root
 1 May 18:27:47 mate-system-mon: SELinux was found but is not enabled.
```



Drivers are:

```
home@home-System-Product-Name:~$ sudo lshw -c video
[sudo] password for home: 
  *-display                 
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:36 memory:d0000000-dfffffff memory:feaf0000-feafffff ioport:d000(size=256) memory:c0000-dffff

```


Turns out this person has the same symptoms.
[https://forums.linuxmint.com/viewtopic.php?t=297985](https://forums.linuxmint.com/viewtopic.php?t=297985)

He writes the solution as:

"Known issue with xorg, fixed by installing HWE packages for Linux Mint 19.2

h t t p s ://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1839174"


However I searched for this in the ubuntu software but can't find one. Someone said to me recently something about turning off video hardware acceleration however I can't remember why they said to do this. However since I only installed this ubuntu last week I havn't not done it to this machine, I don't think - I think it was a laptop issue someone suggested to remove it on.

---

### Post by iamtheeggman2 on 2020-05-02
Furthermore I can't understand why when I go to directional drivers as suggested on the following link for this problem appearing in an old ubuntu, why my additional drivers list is void of any.

[https://ubuntuforums.org/showthread.php?t=2073987&page=2](https://ubuntuforums.org/showthread.php?t=2073987&page=2)

---

### Post by coffeecat on 2020-05-02
> **iamtheeggman2 said:**
> Furthermore I can't understand why when I go to directional drivers as suggested on the following link for this problem appearing in an old ubuntu, why my additional drivers list is void of any.

[https://ubuntuforums.org/showthread.php?t=2073987&page=2](https://ubuntuforums.org/showthread.php?t=2073987&page=2)

Are you sure you linked to the correct thread? That is nearly 8 years old, refers to a long obsolete version of Ubuntu, probably describes a different problem than yours (a full xserver crash rather than your freeze) and, most importantly, involves nvidia graphics hardware whereas you have AMD graphics. In short - irrelevant to your problem.

As to additional drivers not offering you any proprietary drivers, your Radeon HD 4350/4550 is using the correct open source radeon driver. There is no proprietary driver for it.

---

### Post by iamtheeggman2 on 2020-05-02
> **coffeecat said:**
> Are you sure you linked to the correct thread? That is nearly 8 years old, refers to a long obsolete version of Ubuntu, probably describes a different problem than yours (a full xserver crash rather than your freeze) and, most importantly, involves nvidia graphics hardware whereas you have AMD graphics. In short - irrelevant to your problem.

As to additional drivers not offering you any proprietary drivers, your Radeon HD 4350/4550 is using the correct open source radeon driver. There is no proprietary driver for it.



OK thanks for your response, but what about the HWE link they described the same issues as me on their page.

---

### Post by Impavidus on 2020-05-02
HWE refers to using a newer kernel+drivers in an older (>9 months) LTS release of Ubuntu. Basically, you can use the kernel from the latest interim release, so that the latest LTS release can support the latest hardware. As 20.04 has just been released, it doesn't apply to you.

---

