---
title: "Ubuntu 19.04: Suspend on HP Spectre x360 (with nvidia)"
date: 2019-06-06
forum: General Help
---

### Post by hendrik r g on 2019-06-06
Dear all,

  I can't get suspend or hibernate or any kind of standby to work with HP Spectre x360 with an Nvidia card (x360 15-df0126ng).

  
[LIST]
[*]in the ubuntu 19.04 live version, suspend seems to do something but  immediately wakes up. Not ideal but I guess this would be solvable.
[*]in a freshly installed version of 19.04, where only the 418.56  nvidia driver was installed via ubuntu-drivers, the system goes into  suspend and never comes back. I need to press the power button for 10sec  to make a hard restart.
[*]in desperation I tried to make at least hibernate to work to have at  least some sort of standby. Made 32G swapfile and activated it as swap, entry to /etc/default/grub added.  Does not work either (just a clean reboot is perfromed).
[/LIST]
  Blacklisting nouveau does obvisually not help because NVIDIA is the mod.

  Due to the fact that it somewhat works in live mode, I'm almost certain the problem is centered around the NVIDIA driver.

  Any help or idea how to debug would be very appreciated. All articles  I found were several years old and regarding 4.x kernels at best.

---

### Post by hendrik r g on 2019-06-07
I now tried suspend with 6 different distributions (live versions),  latest version each: MX, Manjaro Gnome+KDE, Mint, Suse, Fedora. Interestingly, none of the live versions does even load NVIDIA modules.  Suspend does not work in a single one. HP Bios offers not a single setting  option on this. In Ubuntu, at least the live version appears to suspend and come back.

---

### Post by #&amp;thj^% on 2019-06-07
There is a confirmed bug on this issue starting with Ubuntu 16.04. Unfortunately, this bug has not been fixed even after more than a year. bug: [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1574120](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1574120)
First, Go to System Settings and then click on Power. In the power setting, make sure that option for &#8216;When the lid is closed&#8217; is set to Suspend.
Workaround to make Ubuntu suspend when laptop lid is closed

First, ensure that you have** "pm-utils" **installed on your system. pm-utils is a collection of scripts that handle suspend and resume. (I guess I don't need to tell you that though)
```
sudo apt install pm-utils
```
After that, we need to edit the logind.conf file of systemd.
It&#8217;s always a good idea to make a backup of configuration files before changing them.
```
sudo cp /etc/systemd/logind.conf  /etc/systemd/logind.conf.back
```
Now you have a backup, 
```
sudoedit /etc/systemd/logind.conf
```
you should see something along the lines of:
```

#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=suspend
#HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#HoldoffTimeoutSec=30s
#IdleAction=ignore
#IdleActionSec=30min
#RuntimeDirectorySize=10%
#RemoveIPC=yes
#UserTasksMax=12288
```

What you have to do is to remove the # from some of the lines and change it&#8217;s value to:
```

HandleSuspendKey=suspend
HandleLidSwitch=suspend
HandleLidSwitchDocked=suspend
```
Save your changes and <restart> your system. Now check if your system goes to suspend mode when the lid is closed.

If not, you can also try changing the below line (though I am not sure if that makes a difference):
```

HandleHibernateKey=suspend
```

---

### Post by hendrik r g on 2019-06-08
Thank you 1fallen for your reply.
Very good hint, closing the lid now triggers suspend the the main problem remains:
The following happens when I activate suspend (invariant if via lid close, power button or command):
1) Monitor goes black immediately.
2) About 1 second later, everything is back and I can continue working
3) 5 seconds later, the the power goes off completely and permanently (like it was hibernating).
4) Power button does not react anymore. Nothing can bring the pc back on. Only a hard reset works.

4 of the 7 tried distributions (live versions) did essentially the same including a arc based distribution. From that I guess it must be quite kernel related but I never had a problem like this so I'm not sure where I should start debuging.

---

### Post by hendrik r g on 2019-06-08
Ok, this problem is really strange:

- When the notebook is in the "frozen" state, pressing the power button 25-50 times sometimes brings it back up. Not always.
- But the kernel freezes immediately showing just a black screen and a single _ at the top left.
- I tried to $systemctl suspend  from console in $sudo init 3  mode. It worked ONCE. I tried 5 more times but never worked again. Also freezes in black screen or does not come back at all.

---

