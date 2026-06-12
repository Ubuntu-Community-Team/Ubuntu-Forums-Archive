---
title: "I think firefox freeze my system and I have to reboot"
date: 2021-07-16
forum: General Help
---

### Post by jfca283 on 2021-07-16
Hello, 
I've been experiencing many errors since I'm using ubuntu 20.
I noticed when I have running firefox with some tabs, suddenly, my system freeze.
I can move only the mouse, but everything else collapse.
I installed epiphany in order to test if firefox was 100% responsible, but sometime even using epiphany the system freeze.
When the system freeze I have to wait more than 10-20 minutes in order to recover control over the system, or reboot.
How can I be sure of the reason of this strange behavior?
How can I look on the log to discover the reason of this problem?
I'm using firefox 89.0.2 (64 bits) and ubuntu 20.04
My PC is running with 16 GB RAM and Intel i7.
By the way, using firefox and windows 10 I never suffer from this crashes/problems.
Thanks for your time and interest.

---

### Post by grahammechanical on 2021-07-17
System monitor is a Graphical User Interface (GUI) utility that shows, almost in real time, the processes that are active, the resources (CPU, memory, internet) that are being used and the file system (partitions) usage.

Regards

---

### Post by jfca283 on 2021-07-23
I can't use system monitor when It freezes my screen.
When some time pass and I can recover the system, I don't see any peak of memory of cpu usage.
How can I post the log when the problem occur?

This is some info I could recover

Jul 23 03:35:22 juan-OptiPlex-7010 kernel: [24160.158248] [TTM] Buffer eviction failed

```
Jul 23 03:35:22 juan-OptiPlex-7010 kernel: [24160.158248] [TTM] Buffer eviction failed
Jul 23 03:36:23 juan-OptiPlex-7010 kernel: [24220.577412] [TTM] Buffer eviction failed
Jul 23 03:37:26 juan-OptiPlex-7010 kernel: [24284.315968] [TTM] Buffer eviction failed
Jul 23 03:44:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jul 23 03:44:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jul 23 03:44:38 juan-OptiPlex-7010 gnome-shell[1884]: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jul 23 03:44:38 juan-OptiPlex-7010 gnome-shell[1884]: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jul 23 03:44:38 juan-OptiPlex-7010 gnome-shell[1884]: g_dbus_connection_emit_signal: assertion 'G_IS_DBUS_CONNECTION (connection)' failed
Jul 23 03:44:38 juan-OptiPlex-7010 gnome-shell[1884]: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jul 23 03:44:38 juan-OptiPlex-7010 gnome-shell[1884]: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jul 23 03:51:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jul 23 03:51:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jul 23 03:51:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jul 23 03:51:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jul 23 03:51:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jul 23 03:51:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jul 23 03:51:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jul 23 03:51:37 juan-OptiPlex-7010 gnome-shell[1884]: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jul 23 03:52:23 juan-OptiPlex-7010 gnome-shell[1884]: JS ERROR: TypeError: this._workspacesViews[i] is undefined#012_updateWorkspacesFullGeometry@resource:///org/gnome/shell/ui/workspacesView.js:756:13#012setWorkspacesFullGeometry@resource:///org/gnome/shell/ui/workspacesView.js:746:14#012setWorkspacesFullGeometry@resource:///org/gnome/shell/ui/viewSelector.js:301:33#012_updateWorkspacesGeometry@resource:///org/gnome/shell/ui/overviewControls.js:498:27#012vfunc_allocate@resource:///org/gnome/shell/ui/overviewControls.js:402:14#012_computeWindowCenter@resource:///org/gnome/shell/ui/workspace.js:302:35#012_init@resource:///org/gnome/shell/ui/workspace.js:160:14#012_addWindowClone@resource:///org/gnome/shell/ui/workspace.js:1856:21#012_init@resource:///org/gnome/shell/ui/workspace.js:1174:22#012_updateWorkspaces@resource:///org/gnome/shell/ui/workspacesView.js:232:29#012_init@resource:///org/gnome/shell/ui/workspacesView.js:91:14#012_updateWorkspacesViews@resource:///org/gnome/shell/ui/workspacesView.js:682:24#012show@resource:///org/gnome/shell/ui/workspacesView.js:612:14#012show@resource:///org/gnome/shell/ui/viewSelector.js:276:33#012_animateVisible@resource:///org/gnome/shell/ui/overview.js:580:27#012show@resource:///org/gnome/shell/ui/overview.js:566:14#012_onShowAppsButtonToggled@/usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.c
```

