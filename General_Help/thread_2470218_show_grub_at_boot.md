---
title: "show grub at boot"
date: 2021-12-22
forum: General Help
---

### Post by T6&amp;sfpER35% on 2021-12-22
so after all my desktop started to freeze again after about 3months of no problem. iv'e read somewhere that changing in  grub the  splash screen to nomodeset seems to work.
now i want to try that but cannot get the grub menu at start up , iv'e hit/hold shift , esc  ect at start but nothing works .
iv'e only got xubuntu 20.04.3 with kernel 5.4.0-91-generic on here .
i don't know why every time after a few months , the pc would start freezing randomly .

---

### Post by oldfred on 2021-12-22
With random freezes I might check all the hardware.

If using proprietary driver like nVidia, using nomodeset prevents nVidia driver from loading. 

Shift is for BIOS installs, if an UEFI based install you press escape just after UEFI/BIOS screen but before grub menu appears. Timing can be tricky, often have to try several times to know when or catch the exact time.

You can change grub setting to always show grub.
With 18.04 or later to always see menu
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT_STYLE=menu

sudoedit /etc/default/grub

after any grub changes to update grub menu grub.cfg:
sudo update-grub

---

### Post by T6&amp;sfpER35% on 2021-12-22
i don't know how to check hardware issues, my thinking is why would it work fine a couple months then starts with freezes?
every time it starts freezing i would do a fresh install and it'll work fine again for couple months.
anyhow , i edited/updated the grub settings and it shows at boot now 
[ATTACH=CONFIG]289672[/ATTACH]
then at 'ubuntu' i press "e" , but see no splash screen thingy
[ATTACH=CONFIG]289673[/ATTACH]
even checked 'advanced options' with "e" , shows nothing
[ATTACH=CONFIG]289674[/ATTACH]
this is a proper old machine so don't know if that's maybe why?
```
jp@14:~$ inxi -Fxzd
System:    Kernel: 5.4.0-91-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ECS model: G31T-M7 v: 1.0 serial: <filter> 
           BIOS: American Megatrends v: 080014 date: 02/25/2010 
CPU:       Topology: Dual Core model: Pentium E5300 bits: 64 type: MCP arch: Penryn rev: A 
           L2 cache: 2048 KiB 
           flags: lm nx pae sse sse2 sse3 ssse3 vmx bogomips: 10374 
           Speed: 1581 MHz min/max: 1203/2603 MHz Core speeds (MHz): 1: 1557 2: 1456 
Graphics:  Device-1: NVIDIA GT218 [GeForce 210] vendor: ASUSTeK EN210 SILENT driver: nouveau 
           v: kernel bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.13 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1600x900~60Hz 
           OpenGL: renderer: NVA8 v: 3.3 Mesa 21.0.3 direct render: Yes 
Audio:     Device-1: Intel NM10/ICH7 Family High Definition Audio vendor: Elite Systems 
           driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
           Device-2: NVIDIA High Definition Audio vendor: ASUSTeK driver: snd_hda_intel 
           v: kernel bus ID: 01:00.1 
           Sound Server: ALSA v: k5.4.0-91-generic 
Network:   Device-1: Qualcomm Atheros Attansic L2 Fast Ethernet vendor: Elite Systems 
           driver: atl2 v: 2.2.3 port: ec00 bus ID: 02:00.0 
           IF: ens32 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 465.76 GiB used: 32.26 GiB (6.9%) 
           ID-1: /dev/sda vendor: Samsung model: HD503HI size: 465.76 GiB 
           Floppy-1: /dev/fd0 
           Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GH22NS40 rev: NL01 
           dev-links: cdrom,cdrw,dvd,dvdrw 
           Features: speed: 48 multisession: yes audio: yes dvd: yes 
           rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
Partition: ID-1: / size: 456.95 GiB used: 32.26 GiB (7.1%) fs: ext4 dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 38.0 C mobo: N/A gpu: nouveau temp: 30 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 182 Uptime: 18m Memory: 2.92 GiB used: 1.39 GiB (47.6%) Init: systemd 
           runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
jp@14:~$ 

```
edit : i did change the nVidia driver to the nouveau driver before i did the grub update , thanks for that ,didn't know that , i could have been in a pickle there

---

### Post by T6&amp;sfpER35% on 2021-12-22
ok wait , only place i saw "quiet splash" now was in the grub setting (**sudoedit /etc/default/grub**)
so edited it to "quiet splash nomodeset" and updated grub and restart.
then my display was HUGE... so reverted back.
not sure where to from here

not even sure how a boot process would affect random freezes later on ?

---

### Post by oldfred on 2021-12-22
You have to update grub settings file. Then run the sudo update-grub so on reboot the standard grub.cfg has those new settings.
the e for edit of grub is only when you are rebooting, not when editing grub's files as you have already booted.

If you want nomodeset, you replace the quiet splash setting on the linux line with nomodeset (or add it).
Since you have nVidia, I would not permanently change it, but you can change the /etc/default/grub file & its quiet splash line as permanent change.

I like to remove quiet splash so I see boot process. It used to be you could follow it, but with my SSD now it boots so quickly I can barely follow boot process. All those lines are in log files & sometimes review of log files may show errors.

Are you dual booting with Windows. Windows updates can change system settings and make it seem like Ubuntu has issues.

---

### Post by T6&amp;sfpER35% on 2021-12-23
thanks for trying to help, but i'm not sure i understand?
i thought i did update grub settings , i saved it , the changes showed .
then i ran update grub .
when i changed to nomodeset , my graphics/display were huge so i changed everything back to where it were .

iv'e read in another thread here some guy said he solved the freezes by changing his RAM. 
but in my case what i can't grasp is ,why would my hardware , ram , motherboard, whatever ,work after a fresh install ,  for 3-4 months flawlessly , and then all of a sudden start freezing...
i'm tired of doing fresh installs lol

---

### Post by dragonfly41 on 2021-12-23
> but in my case what i can't grasp is ,why would my hardware , ram , motherboard, whatever ,work after a fresh install , for 3-4 months flawlessly , and then all of a sudden start freezing...

Any *physical* disruption .. such as moving around your PC to make room for the Christmas tree?

---

### Post by T6&amp;sfpER35% on 2021-12-23
nope , it stays stationary in one spot

---

### Post by oldfred on 2021-12-23
Grub uses 640x480 as default so everything in a newer system will be large.
You can in grub check available setting.
c for command line, then this should show available settings. Often you want same as your screen.
vbeinfo

Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


From a grub command line to see available settings pressing <c> & escape to get back to menu:


Then in grub change like this, but use your setting not example of 1366x768 unless that is your setting.
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1366x768

---

### Post by T6&amp;sfpER35% on 2021-12-27
ok well i tried everything suggested + just about all the info i could find on the webs , it still freezes all the time now .
i'm done doing fresh installs and whatnots.
so , sad as it is for me , i went with win10 , at least till i get a new pc 1day.
i'll see in 3-4 months if win10 also start to freeze out of the blue.
thanks for all the effort trying to get it fixed , not only in this thread but multiple one's i saw with freezing problem.

):P

---