### Post by #&amp;thj^% on 2019-06-08
Until I did what was mentioned, I couldn't suspend or hibernate either.(Arch or Ubuntu)
My Specs:
```
System:
  Host: arch Kernel: 5.0.21.a-1-hardened x86_64 bits: 64 
  Desktop: MATE 1.22.1 Distro: Arch Linux 
Machine:
  Type: Laptop System: LENOVO product: 2392APU v: ThinkPad T530 
  serial: <root required> 
  Mobo: LENOVO model: 2392APU v: Win8 Pro DPK TPG serial: <root required> 
  UEFI [Legacy]: LENOVO v: G4ETB4WW (2.74 ) date: 11/23/2018 
Battery:
  ID-1: BAT0 charge: 56.9 Wh condition: 56.9/56.2 Wh (101%) 
CPU:
  Topology: Dual Core model: Intel Core i5-3320M bits: 64 type: MT MCP 
  L2 cache: 3072 KiB 
  Speed: 2303 MHz min/max: 1200/3300 MHz Core speeds (MHz): 1: 1197 2: 1197 
  3: 1197 4: 1197 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: intel 
  resolution: 1600x900~60Hz, 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile v: 4.2 Mesa 19.0.6 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.0.21.a-1-hardened 
Network:
  Device-1: Intel 82579LM Gigabit Network driver: e1000e 
  IF: enp0s25 state: up speed: 1000 Mbps duplex: full mac: <Snip>
  Device-2: Intel Centrino Advanced-N 6205 [Taylor Peak] driver: iwlwifi 
  IF: wlp3s0 state: down mac:<Snip>
  IF-ID-1: tun0 state: unknown speed: 10 Mbps duplex: full mac: N/A 
Drives:
  Local Storage: total: 3.80 TiB used: 1.69 TiB (44.4%) 
  ID-1: /dev/sda vendor: Intel model: SSDSC2BW180A3L size: 167.68 GiB 
  ID-2: /dev/sdb type: USB vendor: Western Digital 
  model: WD My Passport 25E1 size: 1.82 TiB 
  ID-3: /dev/sdc type: USB vendor: Western Digital 
  model: WD My Passport 25E2 size: 1.82 TiB 
Partition:
  ID-1: / size: 155.99 GiB used: 47.84 GiB (30.7%) fs: ext4 dev: /dev/sda4 
  ID-2: /boot size: 487.9 MiB used: 103.0 MiB (21.1%) fs: ext4 
  dev: /dev/sda2 
  ID-3: swap-1 size: 7.66 GiB used: 13.5 MiB (0.2%) fs: swap dev: /dev/sda3 
Sensors:
  System Temperatures: cpu: 53.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 1974 
Info:
  Processes: 195 Uptime: 2h 24m Memory: 11.43 GiB used: 1.69 GiB (14.8%) 
  Shell: bash inxi: 3.0.30 

```
These newer machines with support for windows in the bios is giving them (the kernel devs) grief along with the nvidia driver.
I would like to add that acpi_osi="!Windows 2015" does not solve the problem, while "acpi_osi=! acpi_osi="Windows 2009" does (it could disable the touchpad though).
```
acpi_osi=! acpi_osi="Windows 2009" 
```
I've heard though some functionality is lost.
I wish I had better news for you. :(

---

### Post by cruzer001 on 2019-06-08
I did a search and also suspect the kernel. found a couple things of interest.

[https://askubuntu.com/questions/870301/hp-spectre-x360-kaby-lake-ubuntu-suspend-not-actually-saving-power](https://askubuntu.com/questions/870301/hp-spectre-x360-kaby-lake-ubuntu-suspend-not-actually-saving-power)

[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)

---

### Post by #&amp;thj^% on 2019-06-08
I rigged another motherboard on my laptop for this, it now uses "auto" to switch from UEFI and Legacy Boots.
UEFI Sucks on Hp's
You'll see in my specs "Set BIOS to legacy" IE:"UEFI [Legacy]"

---

### Post by fily1212 on 2019-06-25
Same issue with HP Spectre x360 15-df0006nl with i7-8750H and Nvidia GTX 1050Ti...

---

### Post by odror on 2019-11-04
I have the same issue with ubuntu 19.10 (including the latest mainline kernel, 5.4-rc6). I have spectre 15" with nvidia gtx1650.
In my case it is unusually bad. Not only the machine freezes. It is overheating to almost damage the computer.

I tried  "acpi_osi=! acpi_osi="Windows 2009". It did not make a difference.

Any new ideas. Thanks

---

### Post by hendrik r g on 2019-12-18
As of Dec 2019, the problem still persists with Ubuntu 19.10 (and many  other current Linux distros: Mint, Manjaro, Suse, Gentoo) apparently for  all variants of the Spectre x360 series. Nothing I tried (of the many  many things) changed it. HP is ignoring this for lack of pressure. I'm  very sorry, I can't help. 
But I urge you to write to HP. A good idea  is to hand it in as an official complaint regarding their product as by  there Iso certification they need to take it seriously. If they don't,  write the complaint to their regulatory body (in this case BSI  [www.bsigroup.com](www.bsigroup.com)) that HP is ignoring the customer complaints. Then the  head of quality needs to justify himself and poof corrective measures or  they lose their Iso certification. Best way I know to really **** them  of. The only way to stop them from Ignoring Linux in dier firmware and  bios development for 2000&#8364;+ notebooks is pressure from below. Usually,  WE run the digital **** in companies, make them aware of what they lose  if they **** the devs and admins off. Thank you.

---

### Post by jacob-thefox on 2020-04-13
For anyone who might find this post now.  As of April, 12th, 2020, I was able to get most functions (including suspend to ram, audio, fans) by adding "acpi_osi='Linux' to the kernel command line.  Everything I tried with Windows version strings, etc failed.  It seems this HP works better with Linux if you tell it it's Linux.  There are still numerous ACPI errors in the dmesg log, but the laptop seems to function more or less correctly without melting down or freezing.

---

