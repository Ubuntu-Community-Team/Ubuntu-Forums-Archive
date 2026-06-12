---
title: "New laptop frequently freezes with Ubuntu"
date: 2024-04-01
forum: General Help
---

### Post by sunhatzhenya on 2024-04-01
Hello! I got a new laptop for Christmas, and decided to use Ubuntu rather than the default install of Windows that it came with. I'd never used Linux before, but after a week or two of troubleshooting I was able to get everything working the way that I wanted, but with one major issue: my laptop freezes up a *lot*. There are some apps that cause it to happen more often (such as Discord), but multiple times today I had it crash when all I had open were 6-7 Firefox tabs and two instances of the default calculator app. I have to assume that I messed something up with the installation, as I can't imagine this frequency of crashing is to be expected with a new computer. Are there any fixes people might recommend I take a look at?

System specs:
Processor: AMD® Athlon gold 7220u with radeon graphics × 4
Memory: 4.0 GiB
Graphics: raphael_mendocino, LLVM 15.0.7, DRM 3.54, 6.5.0-26-generic
Disk Capacity: 128 GiB

---

### Post by HermanAB on 2024-04-01
Linux should never crash.  I had machines run four years continuously without ever stopping or restarting for any reason - eventually the PSU blew up.

So, look at the logs to figure out what is the matter.

---

### Post by Rubi1200 on 2024-04-01
You can help us by posting some more information.

Open a terminal with Ctrl+Alt+T and run these commands:

```
inxi -Fz
df -Th
```

Run each one separately and when replying use Go Advanced >> paste the output >> highlight the text >> click on the # icon to wrap with code tags. It makes analysis much easier.

---

### Post by ajgreeny on 2024-04-02
However with your hardware and only 4G ram you will probably find one of the other 'buntu versions much better,  faster and smoother than the Ubuntu with gnome that I assume you are using,

Try live versions of Xubuntu, Kubuntu, Ubuntu-Mate, etc, etc, all using the now very stable version 22.04.
See which you prefer then maybe install it on a new partition to see if it is better for you and that hardware.

---

### Post by linux4penguins on 2024-04-03
Does it start out fine and then starts freezing later? I had that happen with a system with 8gb. The ram would get overloaded and the system would start thrashing. 
I'm now on a 16gb computer and it runs smooth. So I suspect it's the low ram as mentioned before. Maybe look into if you can upgrade the RAM on the laptop.

---

### Post by sunhatzhenya on 2024-04-06
> **linux4penguins said:**
> Does it start out fine and then starts freezing later? I had that happen with a system with 8gb. The ram would get overloaded and the system would start thrashing. 
I'm now on a 16gb computer and it runs smooth. So I suspect it's the low ram as mentioned before. Maybe look into if you can upgrade the RAM on the laptop.

Yeah, this is what happens with me - it's buttery smooth until a switch  just flips, and suddenly I can't do anything until I reboot the system. The laptop is pretty damn slim, I'd be very surprised if I was able to upgrade the specs in any capacity.

> **ajgreeny said:**
> However with your hardware and only 4G ram you  will probably find one of the other 'buntu versions much better,  faster  and smoother than the Ubuntu with gnome that I assume you are using,

Try live versions of Xubuntu, Kubuntu, Ubuntu-Mate, etc, etc, all using the now very stable version 22.04.
See which you prefer then maybe install it on a new partition to see if it is better for you and that hardware.

I was worried something like this would be the case! I thought I'd be able to skate by with my 4GB here, but I'll take a look at one of those other distributions.

---

### Post by sunhatzhenya on 2024-04-06
Here's what I got from running inxi:
```
System:
  Kernel: 6.5.0-26-generic x86_64 bits: 64 Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 82VG v: IdeaPad 1 15AMN7
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0T76477 WIN
    serial: <superuser required> UEFI: LENOVO v: KSCN26WW date: 04/14/2023
Battery:
  ID-1: BAT1 charge: 18.1 Wh (42.9%) condition: 42.2/42.0 Wh (100.5%)
CPU:
  Info: dual core model: AMD Athlon Gold 7220U with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 1024 KiB
  Speed (MHz): avg: 892 min/max: 900/5773 cores: 1: 898 2: 875 3: 898
    4: 898
Graphics:
  Device-1: AMD driver: amdgpu v: kernel
  Device-2: Chicony Integrated Camera type: USB driver: uvcvideo
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: amdgpu,ati
    unloaded: fbdev,modesetting,radeon,vesa gpu: amdgpu
    resolution: 1920x1080~60Hz
  OpenGL: renderer: RAPHAEL_MENDOCINO (raphael_mendocino LLVM 15.0.7 DRM
    3.54 6.5.0-26-generic)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2
Audio:
  Device-1: AMD driver: snd_hda_intel
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    driver: snd_pci_acp6x
  Device-3: AMD Family 17h HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k6.5.0-26-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek driver: rtw89_8852be
  IF: wlp2s0 state: up mac: <filter>
Bluetooth:
  Device-1: Realtek Bluetooth Radio type: USB driver: btusb
  Report: hciconfig ID: hci0 rfk-id: 2 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 119.24 GiB used: 32.75 GiB (27.5%)
  ID-1: /dev/nvme0n1 vendor: SSSTC model: CL1-4D128 size: 119.24 GiB
Partition:
  ID-1: / size: 116.32 GiB used: 32.73 GiB (28.1%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 22.1 MiB (4.3%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 4.6 GiB used: 595.5 MiB (12.6%)
    file: /swapfile
Sensors:
  System Temperatures: cpu: 35.0 C mobo: N/A gpu: amdgpu temp: 32.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 260 Uptime: 9m Memory: 3.06 GiB used: 1.9 GiB (62.2%)
  Shell: Bash inxi: 3.3.13

```