---

### Post by ajgreeny on 2021-07-23
Tell us more about your hardware with output of command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by ActionParsnip on 2021-07-23
Do other browsers do the same?
Do other applications cause the issue (not web browsers)?
Is it particular content that causes the issue like Java or YouTube content etc?

---

### Post by jfca283 on 2021-07-23
```
juan@juan-OptiPlex-7010:~$ inxi -Fzx
System:
  Kernel: 5.8.0-63-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Desktop System: Dell product: OptiPlex 7010 v: 01 serial: <filter> 
  Mobo: Dell model: 0773VG v: A02 serial: <filter> BIOS: Dell v: A12 
  date: 01/10/2013 
CPU:
  Topology: Quad Core model: Intel Core i7-3770 bits: 64 type: MT MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 8192 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 54275 
  Speed: 2395 MHz min/max: 1600/3900 MHz Core speeds (MHz): 1: 2991 2: 3865 
  3: 2319 4: 3391 5: 2913 6: 2273 7: 2121 8: 2757 
Graphics:
  Device-1: NVIDIA GT218 [GeForce 210] vendor: Micro-Star MSI N210 Geforce 
  driver: nouveau v: kernel bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.9 driver: nouveau 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: NVA8 v: 3.3 Mesa 20.2.6 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio vendor: Dell 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-2: NVIDIA High Definition Audio 
  vendor: Micro-Star MSI N210 Geforce 210 PCIe driver: snd_hda_intel 
  v: kernel bus ID: 01:00.1 
  Device-3: N/A type: USB driver: snd-usb-audio,uvcvideo bus ID: 2-1.5:3 
  Sound Server: ALSA v: k5.8.0-63-generic 
Network:
  Device-1: Intel 82579LM Gigabit Network vendor: Dell driver: e1000e 
  v: 3.2.6-k port: f040 bus ID: 00:19.0 
  IF: eno1 state: up speed: 100 Mbps duplex: full mac: <filter> 
  Device-2: KYE Systems (Mouse Systems) GF3000F Ethernet Adapter type: USB 
  driver: hid-generic,usbhid bus ID: 3-1:2 
Drives:
  Local Storage: total: 1.35 TiB used: 53.55 GiB (3.9%) 
  ID-1: /dev/sda vendor: Toshiba model: MQ01ABD100 size: 931.51 GiB 
  temp: 22 C 
  ID-2: /dev/sdb vendor: Kingston model: SA400S37480G size: 447.13 GiB 
  temp: 33 C 
Partition:
  ID-1: / size: 200.30 GiB used: 53.55 GiB (26.7%) fs: ext4 dev: /dev/sdb5 
Sensors:
  System Temperatures: cpu: 33.0 C mobo: N/A gpu: nouveau temp: 29 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 276 Uptime: 1h 01m Memory: 15.59 GiB used: 2.64 GiB (16.9%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38
```

---

### Post by jfca283 on 2021-07-23
I can't tell.
I think It's only firefox.
I don't know if the cause is an extension or something related.
Sometimes I need to wait  10-20 minutes to gain control over the station.
I need even reboot manually my PC when the wating is over 20 minutes.
It's funny that now I trust more on windows than ubuntu, and I hate windows.

---

### Post by jadaube2 on 2021-08-15
Hi jfca283,

I've been experiencing something similar for a couple of days, but i'm using 18.04.  Firefox freezes or disappears, I can't open System Monitor, firefox does not appear as a process, and then then whole thing crashes.  When I reboot, there is file system damage, and I have to run fsck to fix it. I realized I had neglected to run updates for a couple of weeks, and just did so, and sure enough there was a Firefox update.  I don't know if that resolved the problem, but I guess I'll find out soon enough - I'm typing this on firefox right now.

I would suggest you run fsck from a live cd to make sure everything's alright, then reboot and and run apt update, apt upgrade. 

I'll let you know if my firefox crashes again. If it does, I plan to use purge and then reinstall.

Good luck.

---

### Post by GhX6GZMB on 2021-08-15
Firefox has for years been notorious for filling up RAM when running for some time with multiple tabs. This applies both to Win and Ubuntu machines.
I actually thought it had been solved in the newer versions, as I haven't heard of the issue lately.
Perhaps an update to the latest FF version?

---

### Post by jfca283 on 2021-08-16
I disabled every extension, but I still suffer from freezing issues.
Only in Ubuntu20.04, not in Windows10.
The most annoying thing is not knowing the cause.
How can I inform you if when I recover the control of my machine the system monitor looks normal...?

---

### Post by monkeybrain20122 on 2021-08-16
> **ml9104 said:**
> Firefox has for years been notorious for filling up RAM when running for some time with multiple tabs. This applies both to Win and Ubuntu machines.
I actually thought it had been solved in the newer versions, as I haven't heard of the issue lately.
Perhaps an update to the latest FF version?

I have some pretty weak machines including VMs and Firefox never exhibits the issue reported by OP. In fact FF is much more efficient if you have multiple tabs since it lazyloads them. On my fairly weak netbook from 2013 with a modest 6 G of rams FF runs very smooth with 150 tabs. Chromium based browsers (google-chrome, Vivaldi etc)  would choke with just 20, it does a lot better with the lazytab extension but still nowhere near Firefox. 

OP has 16 G of ram and a i7, no way this is due to memory shortage, if that specs is not enough ram for FF it won't run on any hardware.

---

### Post by jfca283 on 2021-08-16
Maybe It's the video driver I am using?


```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: Micro-Star International Co., Ltd. [MSI] N210 [Geforce 210] PCIe graphics adapter
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb, nouveau
```

I installed the nividia driver from the software and update app

---

### Post by monkeybrain20122 on 2021-08-16
Did you try booting into an older kernel? When startup, hit ESC then choose advanced and choose the previous kernel.

What video driver are you using?

---

### Post by monkeybrain20122 on 2021-08-16
So you are using noveau, maybe you should install the Nvidia proprietary driver. Probably Nvidia-331

---

### Post by jfca283 on 2021-08-16
I tried using the software and updates...Didn't work

---

### Post by monkeybrain20122 on 2021-08-16
> **jfca283 said:**
> I tried using the software and updates...Didn't work

Install nvidia-340 and reboot (or nvidia-331 which is a transitional package) It is a very old card but according to this [thread]("https://forums.linuxmint.com/viewtopic.php?t=341365") 340 works.
```

sudo apt install nvidia-340
```

---