And here's the other output:
```
Filesystem     Type      Size  Used Avail Use% Mounted on
tmpfs          tmpfs     314M  2.3M  311M   1% /run
/dev/nvme0n1p2 ext4      117G   33G   78G  30% /
tmpfs          tmpfs     1.6G     0  1.6G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
efivarfs       efivarfs  148K  143K   315 100% /sys/firmware/efi/efivars
/dev/nvme0n1p1 vfat      511M   23M  489M   5% /boot/efi
tmpfs          tmpfs     314M  128K  314M   1% /run/user/1000
```

Thank you!!

---

### Post by dragonfly41 on 2024-04-07
> [COLOR=#000000] I thought I'd be able to skate by with my 4GB here.[/COLOR][COLOR=#000000]
Famous last words. To "skate by" you need to be ruthless in shutting down unwanted processes which take up RAM.  Kill redundant browser tabs.  With apps closed install Stacer which (although consuming RAM) will give you a GUI showing how much RAM is taken up by processes. You can do the same by command line (e.g. top) but you might prefer a bird's eye view.  In Stacer you can routinely clean up. The 6th button down lists processes. Searching "stacer" shows 169MB usage of RAM. Inspect your browser tab processes (e.g. google or firefox). Stacer is your laptop stethoscope.

[/COLOR]

---

### Post by HermanAB on 2024-04-08
I would just install Xubuntu and be done with it.

---

### Post by hyperlinxe on 2024-04-11
Freezing means you've breached the limitations of your hardware,
and so if 4gb of ram is to blame that would mean you had actually
filled up 4gb of ram, or close to it, which takes some effort.

You should be able to solve your problem by reducing the programs
that are loaded up automatically, as opposed to having to install 
a completely new operating system. You can reduce the services
running in the background and the auto start programs to free up your ram,
and look at using lightweight applications too.

If ubuntu's default settings take up 1.6-2gb of ram, turning off unnecessary
services, and auto-start programs will bring your base system(with no apps open)
to around 1 gb or ram, or less if you're lucky. Firefox takes up anywhere between 400mb
to 1gb of ram if you're doing lots of things with it. But what happens is that as you fill up 
your ram, you'll notice the apps you're using are fast, but the overall system slows down,
as you start to fill up your memory, and then when switching between apps, you'll notice
that it is slower than you would expect, because you're overall system is at it's capacity.

You might also try using firefox from it's own repository instead of snap firefox, which will
allow you to run it with less system resources required of it. you can find instructions for doing so on mozillas website here: [https://support.mozilla.org/en-US/kb/install-firefox-linux?utm_source=www.mozilla.org&utm_medium=referral&utm_campaign=firefox-download-thanks#w_install-firefox-deb-package-for-debian-based-distributions](https://support.mozilla.org/en-US/kb/install-firefox-linux?utm_source=www.mozilla.org&utm_medium=referral&utm_campaign=firefox-download-thanks#w_install-firefox-deb-package-for-debian-based-distributions)

You'll have to copy/paste the commands under the section for installing firefox for debian based distributions, and look up some guide for removing snap firefox before you run the sudo apt update && sudo apt install firefox command.

Then you can use regular ubuntu, slimmed down to run properly with your 4gb of ram.

---

### Post by him610 on 2024-04-12
This does not look right.
```
efivarfs       efivarfs  148K  143K   315 **[COLOR="#FF0000"]100%[/COLOR]** /sys/firmware/efi/efivars
```

> The efivarfs filesystem was created to address the shortcomings of using entries in sysfs to maintain EFI variables. The old sysfs EFI variables code only supported variables of up to 1024 bytes. This limitation existed in version 0.99 of the EFI specification, but was removed before any full releases. Since variables can now be larger than a single page, sysfs isn’t the best interface for this.

I have *efivarfs* on four of my systems, and another (older one) that does not have it.

The most any of my systems have in use is 38%. I run Xubuntu exclusively on my machines.

Maybe, one of the more seasoned contributors will add a comment.

---