### Post by jfca283 on 2021-08-16
I tried installing the driver
```
juan@juan-OptiPlex-7010:~$ sudo apt install nvidia-340
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
nvidia-340 est déjà la version la plus récente (340.108-0ubuntu5.20.04.2).
Le paquet suivant a été installé automatiquement et n'est plus nécessaire*:
  libllvm11
Veuillez utiliser «*sudo apt autoremove*» pour le supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 33 non mis à jour.
1 partiellement installés ou enlevés.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer*? [O/n] o
Paramétrage de nvidia-340 (340.108-0ubuntu5.20.04.2) ...
dpkg: erreur: mauvaise syntaxe de la version «*-*»: revision number is empty
dpkg: erreur: mauvaise syntaxe de la version «*-*»: revision number is empty
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Removing old nvidia-340-340.108 DKMS files...

------------------------------
Deleting module version: 340.108
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-340-340.108 DKMS files...
Building for 5.11.0-25-generic
Building for architecture x86_64
Building initial module for 5.11.0-25-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-340.0.crash'
Error! Bad return status for module build on kernel: 5.11.0-25-generic (x86_64)
Consult /var/lib/dkms/nvidia-340/340.108/build/make.log for more information.
dpkg: erreur de traitement du paquet nvidia-340 (--configure)*:
 installed nvidia-340 package post-installation script subprocess returned error exit status 10
Traitement des actions différées («*triggers*») pour libc-bin (2.31-0ubuntu9.2)*...
Traitement des actions différées («*triggers*») pour initramfs-tools (0.136ubuntu6.6)*...
update-initramfs: Generating /boot/initrd.img-5.11.0-25-generic
Des erreurs ont été rencontrées pendant l'exécution*:
 nvidia-340
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I don't know how to handle this mess.
Any idea?

---

### Post by jfca283 on 2021-08-16
it seems a kernel issue....

---

### Post by monkeybrain20122 on 2021-08-16
So it looks like the driver was already installed before but somehow didn't get loaded.

To get out from your current problem
```
sudo dpkg --configure -a
```

---

### Post by jadaube2 on 2021-08-22
After the upgrade, the problem seems to have resolved itself.

---

### Post by jfca283 on 2021-08-22
What upgrade?

---

### Post by shantiq on 2021-08-23
just a very general point/observation here
FF has the most functionalities of all browsers but and in all the various versions of Ubuntu used over last few years it required more RAM higher specs than any of the other browsers
Currently I have a machine that is happy with it but often before not
So I use Brave Midori Palemoon even Otter-browser for FASTER much faster results AND go to FF for tasks which only it can do
I would suggest [Brave]("https://brave.com/") to you as it is fast and has many of the functions or even Chromium it is derived from but maybe you want it to be FF
Anyway i would add that


EDIT:   oh then i see you have 16Gb of RAM and an i7     anyway i leave this here as a general point of info

---

### Post by jfca283 on 2021-08-23
I'm thinking it is not firefox or thunderbird.
When I use Libreoffice and Firefox, I freezes.
When I use Rstudio and Firefox, I freezes.
When I use Libreoffice and Spotify, I freezes.

I think it's a problem related to the memory management.
The strange thing is windows is performing way better than ubuntu doing the same tasks.
And I dislike windows for many reasons. But I just can't find a way to solve my problems.
A SSD drive, i7 and 16 gb doesn't look like a poor machine. Maybe reinstalling ubuntu?

---

### Post by mIk3_08 on 2021-08-23
> **ml9104 said:**
> Firefox has for years been notorious for filling  up RAM when running for some time with multiple tabs. This applies both  to Win and Ubuntu machines.
I actually thought it had been solved in the newer versions, as I haven't heard of the issue lately.
Perhaps an update to the latest FF version?

> **monkeybrain20122 said:**
> I have some pretty weak machines including VMs and Firefox never exhibits the issue reported by OP. In fact FF is much more efficient if you have multiple tabs since it lazyloads them. On my fairly weak netbook from 2013 with a modest 6 G of rams FF runs very smooth with 150 tabs. Chromium based browsers (google-chrome, Vivaldi etc)  would choke with just 20, it does a lot better with the lazytab extension but still nowhere near Firefox. 
OP has 16 G of ram and a i7, no way this is due to memory shortage, if that specs is not enough ram for FF it won't run on any hardware.

I am totally agree with "monkeybrain20122" I also have very poor system machine hardware with 4GB Ram and it run Linux Ubuntu 18 LTS (Long Term Support) Operating System and the users uses Firefox browser and it work fine without any
hassle opening multiple tabs. We use this system machine for a long time now and we haven't encounter any problem in it. Thanks to Linux Ubuntu Community and Linux Ubuntu Developers for there digital art work that help us a lot in a daily basis of use.
We open multiple kinds of browser including Firefox with multiple tab in a 4GB Ram system machine hardware and once again Thanks to Linux Ubuntu Developers and Thanks to God up to this moment we haven't experience any difficulties like
freezing and any problems etc of this Linux Ubuntu LTS (Long Term Support) Operating System. So regards and Good Luck.

---

### Post by vmpx on 2021-10-13
Try disable in browser "use hardware acceleration".

---

### Post by savagefluxhp on 2021-12-28
I removed Firefox and then installed Chromium.  I haven't had a problem of my system crashing since.  Running a Raspberry Pi400, Ubuntu 21.1 impish version.  So far that has been my fix and everything seems to be running well.

$ sudo apt-get --purge autoremove firefox

$ sudo apt update
$ sudo apt install chromium-browser

cheers, hope that helps

---

