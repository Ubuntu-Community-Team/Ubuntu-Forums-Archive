---
title: "Trouble with installing Nvida 390 driver on Ubuntu 18.10"
date: 2018-11-09
forum: General Help
---

### Post by roadrash on 2018-11-09
Ive been trying for ages now to get my system working with Nvidia driver.   My desktop has a Nvidia GTX-480 graphics card and I have tried every Nvidia driver since the 304 version and have much the same problem with them all.
The last Ubuntu I have had working with a Nvidia driver is 18.04.  I have read through all the posts I could find on the problem with Ubuntu 19.10 and Nvida drivers.  I have tried numerous suggestions and tried the supposed fix by uncommenting the line #WaylandEnable=false in /etc/gdm3/custom.conf.  I tried altering the bootloader to remove & include the nomodeset option too.  I tried purging nvidia*before installing the driver and using the command "sudo nvida-xconfig after installing the driver and I seem to get to the point when I am logged in and then its doesnt progress to the graphical interface and instead gves the error and then freezes.  Only a hard reset gets me out of it.  If I then purge the nvidia driver its bootes up to the desktop again but only with the nouveau driver and cannot play any videos without them stuttering
I even tried removing wayland and using just lightdm but stsill no joy.  Please can someone tell me what this error means and is it this that is stopping the Nvidia driver working.
This picture shows as far as I get in the boot process before it fails..

---

### Post by oldfred on 2018-11-09
Moved to development sub-forum, since not current released version.

You should only install the correct driver for your card.
If a newer card then any one of the newer drivers usually works, but many want the newest and use the ppa.

If older card there is only one legacy driver.
       Legacy drivers by GPU model, you will see your card needs the 390.xxx driver
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
    
       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by mc4man on 2018-11-09
Do you mean 18.10 or 19.04 as there is no 19.10 till next year..

---

### Post by roadrash on 2018-11-12
Yes sorry I meant 18.10.  Ive just purged Nvidia* to get me back to a desktop I can use but I really need to get this sorted or I have to keep going back to a much older version of Ubuntu.

> **oldfred said:**
> Moved to development sub-forum, since not current released version.

You should only install the correct driver for your card.
If a newer card then any one of the newer drivers usually works, but many want the newest and use the ppa.

If older card there is only one legacy driver.
       Legacy drivers by GPU model, you will see your card needs the 390.xxx driver
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
    
       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

Can you move this back to current area for 18.10 etc,

---

### Post by oldfred on 2018-11-13
Corrected title & moved to general.

---

### Post by Autodave on 2018-11-13
If it worked properly on 18.o4, then it should work on 18.10.  Having said that, I rarely find that updating from one release to another does anything other than create problems that are either very difficult to fix or impossible to fix.  That is why I only use the LTS releases and always do a clean install.  My recommendation would be to do a clean install of 18.04 after backing up everything.  If you were to do a clean install of 18.10, chances are that your Nvidia driver would work.  Then again, it may not.  Either way, you would be looking at another upgrade in 5 months and the possibility/ probability of having issues again.

---

### Post by oldfred on 2018-11-13
My main working install is the latest LTS version. But I keep my last LTS installed in a separate / (root) partition. Since I have data in another partition I only need to install to /. 
And then I do install the latest install, just to see differences, but again in another 25GB partition. 
I used to upgrade every 6 months, but back then had issues. My first clean install worked so well, I decided never to do an upgrade again.

---

### Post by roadrash on 2018-11-14
> **oldfred said:**
> My main working install is the latest LTS version. But I keep my last LTS installed in a separate / (root) partition. Since I have data in another partition I only need to install to /. 
And then I do install the latest install, just to see differences, but again in another 25GB partition. 
I used to upgrade every 6 months, but back then had issues. My first clean install worked so well, I decided never to do an upgrade again.

That makes a lot of sense and you t;hen still have a working system you can switch back to if the latest doesnt work..  I always do a clean install as I found it causes problems sometimes just upgrading so it it looks like I will have to go back to 18.04 again.  The first timer I asked on here about a previous Nvidia 9800GT I was having the same problems with I was told its too old get a newer graphics card.  So I did and still I have the same problem.  At one time they used to say Linux was great for keeping your old harware useable but it seems thats not so anymore.  Would switching to say Debian itself be better that the quicker evolving Ubuntu?

---

### Post by oldfred on 2018-11-14
I would think your 9800 should work as long as you only have the 340.xx driver. The issue is those that are so old they need the very old 304 driver.
[https://www.nvidia.com/object/IO_32667.html](https://www.nvidia.com/object/IO_32667.html)

Issues with nVidia are often where users install incorrect driver then try to install another driver. They then conflict. Drivers do not un-install previous drivers, so you purge driver and perhaps some settings to make sure you only have to correct driver.

But I have a newer 620 card and it works just as well with the open source nouveau driver.

---

### Post by roadrash on 2018-11-17
Well I had to eventually give up on that install as it became impossible tio use it.  So I have now done a new install of Ubuntu 18.10 and I have done all updates so I am now at the point I would normally install the Nvidia driver.  My next move at this point would be to open a terminal and purge everything nvida* before installing the Nvidia 390 driver.  If I do this now it would boot up to the point it loggs me in but will not prgress to a grahical display.  As I said eariler un-comenting the line to disable Waylamd in the /etc/gdm3/custom.conf as suggeted doesn't make any differnce.  Can someone advise what I do from this point with a clean up to date installation to get the Nvidia 390 driver installed & working with a graphical display.

---

### Post by #&amp;thj^% on 2018-11-17
I shutter to even post on this matter any more but I have seen with adding the "/ppa.launchpad.net/graphics-drivers/ppa/ubuntu " and installing with:
```
sudo apt install nvidia-driver-390
```
Works well enough for me>>>but not the case for a few of the others I have tried to help with this.:(

---

### Post by roadrash on 2018-11-18
I tried thios and again it all installed ok.  Then after the install I opened a terminal and entered "nvida-xconfig" & rebooted.
It restarted up and again stopped juist before log in with a dispaly like below and it wont do anything until i press the reset.

         Starting NVIDIA persistance daemon
[ ok ] Started NVIDIA persistance daemon
         Stopping NVIDIA persistance daemon
[ ok ] Stopped NVIDIA persistance daemon
         Stopping user manager of UID 123 ...
[ ok ] Stopped user manager for UID 123 ...
[ ok ] Removed slice user slice of UID 123...
         Stopping /run/user/123 mount wrapper
[ ok ] Stopped  /run/user/123 mount wrapper
[   *   ] A start job is running for hold until boot process finishes up (51s / no limit)

what is happeng???

---

### Post by mc4man on 2018-11-18
Not sure I'd term 18.04 'much older' than 18.10.
In any event if this is a relatively fresh install go

sudo apt purge nvidia*

sudo apt purge libnvidia*

sudo apt autoremove

sudo apt install lightdm > choose lightdm in the pop up & reboot.

After reboot install nvidia-driver-390 & reboot (nothing else..
May be ok, maybe not.

---

### Post by roadrash on 2018-11-19
Thank you mc4man that was very helpful & I thought it might work but I'm 
afraid it didn't.  I thought the install of lightdm would do it.  It 
again booted up to the login point and it stops with a black screen and 
a single little cursor occasionally blinking up in the top left corner of 
the screen.  I could not get out of it by any was ctrl+alt+F1, 2 or 3.  
II did try the un-commenting of #WaylandEnable=false in the 
/etc/gdm3/custom.conf but it made to difference sadly.  This has been 
driving me mad for about a year now.  I even bought a newer graphics 
card to sort it.
I have pasted the lightdm log In case there is something in there that might help solve this.
The very last part might be a successful log in that was done after i removed the nvidia driver so I could get to this Lightdm log and post it here.  So if you look back further in the log it should show the errors trying to start the desktop.  If there are any more logs you need just ask.

[https://paste.ubuntu.com/p/5XVggTBvbt/]("https://paste.ubuntu.com/p/5XVggTBvbt/")

Please can someone help me with this. I have ran out of ideas and if I cant find a solution I will be forced to use Windows which is a shame sice ive use Ubuntu for over 15 years and still love it.
Dont force me to leave Ubuntu I'm begging now please help me resolve this someone.

---

### Post by 23dornot23d on 2018-11-23
Lets try with inxi -F

**sudo apt install inxi**

**inxi -F**

Then post the results please ............ doing a bit of recon .......... find a few things out first - then we will go one step at a time.

Will try to keep you using Linux ........

You can get to a screen through safe-mode ?

Do a search on all **solved items for 390** if that is the driver you think will work ....... **but also on 304 if that one worked** in the past.

Last resort try a different install .... maybe Linux Mint which is based on Ubuntu ....... there are lots of choices with Linux .......

But try all options before returning to ........ something other than Linux ..... best of luck with whatever you do - never give in though.

---

### Post by roadrash on 2018-11-25
Thanks for this help. Believe me there is nothing I want more than to sort this graphical problem ive had since 17.04 and continue to use my lovely Ubuntu Linux.
here is the output I get from inxi -f:

Topology: Dual core model: Intel Core2 6400 bits: 64 type: MCP L2 cache: 2048 KiB
Speed: 2050 MHz min/max: N/A Core speeds (MHz): 1: 2050 2: 2050
Flags:
Acpi aperfmperf apic arch_perfmon bts clflush cmov constant_tsc
cpuid cx16 cx8 de ds_cpi dtest64 dtherm dts est fpu fxsr ht lahf_lm lm mca
mce mmx monitor msr mtrr nopl nx pae pat pbe pdcm pebs pge pni pse pse36
pti rep_good sep SS sse sse2 ssse3 syscall tm tm2 tpr_shadow tsc vme vmx xtpr

I have tried all Nvida drivers for my graphics card 304, 340 & 390, The last driver I had working in ubuntu 17.04 was Nvida-340. I also tried everything & every driver install on both Ubuntu and Linux Mint. I got pretty much the same result with both of them (they are both a variation on Ubuntu).  I ddi google everything linux and ubuntu,mint with nvida driver. I have been so so patient ever since Ubuntu 17.04 etc in trying to sort this and patience has now run out and I must sort thing or change my OS because its annoying watching jerky stuttering video's.
Thanks for your hope and maybe we can at last sort this.

---

### Post by 23dornot23d on 2018-11-25
> 
here is the output I get from inxi -f

=================================

I have tried all Nvida drivers for my graphics card 304, 340 & 390,  The last **driver I had working in ubuntu 17.04 was Nvida-340**



inxi and CAPITAL F as below

**inxi -Fz**

please as it will give more information ......... than the small -f and z is for security according to the man pages linked below for posting on
forums.
  
see here ...... have added (z) also ..... as shown below.

[http://manpages.ubuntu.com/manpages/bionic/man1/inxi.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/inxi.1.html)

> 
**-F**     Show  Full  output  for inxi


hope we can get somewhere ......... when you did previous installs of the graphics - did you also purge all other drivers before starting the test of
the new driver you loaded up ?

Also on the Nvidia - web page for automatic detection which driver is it saying to use ( do not install this yet - but its just to get an idea what nvidia expects to use )

You should download the file ..... if for nothing else .... to get its title .... and post it back here too - the filename of the driver nvidia expects to use
with your graphics card.

[https://www.geforce.com/drivers](https://www.geforce.com/drivers)

400 series ( GTX 480 ) ......... which driver is it saying to use for your system

---

### Post by roadrash on 2018-11-25
The output inxi -Fz~

> System:
  Host: jon-desktop Kernel: 4.18.0-11-generic x86_64 bits: 64 Console: N/A 
  Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Desktop Mobo: N/A model: 4CoreDual-VSTA serial: N/A 
  BIOS: American Megatrends v: P2.30 date: 02/26/2008 
CPU:
  Topology: Dual Core model: Intel Core2 6400 bits: 64 type: MCP 
  L2 cache: 2048 KiB 
  Speed: 2050 MHz min/max: N/A Core speeds (MHz): 1: 2050 2: 2050 
Graphics:
  Device-1: NVIDIA GF100 [GeForce GTX 480] driver: nvidia v: 390.87 
  Display: server: X.org 1.20.1 driver: none tty: 80x25 
  Message: Advanced graphics data unavailable in console for root. 
Audio:
  Device-1: NVIDIA GF100 High Definition Audio driver: snd_hda_intel 
  Device-2: VIA VT8237A/VT8251 HDA driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.0-11-generic 
Network:
  Device-1: VIA VT6102/VT6103 [Rhine-II] driver: via-rhine 
  IF: enp0s18 state: down mac: <filter> 
Drives:
  Local Storage: total: 434.64 GiB used: 16.92 GiB (3.9%) 
  ID-1: /dev/sda vendor: Maxtor model: 7L250R0 size: 233.76 GiB 
  ID-2: /dev/sdb vendor: Seagate model: ST3200826A size: 186.31 GiB 
  ID-3: /dev/sdc type: USB vendor: Kingston model: DataTraveler 2.0 
  size: 14.57 GiB 
Partition:
  ID-1: / size: 134.74 GiB used: 6.69 GiB (5.0%) fs: ext4 dev: /dev/sda6 
  ID-2: swap-1 size: 2.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 37.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 81 Uptime: 31m Memory: 1.95 GiB used: 115.8 MiB (5.8%) 
  Init: systemd Shell: bash inxi: 3.0.24 

The driver reccomended by Ubuntu is Nvida 390.  I usuall;y install if from within Ubuntu other drivers as reccomended.  I always use apt-get purge nvidia* before install.

---

### Post by 23dornot23d on 2018-11-25
> 
**The driver recommended by Ubuntu** is **Nvida 390**.  

I usually install if  from within Ubuntu other drivers as recommended.  I always use apt-get  purge nvidia* before install.                 


So the Nvidia site - no information .......... ?  

--------------------------------------------------------------------------------------------------------

But you do appear to have something installed ..........

It appears to be installed  **driver: nvidia v: 390.87** ............ and if you do **nvidia-settings** does that show it as working ......... 

maybe a screen shot after doing it - if its installed ............ am also adding bumblebee so it will give kms ( kernel mode setting )
as this worked before for a GeForce GTX 970 in a previous post that we solved here ..... which seemed to get things working ok.

[https://ubuntuforums.org/showthread.php?t=2404813&page=7](https://ubuntuforums.org/showthread.php?t=2404813&page=7)



after doing the commands below .......... hopefully we will have some success ....... if not its back to the drawing board.

[B]
sudo apt install nvidia-settings[/B]

[B]sudo apt install bumblebee

sudo apt install lightdm

reboot

[/B]I think you already installed lightdm ..... as this gets away from the  wayland problem and gdm3 ..... but it does not hurt to run
the command again ........ once you have done the commands above - reboot and see if it works ok ..... please post another

**inxi -F**

look for nvidia-settings in the menu and run it ...... please

$ nvidia-settings

** Message: 23:41:30.887: PRIME: Requires offloading
** Message: 23:41:30.887: PRIME: is it supported? yes



if all has worked ok .......

> 

```

what my own looks like for some sort of comparison ...

  driver: nvidia v: 390.87 
  Display: x11 server: X.Org 1.20.1 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 1366x768~60Hz 


```

Yours - from the previous inxi -F that you did ..........

Graphics:
  [B]Device-1: NVIDIA GF100 [GeForce GTX 480] driver: nvidia v: 390.87
[/B] 
  Display: server: **X.org 1.20.1** driver: **none **

tty: 80x25 
  
[B]Message: Advanced graphics data unavailable in console for root. 
[/B]


---

### Post by roadrash on 2018-11-26
I tried what you said and still had the same result, a balck screen with some text and its locked up. I even tried this from yet another fresh install with all updates done and got the same black screen locked up.   You didint say if I needed to select lightdm as my default dektop so I left it as gdm3. I notice your using X.org but I think I use gdm3.   I have now purged nvida again and left everything else like bumblebee installed and here is the output of inxi -Fz:
> System:
  Host: jon-desktop Kernel: 4.18.0-11-generic x86_64 bits: 64 
  Desktop: Gnome 3.30.1 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Desktop Mobo: N/A model: 4CoreDual-VSTA serial: N/A 
  BIOS: American Megatrends v: P2.30 date: 02/26/2008 
CPU:
  Topology: Dual Core model: Intel Core2 6400 bits: 64 type: MCP 
  L2 cache: 2048 KiB 
  Speed: 2050 MHz min/max: N/A Core speeds (MHz): 1: 2050 2: 2050 
Graphics:
  Device-1: NVIDIA GF100 [GeForce GTX 480] driver: N/A 
  Display: server: X.Org 1.20.1 driver: fbdev,nouveau 
  unloaded: modesetting,vesa resolution: 1280x800~76Hz 
  OpenGL: renderer: llvmpipe (LLVM 7.0 128 bits) v: 3.3 Mesa 18.2.2 
Audio:
  Device-1: NVIDIA GF100 High Definition Audio driver: snd_hda_intel 
  Device-2: VIA VT8237A/VT8251 HDA driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.0-11-generic 
Network:
  Device-1: VIA VT6102/VT6103 [Rhine-II] driver: via-rhine 
  IF: enp0s18 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 434.64 GiB used: 15.98 GiB (3.7%) 
  ID-1: /dev/sda vendor: Maxtor model: 7L250R0 size: 233.76 GiB 
  ID-2: /dev/sdb vendor: Seagate model: ST3200826A size: 186.31 GiB 
  ID-3: /dev/sdc type: USB vendor: Kingston model: DataTraveler 2.0 
  size: 14.57 GiB 
Partition:
  ID-1: / size: 134.74 GiB used: 5.73 GiB (4.2%) fs: ext4 dev: /dev/sda6 
  ID-2: swap-1 size: 2.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 44.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 182 Uptime: 6m Memory: 1.95 GiB used: 865.3 MiB (43.4%) 
  Shell: bash inxi: 3.0.24 


---

### Post by 23dornot23d on 2018-11-26
You need to use lightdm as it defaults to xorg .............

gdm3 as far as I know is using wayland , and the problems that some of the threads were saying is 
the easy way is just to use lightdm.

ok so its showing only nouveau being used

Do not remove anything - please follow what I have put below the last inxi you gave me ........ the commands should get your system to
work .......

> 
Graphics:
  Device-1: NVIDIA GF100 [GeForce GTX 480] driver: **N/A **
  Display: server: X.Org 1.20.1 driver: **fbdev,nouveau **
  unloaded: modesetting,vesa resolution: 1280x800~76Hz 
  **OpenGL: renderer: llvmpipe (LLVM 7.0 128 bits) v: 3.3 Mesa 18.2.2** 


( this is a worry too - will it go when loading in Mate - yet to see ) [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1752938](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1752938)

[B]sudo apt reinstall lightdm

[/B]and choose lightdm[B] you might also have to do ( sudo dpkg-reconfigure lightdm ) if you are not given a choice in the command above.

sudo mv xorg.conf xorg.conf-old

sudo apt install mate

[/B]Then using mate ....... go to settings and choose the nvidia driver that it shows ......... under additional drivers
just to be sure we get the driver that is recommended for use.[B]

Should look like this once the nvidia-settings is used with the nvidia driver in place ........ hopefully

[IMG]https://sites.google.com/site/000menu/_/rsrc/1543250526015/wayland/problems-ubuntu-build/nvidia.jpg?height=224&width=400[/IMG][/B]

Then tell us what happens after a fresh boot - seems the nvidia driver is no longer there thats why loading mate and choosing it from there ... as I know
this works on my own system ......... which is using the 390.87 nvidia driver ......

Here is what it looks like in Synaptic searching on Nvidia 390 installed .....
[IMG]https://sites.google.com/site/000menu/_/rsrc/1543256580129/wayland/problems-ubuntu-build/nvidia-390.jpg?height=130&width=500[/IMG]

By the way - once you get the graphics working properly - you can use whichever desktop you prefer ......

---

### Post by roadrash on 2018-11-26
Well hate to say it didn't work either.  I was surprised as i really thought you were onto something that time. 
I set lightdm as disply manger and after install the nvidia driver it still gets stuck at the login stage with a black screen.
I then tried setting xdm as defualt but still it get stuck in the same place.
Can you tell me if you have the line EnableWayland=false uncommented in your /etc/gdm3/custom.conf? 
 I did a inxi report for you again before I purged the nviida driver so I could get back to a desktop.:

>  System:
  Host: jon-desktop Kernel: 4.18.0-11-generic x86_64 bits: 64 Console: N/A 
  Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Desktop Mobo: N/A model: 4CoreDual-VSTA serial: N/A 
  BIOS: American Megatrends v: P2.30 date: 02/26/2008 
CPU:
  Topology: Dual Core model: Intel Core2 6400 bits: 64 type: MCP 
  L2 cache: 2048 KiB 
  Speed: 2050 MHz min/max: N/A Core speeds (MHz): 1: 2050 2: 2050 
Graphics:
  Device-1: NVIDIA GF100 [GeForce GTX 480] driver: nvidia v: 390.87 
  Display: server: X.org 1.20.1 driver: none tty: 80x25 
  Message: Advanced graphics data unavailable in console for root. 
Audio:
  Device-1: NVIDIA GF100 High Definition Audio driver: snd_hda_intel 
  Device-2: VIA VT8237A/VT8251 HDA driver: snd_hda_intel 
  Device-3: Hewlett-Packard type: USB driver: snd-usb-audio,uvcvideo 
  Sound Server: ALSA v: k4.18.0-11-generic 
Network:
  Device-1: VIA VT6102/VT6103 [Rhine-II] driver: via-rhine 
  IF: enp0s18 state: down mac: <filter> 
Drives:
  Local Storage: total: 420.07 GiB used: 6.89 GiB (1.6%) 
  ID-1: /dev/sda vendor: Maxtor model: 7L250R0 size: 233.76 GiB 
  ID-2: /dev/sdb vendor: Seagate model: ST3200826A size: 186.31 GiB 
Partition:
  ID-1: / size: 134.74 GiB used: 6.89 GiB (5.1%) fs: ext4 dev: /dev/sda6 
  ID-2: swap-1 size: 2.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 42.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 90 Uptime: 1m Memory: 1.95 GiB used: 117.7 MiB (5.9%) 
  Init: systemd Shell: bash inxi: 3.0.24 

---

### Post by 23dornot23d on 2018-11-26
> 
Can you tell me if you have the line EnableWayland=false uncommented in your /etc/gdm3/custom.conf? 


No because I do not use gdm3 anymore ........... but it will make no difference to lightdm as it will have its own configuration file.

I have posted it below ........ but I do not alter it ....... as I am not using gdm3

```

# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=base

# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

# Enabling automatic login

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

[security]

[xdmcp]

[chooser]

[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true

```

Are you still able to use it ok in a earlier version - can you post the inxi from that version ........ if it is still running ok in that version.

It does not matter if you have it un-commented out ....... that is not causing the problem - when using lightdm.

The only other thing I do sometimes is to move the /etc/X11/xorg.conf to /etc/X11/xorg.conf-old

and let it find the other one that is set up automatically ...........

somehow it keeps switching ........ mine has a driver in both places ......... each time with your system it has one or the other but not both
I do not understand ........ why ...... maybe someone else does ..........

> 
Device-1: NVIDIA GF100 [GeForce GTX 480] driver: nvidia v: 390.87 
  Display: server: X.org 1.20.1 driver: none tty: 80x25 


**The last Ubuntu I have had working with a Nvidia driver is 18.04**

Do you still manage to get that graphic card to work on the older version  ...... there may be some clues if you can post a inxi from that when its running ok.

but if not - have you tried any of the live boot usb's / dvd's from other linux systems to see if any other system picks up the card properly.

---

### Post by roadrash on 2018-11-26
Ok will try a install of 17.04 I think it was last and see what happens.. to get you a inxi.

---

### Post by oldfred on 2018-11-26
17.04 is EOF or end of life, and you will not get it to work as repositories are closed.

New systems have an UEFI system setting to turn on/off video card or Intel video. Not sure if older BIOS had similar setting or not.

Or some old ones have Optimus Technology and Bumblebee was used. Two switched video but one port. But newer nVidia drivers eliminated the need for Bumblebee which bumblebee then may interfere.

What brand/model system. Desktop with separate video or laptop with perhaps Optimus?

---

### Post by roadrash on 2018-11-27
If i remember right my probems started with 18.04 and even when trying to install ubuntu i had to use nomodeset or i got a crashed screen display. Then when i get to a desktop the resolution is so low i cant see the whole screen. I would have to use the tab key and enter key to select things i couldnt see on the screen.  Once i got ubuntu installed i could get a better resolution but videos would be stuttering without the nvidia driver. Its been a few years since ive got the nvidia driver to install on ubuntu or mint.  Hopefully if we can find out whats causing this i can enjoy using ubunto on my desktop again.  I will try 17.10 or 18.04 today but i'm sure 18.04 ive tried many times to install the nvidia driver on and failed.

Ive done it!!!!! but its not exactly a success. as the desktop is slow and laggy to use and videos are also slow and jerky probably worse than without the nvidia driver.
Anyway this is what I did to get the nvidia driver installed from a fresh install of Ubuntu 18.04.1 (bionic beaver). First I applied all updates.  Then from the desktop I installed lightdm and made it default, then installed Mate and once installed I logged out and back into the mate desktop. Then I installed bumblebee.  Then I rebooted to a recovery root terminal and installed the nvidia-340 driver and rebooted and it goes too a graphical; desktop.  Here is the output of inxi after the sccessful install

[QUOTE]System:    Host: jon-desktop Kernel: 4.15.0-39-generic x86_64 bits: 64
           Desktop: MATE 1.20.1  Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: N/A model: 4CoreDual-VSTA serial: N/A
           BIOS: American Megatrends v: P2.30 date: 02/26/2008
CPU:       Dual core Intel Core2 6400 (-MCP-) cache: 2048 KB
           clock speeds: max: 2049 MHz 1: 2049 MHz 2: 2049 MHz
Graphics:  Card: NVIDIA GF100 [GeForce GTX 480]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 1280x800@76.00hz
           OpenGL: renderer: N/A version: N/A
Audio:     Card-1 VIA VT8237A/VT8251 HDA Controller driver: snd_hda_intel
           Card-2 NVIDIA GF100 High Def. Audio Controller
           driver: snd_hda_intel
           Card-3 Hewlett-Packard driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-39-generic
Network:   Card: VIA VT6102/VT6103 [Rhine-II] driver: via-rhine
           IF: enp0s18 state: unknown speed: 100 Mbps duplex: full
           mac: <filter>
Drives:    HDD Total Size: 451.0GB (2.1% used)
           ID-1: /dev/sdb model: ST3200826A size: 200.0GB
           ID-2: /dev/sda model: Maxtor_7L250R0 size: 251.0GB
Partition: ID-1: / size: 135G used: 7.0G (6%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 2.15GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 45.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 179 Uptime: 4 min Memory: 537.3/1993.2MB
           Client: Shell (bash) inxi: 2.3.56 
[QUOTE]

After this I tried some othet things.  I tied the same with the nviida 390- driver and it failed.  I also tried differnt desktops and only mate & cinnamon worked although cinnamon crashed with a error.
Hopefully maybe we can work out why the 390 driver doen't work.  I am now going to try this in the latest Ubuntu 18.10 and see if it will work and then try again in Mint too especially Mate & cinnamon versions.

---

### Post by 23dornot23d on 2018-11-27
> 
**Graphics:  Card: NVIDIA GF100 [GeForce GTX 480]**
           Display Server: x11 (**X.Org 1.19.6** )
           drivers: **fbdev,nouveau** (unloaded: modesetting,vesa)
           Resolution: 1280x800@76.00hz
           OpenGL: renderer: N/A version: N/A


This from earlier on - looks like its in a VM .... for the renderer .... odd ..........

> 
Graphics:
  Device-1: NVIDIA GF100 [GeForce GTX 480] driver: N/A 
  Display: **server: X.Org 1.20.1 **driver:** fbdev,nouveau** 
  unloaded: modesetting,vesa resolution: 1280x800~76Hz 
  **OpenGL: renderer: llvmpipe (LLVM 7.0 128 bits) v: 3.3 Mesa 18.2.2** 


[https://www.geforce.com/hardware/desktop-gpus/geforce-gtx-480/specifications](https://www.geforce.com/hardware/desktop-gpus/geforce-gtx-480/specifications)

You probably do not need to install Bumblebee ...... but if it works ... its ok ....... it will say when loading if it recognizes the card as being optimus
or not ....... I use it because it allows me to switch between intel and nvidia ...... its mainly for power savings on laptops ........ but you have a desktop
machine - the only reason I said to load it is because it worked at sorting the kms ( kernel mode settings out ) ...... but as Oldfred said it may not be
needed and could cause another problem if it in fact is not altering the outcome of the display - 

> 
Feature Support:
4.2OpenGL
PCI-E 2.0 x16Bus Support
YesCertified for Windows 7
DirectX 11, 3D Vision, 3D Vision Surround, PhysX, CUDA, SLISupported Technologies
2-way, 3-waySLI Options[SUP]1[/SUP]




With the nvidia running - the computer should be reasonably fast looking at the specs above in the link ........ it runs CUDA too when working properly
which is something I have for Blender - which is good for 3d graphics rendering etc.

> 
After this I tried some othet things.  I tied the same with the nviida  390- driver and it failed.  I also tried differnt desktops and only mate  & cinnamon worked although cinnamon crashed with a error.
Hopefully maybe we can work out why the 390 driver doen't work.  I am  now going to try this in the latest Ubuntu 18.10 and see if it will work  and then try again in Mint too especially Mate & cinnamon versions.                 


We find all sorts of things out by trying different versions and setups .......... I always keep older versions as backups .... the installs are reasonably small not usually above 30gig a piece and the
boot loader allows me to select whichever I want - must admit over the years - some of the earlier ones actually run quite a lot faster on the Desktop itself - its when video is used and in Firefox for
You-Tube etc ....... I think Old Fred has multiple boot options too ..... what with newer computers and UEFI though it seems to be getting much more complex than it was before.

From Old Freds comment ....... did you check this out ?

> 
New systems have an UEFI system setting to turn on/off video card or  Intel video. Not sure if older BIOS had similar setting or not.

Or some old ones have Optimus Technology and Bumblebee was used. Two  switched video but one port. But newer nVidia drivers eliminated the  need for Bumblebee which bumblebee then may interfere.



[B]1 )
[/B]
Did you take a look at the BIOS too ........ was the Nvidia Card Selected in the BIOS ........ if there is a selection for it ........ to get to the BIOS you usually have to hold a key down at boot-up

here is a video of what it may look like - [https://www.youtube.com/watch?v=BtDkczrf5fI](https://www.youtube.com/watch?v=BtDkczrf5fI)
but do not go altering anything unless you are sure what you are doing ..... you can always exit without saving if you go into it for a look.

for my own machine its the <ESC> escape key ..... but you would have to check that out for your own machine ..... sometimes it flashes up really quickly as the machine boots up on the splash 
screen .........

Is there a good reason to want to use 18.10 .......... as **18.04 has a longer time on it before it needs changing again** ......... just thinking of all the trouble you may have again trying to sort out
the graphics.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

                                                                                    ===================================================Released-------------            End of Life

[TABLE]
[TR]
[TD="bgcolor: #762852"]Ubuntu 18.10[/TD]
[TD="bgcolor: #f1f1dd"][Cosmic Cuttlefish]("https://wiki.ubuntu.com/CosmicCuttlefish")[/TD]
[TD="bgcolor: #f1f1dd"] [Release Notes]("https://wiki.ubuntu.com/CosmicCuttlefish/ReleaseNotes")[/TD]
[TD="bgcolor: #f1f1dd"] [October 18, 2018]("https://lists.ubuntu.com/archives/ubuntu-announce/2018-October/000237.html")[/TD]
[TD="bgcolor: #f1f1dd"] [July 2019]("https://lists.ubuntu.com/archives/ubuntu-announce/2018-October/000237.html")[/TD]
[/TR]
[TR]
[TD="bgcolor: #762852"]Ubuntu **18.04.1 LTS**[/TD]
[TD="bgcolor: #f1f1dd"][Bionic Beaver]("https://wiki.ubuntu.com/BionicBeaver")[/TD]
[TD="bgcolor: #f1f1dd"] [Changes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/ChangeSummary/18.04.1")[/TD]
[TD="bgcolor: #f1f1dd"] [July 26, 2018]("https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000234.html")[/TD]
[TD="bgcolor: #f1f1dd"]  [April 2023]("https://lists.ubuntu.com/archives/ubuntu-announce/2018-April/000231.html")[/TD]
[/TR]
[TR]
[TD="bgcolor: #762852"]Ubuntu 18.04 LTS[/TD]
[TD="bgcolor: #f1f1dd"][Bionic Beaver]("https://wiki.ubuntu.com/BionicBeaver")[/TD]
[TD="bgcolor: #f1f1dd"] [Release Notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes")[/TD]
[TD="bgcolor: #f1f1dd"] [April 26, 2018]("https://lists.ubuntu.com/archives/ubuntu-announce/2018-April/000231.html")[/TD]
[TD="bgcolor: #f1f1dd"] [April 2023]("https://lists.ubuntu.com/archives/ubuntu-announce/2018-April/000231.html")[/TD]
[/TR]
[/TABLE]


Still need to sort this out ........ should say nvidia instead of nouveau .......... as far as I see on my own setup - also need opengl too .......
then you will be able to run 

**glxinfo**                              

To get some output saying it is using the nvidia card.

> 
drivers: **fbdev,nouveau** (unloaded: modesetting,vesa)
           Resolution: 1280x800@76.00hz
           **OpenGL: renderer: N/A version: N/A**                      


> 
Anyway this is what I did to get the nvidia driver installed from a  fresh install of Ubuntu 18.04.1 (bionic beaver). First I applied all  updates.  Then from the desktop I installed lightdm and made it default,  then installed Mate and once installed I logged out and back into the  mate desktop. Then I installed bumblebee.  Then I rebooted to a recovery  root terminal and installed the **nvidia-340 driver** 


In the **Mate Menu** - under - **Administration **..........

[B]2 )
[/B]
**Try nvidia-settings**

within the **mate desktop** ..........

Post a **screenshot** of what you have .......... if you would please ........

==============================================================

I have a strange feeling about this - that its not really finding and using the card at all ..... especially after going through
this that you pasted earlier ............

[https://paste.ubuntu.com/p/5XVggTBvbt/](https://paste.ubuntu.com/p/5XVggTBvbt/)

 no mention of the nvidia in it ........... 

Possible its switched off in the BIOS
Might not be seated quite down in its slot ( the graphics card )
or something else ......... but to go through all the drivers and not get it working yet is odd.

maybe the xorg.log file has some more clues as to what is happening.

[B]3 )
[/B]
Can you post this file to a pastebin please ........... if it is there ........
**/var/log/Xorg.0.log**
==================================================
or whatever Xorg log files you have ......... Xorg.1.log ...... Xorg.8.log
==================================================

Basically three things to do there - sorry for the long post - lot of thinking
about what we have so far and wanted to get it down in a thread.

Can take each thing separately and go through them ... just to be sure
as I would like to help you solve this problem - or at least give as much
information as possible - so someone else who is looking at it can work
out - if we are heading towards success or not !!!

---

### Post by roadrash on 2018-11-28
From what I have been reading online there are quite a few people who had the same problem of the 18.xx Ubuntu's being a bit slow & lagging mouse stalling & jerky, and generally unresponsive.  This is what I am getting with 18.10.  Today I have been trying other systems based on Ubuntu like Linux Mint and sticking just now with the Mate desktop (my prefered desktop anyway).  I yesterday installed Linux mint 18.1 Serena and when I used installed Bumblebee I got the Nvidia-340 driver to install but it would not install the Nvidia-390 driver.  I found out where the boot up fails using the Nvidia 390 driver and it gets stuck with a blank screen and with a flashing cursor in the top left corner of the screen and it a message you cant see about "waiting for a process to finish and waiting 43s or / none"  or something.  Its this process that is stopping the desktop from loading with the 390 driver but no info on what the process is.  I did a inxi on my install of Linux mint 18.1 and here arte the results of that which actually say "Nvidia failed" but it seems ok and is showing Nouveau driver not being used and the Nvida being used.


> System:    Host: jon-desktop Kernel: 4.4.0-139-generic x86_64 (64 bit)
           Desktop: MATE 1.16.2  Distro: Linux Mint 18.1 Serena
Machine:   Mobo: N/A model: 4CoreDual-VSTA
           Bios: American Megatrends v: P2.30 date: 02/26/2008
CPU:       Dual core Intel Core2 6400 (-MCP-) cache: 2048 KB 
           clock speeds: max: 2050 MHz 1: 2050 MHz 2: 2050 MHz
Graphics:  Card: NVIDIA GF100 [GeForce GTX 480]
           Display Server: X.Org 1.18.4 drivers: vesa,nouveau (unloaded: fbdev) FAILED: nvidia
           Resolution: 1024x768@0.00hz
           GLX Renderer: N/A GLX Version: N/A
Audio:     Card-1 VIA VT8237A/VT8251 HDA Controller driver: snd_hda_intel
           Card-2 NVIDIA GF100 High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-139-generic
Network:   Card: VIA VT6102/VT6103 [Rhine-II] driver: via-rhine
           IF: enp0s18 state: unknown speed: 100 Mbps duplex: full
           mac: <filter>
Drives:    HDD Total Size: 451.0GB (2.1% used)
           ID-1: /dev/sdb model: ST3200826A size: 200.0GB
           ID-2: /dev/sda model: Maxtor_7L250R0 size: 251.0GB
Partition: ID-1: / size: 136G used: 7.1G (6%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 2.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 158 Uptime: 4 min Memory: 384.0/1999.5MB
           Client: Shell (bash) inxi: 2.2.35 
jon@jon-desktop ~ $ sudo inxi -Fz
[sudo] password for jon: 
System:    Host: jon-desktop Kernel: 4.4.0-139-generic x86_64 (64 bit)
           Desktop: MATE 1.16.2  Distro: Linux Mint 18.1 Serena
Machine:   Mobo: N/A model: 4CoreDual-VSTA
           Bios: American Megatrends v: P2.30 date: 02/26/2008
CPU:       Dual core Intel Core2 6400 (-MCP-) cache: 2048 KB 
           clock speeds: max: 2050 MHz 1: 2050 MHz 2: 2050 MHz
Graphics:  Card: NVIDIA GF100 [GeForce GTX 480]
           Display Server: X.org 1.18.4 drivers: vesa,nouveau (unloaded: fbdev) FAILED: nvidia
           tty size: 80x24 Advanced Data: N/A for root
Audio:     Card-1 VIA VT8237A/VT8251 HDA Controller driver: snd_hda_intel
           Card-2 NVIDIA GF100 High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-139-generic
Network:   Card: VIA VT6102/VT6103 [Rhine-II] driver: via-rhine
           IF: enp0s18 state: unknown speed: 100 Mbps duplex: full
           mac: <filter>
Drives:    HDD Total Size: 451.0GB (2.1% used)
           ID-1: /dev/sdb model: ST3200826A size: 200.0GB
           ID-2: /dev/sda model: Maxtor_7L250R0 size: 251.0GB
Partition: ID-1: / size: 136G used: 7.1G (6%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 2.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 159 Uptime: 4 min Memory: 385.1/1999.5MB
           Client: Shell (sudo) inxi: 2.2.35 
jon@jon-desktop ~ $ 


I will be installing all versions one at a time progressively newer to see at what version it gets slow.

---

### Post by 23dornot23d on 2018-11-28
> 
I will be installing all versions one at a time progressively newer to see at what version it gets slow.                 


When you get the line with drivers in it to say nvidia ....... is being used ...... post back a inxi of it .........

> 
Graphics:  Card: NVIDIA GF100 [GeForce GTX 480]
           Display Server: X.Org 1.18.4 **drivers: vesa,nouveau** (unloaded: fbdev) **FAILED: nvidia**
           Resolution: 1024x768@0.00hz
           GLX Renderer: N/A GLX Version: N/A


If not ..... then refer back to my last post and see if there is anything you can answer any of the 3 things that I asked for that can confirm that
nvidia is being used ....... so far its not showing that we have used the nvidia card  ........ that is the first time
I have seen FAILED though ... as if there might be some other problem with that card.

vesa ..... is a basic setup like a fallback.

> 
vesa is an Xorg driver for generic VESA video cards. It can drive most VESA-compatible video cards, **but only makes use of the basic standard VESA core that is common to these cards**. The driver supports depths 8, 15 16 and 24.


[https://www.x.org/archive/current/doc/man/man4/vesa.4.xhtml](https://www.x.org/archive/current/doc/man/man4/vesa.4.xhtml)

---

### Post by roadrash on 2018-11-28
Here are the answers you asked earier before I gotr sidetracked with trying to find when the slowness started.

As it is now I have Ubunu 18.04.1 installed with all updates done with bumblebee installed with lighdm and mate desktop.  I have aslo got the Nvidia-304 driver working but the whole system is slow and takes a few secone to respond to anything i do and video's are very slow and jerky.  Otherwise its working fine. 

Here is a picture of my Nvidia settings and shows my drivers and updates(not that there is much to look at). I found out that the slowness and driver problems started with Ubuntu 18.04 and mint versions of 18.04.  

If there are any other ;pgs etc you want please ask.  for now here is the conetents of my Xorg.0.log:

```

[    45.701] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[    45.701] X Protocol Version 11, Revision 0
[    45.701] Build Operating System: Linux 4.4.0-138-generic x86_64 Ubuntu
[    45.701] Current Operating System: Linux jon-Inspiron-1545 4.15.0-39-generic #42-Ubuntu SMP Tue Oct 23 15:48:01 UTC 2018 x86_64
[    45.701] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-39-generic root=UUID=94e90b15-296d-432d-b132-f2d6d90485a9 ro quiet splash vt.handoff=1
[    45.701] Build Date: 25 October 2018  04:11:27PM
[    45.701] xorg-server 2:1.19.6-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    45.701] Current version of pixman: 0.34.0
[    45.701]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    45.701] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.702] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 28 19:19:59 2018
[    45.728] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.730] (==) No Layout section.  Using the first Screen section.
[    45.730] (==) No screen section available. Using defaults.
[    45.730] (**) |-->Screen "Default Screen Section" (0)
[    45.730] (**) |   |-->Monitor "<default monitor>"
[    45.731] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    45.731] (==) Automatically adding devices
[    45.731] (==) Automatically enabling devices
[    45.731] (==) Automatically adding GPU devices
[    45.731] (==) Automatically binding GPU devices
[    45.731] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    45.731] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.731]     Entry deleted from font path.
[    45.731] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    45.731]     Entry deleted from font path.
[    45.732] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.732]     Entry deleted from font path.
[    45.732] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    45.732]     Entry deleted from font path.
[    45.732] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.732]     Entry deleted from font path.
[    45.732] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    45.732] (==) ModulePath set to "/usr/lib/xorg/modules"
[    45.732] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.732] (II) Loader magic: 0x556f50b03020
[    45.732] (II) Module ABI versions:
[    45.732]     X.Org ANSI C Emulation: 0.4
[    45.732]     X.Org Video Driver: 23.0
[    45.732]     X.Org XInput driver : 24.1
[    45.732]     X.Org Server Extension : 10.0
[    45.734] (++) using VT number 7

[    45.734] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    45.735] (II) xfree86: Adding drm device (/dev/dri/card0)
[    45.752] (--) PCI:*(0:0:2:0) 8086:0166:1025:064b rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00002000/64, BIOS @ 0x????????/131072
[    45.752] (II) LoadModule: "glx"
[    45.753] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    46.377] (II) Module glx: vendor="X.Org Foundation"
[    46.378]     compiled for 1.19.6, module version = 1.0.0
[    46.378]     ABI class: X.Org Server Extension, version 10.0
[    46.378] (==) Matched modesetting as autoconfigured driver 0
[    46.378] (==) Matched fbdev as autoconfigured driver 1
[    46.378] (==) Matched vesa as autoconfigured driver 2
[    46.378] (==) Assigned the driver to the xf86ConfigLayout
[    46.378] (II) LoadModule: "modesetting"
[    46.378] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    46.378] (II) Module modesetting: vendor="X.Org Foundation"
[    46.378]     compiled for 1.19.6, module version = 1.19.6
[    46.378]     Module class: X.Org Video Driver
[    46.378]     ABI class: X.Org Video Driver, version 23.0
[    46.378] (II) LoadModule: "fbdev"
[    46.379] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    46.379] (II) Module fbdev: vendor="X.Org Foundation"
[    46.379]     compiled for 1.19.3, module version = 0.4.4
[    46.379]     Module class: X.Org Video Driver
[    46.379]     ABI class: X.Org Video Driver, version 23.0
[    46.379] (II) LoadModule: "vesa"
[    46.379] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    46.379] (II) Module vesa: vendor="X.Org Foundation"
[    46.379]     compiled for 1.19.3, module version = 2.3.4
[    46.379]     Module class: X.Org Video Driver
[    46.379]     ABI class: X.Org Video Driver, version 23.0
[    46.379] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    46.379] (II) FBDEV: driver for framebuffer: fbdev
[    46.379] (II) VESA: driver for VESA chipsets: vesa
[    46.399] (II) modeset(0): using drv /dev/dri/card0
[    46.399] (WW) Falling back to old probe method for fbdev
[    46.399] (II) Loading sub module "fbdevhw"
[    46.399] (II) LoadModule: "fbdevhw"
[    46.399] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    46.399] (II) Module fbdevhw: vendor="X.Org Foundation"
[    46.399]     compiled for 1.19.6, module version = 0.0.2
[    46.399]     ABI class: X.Org Video Driver, version 23.0
[    46.399] (WW) Falling back to old probe method for vesa
[    46.399] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    46.400] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[    46.400] (==) modeset(0): RGB weight 888
[    46.400] (==) modeset(0): Default visual is TrueColor
[    46.400] (II) Loading sub module "glamoregl"
[    46.400] (II) LoadModule: "glamoregl"
[    46.400] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    46.527] (II) Module glamoregl: vendor="X.Org Foundation"
[    46.527]     compiled for 1.19.6, module version = 1.0.0
[    46.527]     ABI class: X.Org ANSI C Emulation, version 0.4
[    46.527] (II) glamor: OpenGL accelerated X.org driver based.
[    46.844] (II) glamor: EGL version 1.4 (DRI2):
[    46.847] (II) modeset(0): glamor initialized
[    46.847] (II) modeset(0): Output LVDS-1 has no monitor section
[    46.852] (II) modeset(0): Output VGA-1 has no monitor section
[    46.862] (II) modeset(0): Output HDMI-1 has no monitor section
[    46.862] (II) modeset(0): Output DP-1 has no monitor section
[    46.862] (II) modeset(0): EDID for output LVDS-1
[    46.862] (II) modeset(0): Manufacturer: AUO  Model: 26ec  Serial#: 0
[    46.862] (II) modeset(0): Year: 2009  Week: 1
[    46.862] (II) modeset(0): EDID Version: 1.3
[    46.862] (II) modeset(0): Digital Display Input
[    46.862] (II) modeset(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    46.862] (II) modeset(0): Gamma: 2.20
[    46.863] (II) modeset(0): No DPMS capabilities specified
[    46.863] (II) modeset(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    46.863] (II) modeset(0): First detailed timing is preferred mode
[    46.863] (II) modeset(0): redX: 0.577 redY: 0.333   greenX: 0.333 greenY: 0.554
[    46.863] (II) modeset(0): blueX: 0.161 blueY: 0.144   whiteX: 0.313 whiteY: 0.329
[    46.863] (II) modeset(0): Manufacturer's mask: 0
[    46.863] (II) modeset(0): Supported detailed timing:
[    46.863] (II) modeset(0): clock: 71.8 MHz   Image Size:  344 x 193 mm
[    46.863] (II) modeset(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    46.863] (II) modeset(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 784 v_border: 0
[    46.863] (II) modeset(0): Unknown vendor-specific block f
[    46.863] (II) modeset(0):  AUO
[    46.863] (II) modeset(0):  B156XW02 V6
[    46.863] (II) modeset(0): EDID (in hex):
[    46.863] (II) modeset(0):     00ffffffffffff0006afec2600000000
[    46.863] (II) modeset(0):     01130103802213780ad7759355558d29
[    46.863] (II) modeset(0):     24505400000001010101010101010101
[    46.863] (II) modeset(0):     0101010101010c1c56a0500010303020
[    46.863] (II) modeset(0):     360058c1100000180000000f00000000
[    46.863] (II) modeset(0):     00000000000000000020000000fe0041
[    46.863] (II) modeset(0):     554f0a202020202020202020000000fe
[    46.863] (II) modeset(0):     004231353658573032205636200a0065
[    46.863] (II) modeset(0): Printing probed modes for output LVDS-1
[    46.864] (II) modeset(0): Modeline "1366x768"x60.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    46.864] (II) modeset(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    46.864] (II) modeset(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    46.864] (II) modeset(0): Modeline "1280x720"x120.0  156.12  1280 1376 1512 1744  720 721 724 746 doublescan -hsync +vsync (89.5 kHz d)
[    46.864] (II) modeset(0): Modeline "1280x720"x120.0  120.75  1280 1304 1320 1360  720 721 724 740 doublescan +hsync -vsync (88.8 kHz d)
[    46.864] (II) modeset(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz d)
[    46.864] (II) modeset(0): Modeline "1280x720"x59.7   63.75  1280 1328 1360 1440  720 723 728 741 +hsync -vsync (44.3 kHz d)
[    46.864] (II) modeset(0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    46.864] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    46.864] (II) modeset(0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    46.864] (II) modeset(0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    46.864] (II) modeset(0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    46.864] (II) modeset(0): Modeline "1024x576"x119.9   98.50  1024 1092 1200 1376  576 577 580 597 doublescan -hsync +vsync (71.6 kHz d)
[    46.864] (II) modeset(0): Modeline "1024x576"x119.9   78.38  1024 1048 1064 1104  576 577 580 592 doublescan +hsync -vsync (71.0 kHz d)
[    46.864] (II) modeset(0): Modeline "1024x576"x59.9   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync (35.9 kHz d)
[    46.864] (II) modeset(0): Modeline "1024x576"x59.8   42.00  1024 1072 1104 1184  576 579 584 593 +hsync -vsync (35.5 kHz d)
[    46.864] (II) modeset(0): Modeline "960x600"x119.9   96.62  960 1028 1128 1296  600 601 604 622 doublescan -hsync +vsync (74.6 kHz d)
[    46.864] (II) modeset(0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    46.864] (II) modeset(0): Modeline "960x540"x119.9   86.50  960 1024 1124 1288  540 541 544 560 doublescan -hsync +vsync (67.2 kHz d)
[    46.864] (II) modeset(0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    46.864] (II) modeset(0): Modeline "960x540"x59.6   40.75  960 992 1088 1216  540 543 548 562 -hsync +vsync (33.5 kHz d)
[    46.864] (II) modeset(0): Modeline "960x540"x59.8   37.25  960 1008 1040 1120  540 543 548 556 +hsync -vsync (33.3 kHz d)
[    46.864] (II) modeset(0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    46.864] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    46.864] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    46.864] (II) modeset(0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    46.864] (II) modeset(0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    46.864] (II) modeset(0): Modeline "864x486"x59.9   32.50  864 888 968 1072  486 489 494 506 -hsync +vsync (30.3 kHz d)
[    46.864] (II) modeset(0): Modeline "864x486"x59.6   30.50  864 912 944 1024  486 489 494 500 +hsync -vsync (29.8 kHz d)
[    46.864] (II) modeset(0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    46.864] (II) modeset(0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    46.864] (II) modeset(0): Modeline "800x450"x119.9   59.12  800 848 928 1056  450 451 454 467 doublescan -hsync +vsync (56.0 kHz d)
[    46.864] (II) modeset(0): Modeline "800x450"x119.6   48.75  800 824 840 880  450 451 454 463 doublescan +hsync -vsync (55.4 kHz d)
[    46.864] (II) modeset(0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    46.864] (II) modeset(0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    46.864] (II) modeset(0): Modeline "700x450"x119.9   51.75  700 740 812 924  450 451 456 467 doublescan -hsync +vsync (56.0 kHz d)
[    46.864] (II) modeset(0): Modeline "700x450"x119.8   43.25  700 724 740 780  450 451 456 463 doublescan +hsync -vsync (55.4 kHz d)
[    46.864] (II) modeset(0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    46.864] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    46.864] (II) modeset(0): Modeline "720x405"x59.5   22.50  720 744 808 896  405 408 413 422 -hsync +vsync (25.1 kHz d)
[    46.865] (II) modeset(0): Modeline "720x405"x59.0   21.75  720 768 800 880  405 408 413 419 +hsync -vsync (24.7 kHz d)
[    46.865] (II) modeset(0): Modeline "684x384"x119.8   42.62  684 720 788 892  384 385 390 399 doublescan -hsync +vsync (47.8 kHz d)
[    46.865] (II) modeset(0): Modeline "684x384"x119.7   36.12  684 708 724 764  384 385 390 395 doublescan +hsync -vsync (47.3 kHz d)
[    46.865] (II) modeset(0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    46.865] (II) modeset(0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    46.865] (II) modeset(0): Modeline "640x400"x119.8   41.75  640 676 740 840  400 401 404 415 doublescan -hsync +vsync (49.7 kHz d)
[    46.865] (II) modeset(0): Modeline "640x400"x120.0   35.50  640 664 680 720  400 401 404 411 doublescan +hsync -vsync (49.3 kHz d)
[    46.865] (II) modeset(0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    46.865] (II) modeset(0): Modeline "640x360"x119.7   37.25  640 672 736 832  360 361 364 374 doublescan -hsync +vsync (44.8 kHz d)
[    46.865] (II) modeset(0): Modeline "640x360"x119.7   31.88  640 664 680 720  360 361 364 370 doublescan +hsync -vsync (44.3 kHz d)
[    46.865] (II) modeset(0): Modeline "640x360"x59.8   18.00  640 664 720 800  360 363 368 376 -hsync +vsync (22.5 kHz d)
[    46.865] (II) modeset(0): Modeline "640x360"x59.3   17.75  640 688 720 800  360 363 368 374 +hsync -vsync (22.2 kHz d)
[    46.865] (II) modeset(0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    46.865] (II) modeset(0): Modeline "512x288"x120.0   23.25  512 532 580 648  288 289 292 299 doublescan -hsync +vsync (35.9 kHz d)
[    46.865] (II) modeset(0): Modeline "512x288"x119.8   21.00  512 536 552 592  288 289 292 296 doublescan +hsync -vsync (35.5 kHz d)
[    46.865] (II) modeset(0): Modeline "480x270"x119.3   20.38  480 496 544 608  270 271 274 281 doublescan -hsync +vsync (33.5 kHz d)
[    46.865] (II) modeset(0): Modeline "480x270"x119.6   18.62  480 504 520 560  270 271 274 278 doublescan +hsync -vsync (33.3 kHz d)
[    46.865] (II) modeset(0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    46.865] (II) modeset(0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    46.865] (II) modeset(0): Modeline "432x243"x119.8   16.25  432 444 484 536  243 244 247 253 doublescan -hsync +vsync (30.3 kHz d)
[    46.865] (II) modeset(0): Modeline "432x243"x119.1   15.25  432 456 472 512  243 244 247 250 doublescan +hsync -vsync (29.8 kHz d)
[    46.865] (II) modeset(0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    46.865] (II) modeset(0): Modeline "360x202"x119.0   11.25  360 372 404 448  202 204 206 211 doublescan -hsync +vsync (25.1 kHz d)
[    46.865] (II) modeset(0): Modeline "360x202"x118.3   10.88  360 384 400 440  202 204 206 209 doublescan +hsync -vsync (24.7 kHz d)
[    46.865] (II) modeset(0): Modeline "320x180"x119.7    9.00  320 332 360 400  180 181 184 188 doublescan -hsync +vsync (22.5 kHz d)
[    46.865] (II) modeset(0): Modeline "320x180"x118.6    8.88  320 344 360 400  180 181 184 187 doublescan +hsync -vsync (22.2 kHz d)
[    46.870] (II) modeset(0): EDID for output VGA-1
[    46.880] (II) modeset(0): EDID for output HDMI-1
[    46.880] (II) modeset(0): EDID for output DP-1
[    46.880] (II) modeset(0): Output LVDS-1 connected
[    46.880] (II) modeset(0): Output VGA-1 disconnected
[    46.880] (II) modeset(0): Output HDMI-1 disconnected
[    46.880] (II) modeset(0): Output DP-1 disconnected
[    46.880] (II) modeset(0): Using exact sizes for initial modes
[    46.880] (II) modeset(0): Output LVDS-1 using initial mode 1366x768 +0+0
[    46.881] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[    46.881] (==) modeset(0): DPI set to (96, 96)
[    46.881] (II) Loading sub module "fb"
[    46.881] (II) LoadModule: "fb"
[    46.881] (II) Loading /usr/lib/xorg/modules/libfb.so
[    46.882] (II) Module fb: vendor="X.Org Foundation"
[    46.882]     compiled for 1.19.6, module version = 1.0.0
[    46.882]     ABI class: X.Org ANSI C Emulation, version 0.4
[    46.882] (II) UnloadModule: "fbdev"
[    46.882] (II) Unloading fbdev
[    46.882] (II) UnloadSubModule: "fbdevhw"
[    46.882] (II) Unloading fbdevhw
[    46.882] (II) UnloadModule: "vesa"
[    46.882] (II) Unloading vesa
[    46.882] (==) Depth 24 pixmap format is 32 bpp
[    47.002] (==) modeset(0): Backing store enabled
[    47.002] (==) modeset(0): Silken mouse enabled
[    47.002] (II) modeset(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    47.032] (==) modeset(0): DPMS enabled
[    47.032] (II) modeset(0): [DRI2] Setup complete
[    47.032] (II) modeset(0): [DRI2]   DRI driver: i965
[    47.032] (II) modeset(0): [DRI2]   VDPAU driver: i965
[    47.032] (--) RandR disabled
[    47.054] (II) SELinux: Disabled on system
[    47.060] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    47.060] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    47.060] (II) AIGLX: enabled GLX_INTEL_swap_event
[    47.060] (II) AIGLX: enabled GLX_SGI_swap_control
[    47.060] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    47.060] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    47.060] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    47.060] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    47.061] (II) AIGLX: Loaded and initialized i965
[    47.061] (II) GLX: Initialized DRI2 GL provider for screen 0
[    47.062] (II) modeset(0): Damage tracking initialized
[    47.062] (II) modeset(0): Setting screen physical size to 361 x 203
[    47.161] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    47.161] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    47.161] (II) LoadModule: "libinput"
[    47.161] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    47.201] (II) Module libinput: vendor="X.Org Foundation"
[    47.201]     compiled for 1.19.6, module version = 0.27.1
[    47.201]     Module class: X.Org XInput Driver
[    47.201]     ABI class: X.Org XInput driver, version 24.1
[    47.201] (II) Using input driver 'libinput' for 'Power Button'
[    47.201] (**) Power Button: always reports core events
[    47.201] (**) Option "Device" "/dev/input/event3"
[    47.202] (**) Option "_source" "server/udev"
[    47.202] (II) event3  - Power Button: is tagged by udev as: Keyboard
[    47.202] (II) event3  - Power Button: device is a keyboard
[    47.202] (II) event3  - Power Button: device removed
[    47.216] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    47.216] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    47.216] (**) Option "xkb_model" "pc105"
[    47.216] (**) Option "xkb_layout" "gb"
[    47.240] (II) event3  - Power Button: is tagged by udev as: Keyboard
[    47.240] (II) event3  - Power Button: device is a keyboard
[    47.241] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    47.241] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    47.241] (II) Using input driver 'libinput' for 'Video Bus'
[    47.241] (**) Video Bus: always reports core events
[    47.241] (**) Option "Device" "/dev/input/event5"
[    47.241] (**) Option "_source" "server/udev"
[    47.242] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[    47.242] (II) event5  - Video Bus: device is a keyboard
[    47.242] (II) event5  - Video Bus: device removed
[    47.268] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event5"
[    47.268] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    47.268] (**) Option "xkb_model" "pc105"
[    47.268] (**) Option "xkb_layout" "gb"
[    47.269] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[    47.269] (II) event5  - Video Bus: device is a keyboard
[    47.270] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    47.270] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    47.270] (II) Using input driver 'libinput' for 'Power Button'
[    47.270] (**) Power Button: always reports core events
[    47.270] (**) Option "Device" "/dev/input/event0"
[    47.270] (**) Option "_source" "server/udev"
[    47.271] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    47.271] (II) event0  - Power Button: device is a keyboard
[    47.271] (II) event0  - Power Button: device removed
[    47.292] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    47.292] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    47.292] (**) Option "xkb_model" "pc105"
[    47.292] (**) Option "xkb_layout" "gb"
[    47.293] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    47.293] (II) event0  - Power Button: device is a keyboard
[    47.294] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    47.294] (II) No input driver specified, ignoring this device.
[    47.294] (II) This device may have been added with another device file.
[    47.295] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    47.295] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[    47.295] (II) Using input driver 'libinput' for 'Sleep Button'
[    47.295] (**) Sleep Button: always reports core events
[    47.295] (**) Option "Device" "/dev/input/event2"
[    47.295] (**) Option "_source" "server/udev"
[    47.296] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[    47.296] (II) event2  - Sleep Button: device is a keyboard
[    47.296] (II) event2  - Sleep Button: device removed
[    47.320] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input2/event2"
[    47.320] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    47.320] (**) Option "xkb_model" "pc105"
[    47.320] (**) Option "xkb_layout" "gb"
[    47.321] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[    47.321] (II) event2  - Sleep Button: device is a keyboard
[    47.323] (II) config/udev: Adding input device HD WebCam: HD WebCam (/dev/input/event11)
[    47.323] (**) HD WebCam: HD WebCam: Applying InputClass "libinput keyboard catchall"
[    47.323] (II) Using input driver 'libinput' for 'HD WebCam: HD WebCam'
[    47.323] (**) HD WebCam: HD WebCam: always reports core events
[    47.323] (**) Option "Device" "/dev/input/event11"
[    47.323] (**) Option "_source" "server/udev"
[    47.324] (II) event11 - HD WebCam: HD WebCam: is tagged by udev as: Keyboard
[    47.324] (II) event11 - HD WebCam: HD WebCam: device is a keyboard
[    47.324] (II) event11 - HD WebCam: HD WebCam: device removed
[    47.364] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input12/event11"
[    47.364] (II) XINPUT: Adding extended input device "HD WebCam: HD WebCam" (type: KEYBOARD, id 10)
[    47.364] (**) Option "xkb_model" "pc105"
[    47.364] (**) Option "xkb_layout" "gb"
[    47.365] (II) event11 - HD WebCam: HD WebCam: is tagged by udev as: Keyboard
[    47.365] (II) event11 - HD WebCam: HD WebCam: device is a keyboard
[    47.366] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    47.366] (II) No input driver specified, ignoring this device.
[    47.366] (II) This device may have been added with another device file.
[    47.367] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event10)
[    47.367] (II) No input driver specified, ignoring this device.
[    47.367] (II) This device may have been added with another device file.
[    47.368] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[    47.368] (II) No input driver specified, ignoring this device.
[    47.368] (II) This device may have been added with another device file.
[    47.369] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    47.369] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    47.369] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    47.369] (**) AT Translated Set 2 keyboard: always reports core events
[    47.369] (**) Option "Device" "/dev/input/event4"
[    47.369] (**) Option "_source" "server/udev"
[    47.369] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    47.369] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[    47.369] (II) event4  - AT Translated Set 2 keyboard: device removed
[    47.392] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    47.392] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    47.392] (**) Option "xkb_model" "pc105"
[    47.392] (**) Option "xkb_layout" "gb"
[    47.393] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    47.393] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[    47.394] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    47.394] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[    47.394] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    47.394] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    47.394] (II) LoadModule: "synaptics"
[    47.394] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    47.395] (II) Module synaptics: vendor="X.Org Foundation"
[    47.395]     compiled for 1.19.3, module version = 1.9.0
[    47.395]     Module class: X.Org XInput Driver
[    47.395]     ABI class: X.Org XInput driver, version 24.1
[    47.395] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    47.395] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    47.395] (**) Option "Device" "/dev/input/event6"
[    47.432] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    47.432] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5774 (res 56)
[    47.432] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5022 (res 105)
[    47.432] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    47.432] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    47.432] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    47.432] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    47.432] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    47.432] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    47.472] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    47.472] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    47.472] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    47.472] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    47.472] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[    47.472] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    47.472] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    47.472] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    47.472] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    47.472] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    47.473] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    47.473] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    47.477] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event7)
[    47.477] (**) Acer WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    47.477] (II) Using input driver 'libinput' for 'Acer WMI hotkeys'
[    47.477] (**) Acer WMI hotkeys: always reports core events
[    47.477] (**) Option "Device" "/dev/input/event7"
[    47.478] (**) Option "_source" "server/udev"
[    47.478] (II) event7  - Acer WMI hotkeys: is tagged by udev as: Keyboard
[    47.478] (II) event7  - Acer WMI hotkeys: device is a keyboard
[    47.478] (II) event7  - Acer WMI hotkeys: device removed
[    47.500] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[    47.500] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[    47.500] (**) Option "xkb_model" "pc105"
[    47.500] (**) Option "xkb_layout" "gb"
[    47.501] (II) event7  - Acer WMI hotkeys: is tagged by udev as: Keyboard
[    47.501] (II) event7  - Acer WMI hotkeys: device is a keyboard
[    52.726] (II) modeset(0): EDID vendor "AUO", prod id 9964
[    52.726] (II) modeset(0): Printing DDC gathered Modelines:
[    52.726] (II) modeset(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    52.740] (II) modeset(0): EDID vendor "AUO", prod id 9964
[    52.740] (II) modeset(0): Printing DDC gathered Modelines:
[    52.740] (II) modeset(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    52.756] (II) modeset(0): EDID vendor "AUO", prod id 9964
[    52.756] (II) modeset(0): Printing DDC gathered Modelines:
[    52.756] (II) modeset(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    52.772] (II) modeset(0): EDID vendor "AUO", prod id 9964
[    52.772] (II) modeset(0): Printing DDC gathered Modelines:
[    52.772] (II) modeset(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    55.339] (II) modeset(0): EDID vendor "AUO", prod id 9964
[    55.340] (II) modeset(0): Printing DDC gathered Modelines:
[    55.340] (II) modeset(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)

```

Sorry gave you the wrong picture of the nvidia driver installed.  Also you might be interested in the massive load on my processor at idle.  It switches between cores and is mosly around 90%+.

---

### Post by oldfred on 2018-11-28
Please use code tags with longer text or terminal output. Easy to add with Forum's Advanced editor and # icon.

Post this to see nVidia and kernel:
       dkms status 

You are showing 340, not 304 nVidia. If you had 304, it probably would not work as 304 is for very old nVidia cards, and is not in repository for newest versions of Ubuntu.
Best to use recommended version, normally.

---

### Post by CatKiller on 2018-11-28
There's nothing in that log that shows you're using the nvidia driver. In fact, it says that you're using the vesa driver, which would perform appallingly, and would give you high cpu load.

---

### Post by roadrash on 2018-11-28
> **oldfred said:**
> Please use code tags with longer text or terminal output. Easy to add with Forum's Advanced editor and # icon.

Post this to see nVidia and kernel:
       dkms status 

You are showing 340, not 304 nVidia. If you had 304, it probably would not work as 304 is for very old nVidia cards, and is not in repository for newest versions of Ubuntu.
Best to use recommended version, normally.

It was the 340 driver that i installed.  I did try the reccomended 384 driver and it failed with the usual black screen and flashing cursor in top left corner wish I found out was a error that couldn't be seen saying this
;  [***] A start job is running for hold until process finishes up (29s / no limit).  I dont usually see the text just the falshing cusor.  If we could sort out whatever this start job/process is thats stalled I might be able to get to a graphical display with the  384 & 390 drivers.

> **CatKiller said:**
> There's nothing in that log that shows you're using the nvidia driver. In fact, it says that you're using the vesa driver, which would perform appallingly, and would give you high cpu load.

It shows I have the Nvidia driver installed though so how do I make it use it?

---

### Post by oldfred on 2018-11-28
The dkms status command posted above will show if installed as it must be part of kernel.

When system gets slow run this command and see what process or processes are running and using most of system
top

---

### Post by CatKiller on 2018-11-28
> **roadrash said:**
> My desktop has a Nvidia GTX-480 graphics card

Disable your integrated graphics in your BIOS.

Don't install Bumblebee.

Don't use Wayland.

---

### Post by 23dornot23d on 2018-11-28
Yes that is showing that you have selected the driver ..... and on the screenshot it says using the proprietary driver ........

[https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818](https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818)

The inxi log from earlier on shows that it knows what card you have too ........ but the last part of the task is to show that
the card is actually working properly ........ and as said ..... bumblebee does not need using in your case.

Your using Lightdm - so wayland is not being used ....... its not mentioned in the logs you have posted so far.

The driver it seems to be using is in that log though for the i965

> 
[    47.032] (==) modeset(0): DPMS enabled
[    47.032] (II) modeset(0): [DRI2] Setup complete
[    47.032] (II) modeset(0): [DRI2]   DRI driver: i965
[    47.032] (II) modeset(0): [DRI2]   VDPAU driver: i965
[    47.032] (--) RandR disabled
[    47.054] (II) SELinux: Disabled on system
[    47.060] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    47.060] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    47.060] (II) AIGLX: enabled GLX_INTEL_swap_event
[    47.060] (II) AIGLX: enabled GLX_SGI_swap_control
[    47.060] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    47.060] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    47.060] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    47.060] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    47.061] (II) AIGLX: Loaded and initialized i965



As said ......... by catkiller

> 
Disable your integrated graphics in your BIOS. ( I posted a video of this earlier ) [https://www.youtube.com/watch?v=BtDkczrf5fI](https://www.youtube.com/watch?v=BtDkczrf5fI)

Don't install Bumblebee. ( yep we do not need this - as its for powersaving on laptops )

Don't use Wayland.                 ( if lightdm is being used - then wayland is not - its not showing in your pastebin )

post this too if you would please .... as Old Fred asked for it to show what is loaded in with your latest setup.

$ **dkms status**



I mentioned this as did Fred too ....... and now Catkiller ....... we probably have all come to the same conclusion ..... that the nvidia card is not being used yet ........

Although the driver may show up as being installed and the computer readout shows which card you have installed ........ ( probably picks the information up off a chip in the graphics card )

It still does not seem to be using it - for whatever reason ..........

> 
[B]1 )
[/B]
Did you take a look at the BIOS too ........ was the Nvidia Card  Selected in the BIOS ........ if there is a selection for it ........ to  get to the BIOS you usually have to hold a key down at boot-up

here is a video of what it may look like - [https://www.youtube.com/watch?v=BtDkczrf5fI](https://www.youtube.com/watch?v=BtDkczrf5fI)
but do not go altering anything unless you are sure what you are doing  ..... you can always exit without saving if you go into it for a look.


I should have said to take a photo of what it shows for the graphics settings ......... in the BIOS.

and post it back ........... please ......

---

### Post by Bashing-om on 2018-11-28
roadrash; 23dornot23d ...

At the risk of muddying the waters even more.

I bet in the output of:
```

/var/log/gpu-manager.log

```
there is "Error: can't access /sys/bus/pci/devices/0000:06:00.0/driver
can't access /run/u-d-c-nvidia-was-loaded file" - or similar as the PCI will differ .

```

sudo lshw -C display 

```
will show that the kernel has in deed loaded the proprietary driver.

whereas the /var/log/Xorg.0.log file will show the GUI loading the fall back driver.

Now I also anticipate that the Xorg.0.log shows - ModulePath set to "/usr/lib/xorg/modules" -
and we look  for the directive there:
```

ls -al /usr/lib/xorg/modules
ls -al /usr/lib/xorg/modules/drivers/

```
and there is no  nvidia_drv.so file.

If all the above is true .. I am stuck also in how to properly load up the Nvidia driver.
Been going around and around with this issue for a spell now .

[INDENT][INDENT]one of those deep times
[/INDENT][/INDENT]

---

### Post by 23dornot23d on 2018-11-28
Really need to know that the **Nvidia card is being used by the BIOS** ........ 

if its not ...... then its never going to pick up.

These will be interesting to see though - cheers @Bashing-Om

> 

[B]leafpad /var/log/gpu-manager.log

[/B][B]sudo lshw -C display

ls -al /usr/lib/xorg/modules

ls -al /usr/lib/xorg/modules/drivers/

[/B]=======================================================================================

post this too if you would please .... as Old Fred asked for it to show what is loaded in with your latest setup.[B]

[B]dkms status
[/B] [/B]


if it is already set in the BIOS ....... then there may be a problem with the card itself - but I am hoping not - as no error messages have shown up to say
that there are other than it Failed to load nvidia driver when you used mint - the only messages so far are telling us what drivers are being used and the fact the Mate screenshot which shows a proprietary driver is in use
which gives hope - **other than that the card was not being used as the CPU usage was so high** - which did not look good or normal if the Nvidia card was in use the CPU usage should be low.

[https://ubuntuforums.org/attachment.php?attachmentid=281812&d=1543434884](https://ubuntuforums.org/attachment.php?attachmentid=281812&d=1543434884)

Bumblebee may have blacklisted the Nvidia Card as it uses switching ...... so it may be worth doing the two commands below once
we have as much information as needed while we still have a nice screen to work from ......

really need the **BIOS set  for Nvidia** if its not already set before doing this though as we may be  back to working from a terminal again

it should be set to bus .....** PCI-E** 2.0 x16 in the BIOS ...... so its a **PCI**-E card first ......... in the listing in BIOS.

From the specs of the Nvidia GTX 480 here [https://www.geforce.com/hardware/desktop-gpus/geforce-gtx-480/specifications](https://www.geforce.com/hardware/desktop-gpus/geforce-gtx-480/specifications)

Then once the BIOS is sorted and we know its definitely using the Nvidia Card ....... then ......

[B]sudo apt remove bumblebee
sudo apt remove bbswitch

[/B]Then see if we can still get to a display ..... maybe the Nvidia card will go into use once its set in the BIOS and bumblebee,bbswitch removed - then work ok.

As this screenshot informs us that the 340 driver is already in use ....... but as yet the card is not getting the instructions from it - turning it on in the BIOS
may resolve this issue.

[https://ubuntuforums.org/attachment....0&d=1543434818]("https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818")

---

### Post by roadrash on 2018-11-29
Sorry for not addressing all your requests so I will do my best to nswer them all now but my pc is running a bit like a old pentium 75 running windows with very little ram.  I appreciate greatly all your efforts to reolve this for me.

The output of dkms as requested ted by Old Fred:

> bbswitch, 0.8, 4.15.0-39-generic, x86_64: installed
nvidia-340, 340.107, 4.15.0-39-generic, x86_64: installed

**Did you take a look at the BIOS too** - Yes i have the PCIE set as primary video source.

**At the risk of muddying the waters even more, I bet in the output of "/var/log/gpu-manager.log" there is a error**

> log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-39-generic/updates/dkms
Found nvidia module: nvidia.ko
Looking for amdgpu modules in /lib/modules/4.15.0-39-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? yes
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:6c0
BusID "PCI:2@0:0:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:02:00.0/driver
The device is not bound to any driver.
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

**will show that the kernel has in deed loaded the proprietary driver.**

>   *-display UNCLAIMED       
       description: VGA compatible controller
       product: GF100 [GeForce GTX 480]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f4000000-f5ffffff memory:d0000000-d7ffffff memory:d8000000-dbffffff ioport:cc00(size=128) memory:c0000-dffff

**whereas the /var/log/Xorg.0.log file will show the GUI loading the fall back driver.**

[https://pastebin.com/embed_js/k19Fj4iR]("https://pastebin.com/embed_js/k19Fj4iR")

[B]Now I also anticipate that the Xorg.0.log shows - ModulePath set to "/usr/lib/xorg/modules" -
and we look for the directive there:[/B]

> ls -al /usr/lib/xorg/modules
total 900
drwxr-xr-x 5 root root   4096 Nov 28 17:23 .
drwxr-xr-x 3 root root   4096 Nov 28 17:23 ..
drwxr-xr-x 2 root root   4096 Nov 28 17:23 drivers
drwxr-xr-x 2 root root   4096 Nov 28 17:23 extensions
drwxr-xr-x 2 root root   4096 Jul 25 04:08 input
-rw-r--r-- 1 root root  92848 Oct 25 16:18 libexa.so
-rw-r--r-- 1 root root  18696 Oct 25 16:18 libfbdevhw.so
-rw-r--r-- 1 root root 138032 Oct 25 16:18 libfb.so
-rw-r--r-- 1 root root 208888 Oct 25 16:18 libglamoregl.so
-rw-r--r-- 1 root root 146088 Oct 25 16:18 libint10.so
-rw-r--r-- 1 root root  10376 Oct 25 16:18 libshadowfb.so
-rw-r--r-- 1 root root  35016 Oct 25 16:18 libshadow.so
-rw-r--r-- 1 root root  27024 Oct 25 16:18 libvbe.so
-rw-r--r-- 1 root root  31784 Oct 25 16:18 libvgahw.so
-rw-r--r-- 1 root root 178960 Oct 25 16:18 libwfb.so
======================
> ls -al /usr/lib/xorg/modules/drivers/
total 3028
drwxr-xr-x 2 root root    4096 Nov 28 17:23 .
drwxr-xr-x 5 root root    4096 Nov 28 17:23 ..
-rw-r--r-- 1 root root  144352 Mar 20  2018 amdgpu_drv.so
-rw-r--r-- 1 root root   10408 Mar 20  2018 ati_drv.so
-rw-r--r-- 1 root root   23624 Mar  9  2017 fbdev_drv.so
-rw-r--r-- 1 root root 1703208 Jan 17  2018 intel_drv.so
-rw-r--r-- 1 root root   90360 Oct 25 16:18 modesetting_drv.so
-rw-r--r-- 1 root root  217104 Jun 21  2017 nouveau_drv.so
-rw-r--r-- 1 root root  180912 Mar  9  2017 qxl_drv.so
-rw-r--r-- 1 root root  501920 Mar 20  2018 radeon_drv.so
-rw-r--r-- 1 root root   27760 Mar  9  2017 vesa_drv.so
-rw-r--r-- 1 root root  170008 Mar  9  2017 vmware_drv.so

---

### Post by CatKiller on 2018-11-29
> **roadrash said:**
> **Did you take a look at the BIOS too** - Yes i have the PCIE set as primary video source.

You'll also want to look for the setting to disable the integrated graphics. What the option is called will vary by motherboard, but it will be something like "initialise iGPU." You'll want to turn that off, so that you are only using your graphics card and there are no other options to confuse the configuration.

---

### Post by 23dornot23d on 2018-11-29
> 
Looking for nvidia modules in /lib/modules/4.15.0-39-generic/updates/dkms
**Found nvidia module: nvidia.ko**

[B]Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? yes
[/B]
**Is nvidia kernel module available? yes**

Error: can't access /sys/bus/pci/devices/0000:02:00.0/driver
The device is not bound to any driver.
Error : Failed to open /dev/dri



The nvidia card is blacklisted somewhere ....... possibly in bumblebee .......

> 
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do                      



As it is not needed ...... looking at this ,,,,, single card ......

So you can remove bumblebee and bbswitch as it is doing nothing - other than maybe possibly now blacklisting the nvidia card - which we will see after
removing it ...... a conf file exists in /etc/bumblebee/bumblebee.conf ...... but instead of editing this we might as well remove it completely by getting
rid of bumblebee now.

if it is no longer blacklisted we are ok ....... if not after doing the below then it is something else.

**sudo apt remove bumblebee**
[B]sudo apt remove bbswitch

[/B]> 
bbswitch, 0.8, 4.15.0-39-generic, x86_64: installed[B]
nvidia-340, 340.107, 4.15.0-39-generic, x86_64: installed                      

[/B]Then to ensure the nvidia driver is being used ..... go back to **additional drivers** and ensure that the **nvidia 340** is still in use.
[https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818](https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818)
removing bumblebee should not change the driver - but this is just to be sure .......


Ok just seen CatKiller as asked for one more thing to check - do that on reboot .......  sorry - you have to reboot to do this.

> 
You'll also want to look for the setting to disable the integrated  graphics. What the option is called will vary by motherboard, but it  will be something like "initialise iGPU." You'll want to turn that off,  so that you are only using your graphics card and there are no other  options to confuse the configuration.                 




...... hopefully you will see nvidia is not blacklisted - if it is - then its blacklisted somewhere else ........ which someone else may know where ?
possibly in /etc/modprobe.d/blacklist.conf

---

### Post by CatKiller on 2018-11-29
> **23dornot23d said:**
> 
...... hopefully you will see nvidia is not blacklisted - if it is - then its blacklisted somewhere else ........ which someone else may know where ?

Without Bumblebee installed, and without the integrated graphics being available, the Nvidia install scripts should add the entries to load the nvidia module and blacklist the others. It isn't generally something we'd have to do manually.

---

### Post by Bashing-om on 2018-11-29
23dornot23d' Hey hey ...

Pardon me if I am intruding on the thought process, but:
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)
relates that nvidia recommends the 390 version driver for this cad . I do not know that the 340 has the capability (??).
All I can see is a single Nvidia card installed in this system, so yes. agreed  .. clear out BumbleBee and get this system cleaned up .. For sure find out where nvidia is blacklisted ! Once all purged and clean I do suggest to have the system choose the driver to install -> '  sudo ubuntu-drivers autoinstall ' .

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

on a second thought - get the system cleaned up and check that all nvidia stuff is removed.
```

ls -al /lib/modules/4.18.0-11-generic/updates/dkms
ls -al /usr/lib/xorg/modules/drivers
ls -al /usr/lib/x86_64-linux-gnu/nvidia/xorg
ls -al /usr/share/X11/xorg.conf.d
ls /lib/modprobe.d |grep nvidia
lsmod | grep nvidia
ls -al /dev/nvidia*

```
as we are trying to understand the why of nvidia driver's fail to load.
Get it all clean and then see what happens .

we can do that :)

---

### Post by roadrash on 2018-11-29
This motherboard does not have any onboard graphics just AGP and PCI/e slots so cant disable them.

I did as you said and removed bumblebeen.  I couldn't remove bbswitch because it says its not installed.
I checked the driver is still installed and it is, so I rebooted.
Just as in the past before I used bumblebee it stops just after the login text comes up and goes to a black screen with the little flashing cursor in the stop left corner of the screen which I found out was a message " **[***] A start job is running for hold until process finishes up (29s / no limit)** .  I dont know what is delaying this but it doent get past this message without bumblebee.

---

### Post by 23dornot23d on 2018-11-29
[B]I really do dislike seeing this message displayed

[/B]> 
[***] A start job is running for hold until process finishes up (29s / no limit)
[B]

Can anyone tell me why a developer would give that as a message ........ just keep waiting ..... your on hold .....

The process is *** - the developer cannot tell you - why - who knows ............



[/B]Yes - I think bbswitch will have probably gone when uninstalling bumblebee ......
you can check with the command you used earlier that Old Fred posted

**[B]dkms status**[/B]

You can try this - but I have a feeling there is something else wrong with the card itself ........ it could be minor but its
stopping us getting any further unless as Bashing Om says ......... with this command ......... it will upgrade to the 390.87
possibly .......... lets hope for the best.[B]


sudo ubuntu-drivers autoinstall[/B]

---

### Post by CatKiller on 2018-11-29
> **roadrash said:**
> This motherboard does not have any onboard graphics just AGP and PCI/e slots so cant disable them.

Intel processors have included a GPU since about the Sandy Bridge era.

---

### Post by roadrash on 2018-11-29
I was wondering would there be a boot log with details of where it stalled??

> **CatKiller said:**
> Intel processors have included a GPU since about the Sandy Bridge era.

Check the specs its a ASrock 4 core dual VSTA.

---

### Post by Bashing-om on 2018-11-29
> **roadrash said:**
> I was wondering would there be a boot log with details of where it stalled??

```

journalctl -b -0
```
shows messages from the current boot

[INDENT][INDENT]it's a start
[/INDENT][/INDENT]

---

### Post by roadrash on 2018-11-29
> **Bashing-om said:**
> ```

journalctl -b -0
```
shows messages from the current boot

[INDENT][INDENT]it's a start
[/INDENT][/INDENT]

I will need to show the previous boot log beacuse I will have to boot to the recovery console root terminal to get the log and I dont want the recovery consoles boot log.  I cant run in graphical environemnt now bumblebee has been removed.

---

### Post by Bashing-om on 2018-11-29
roadrash; Well ----

You will need to enable persistent logging to track old boot files:
see: [https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs](https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by roadrash on 2018-11-29
Just had a idea.  I can boot with a live dvd and access the log with that cant I?   What log do I need to access in /Var/logs

Here are some logs taken after a crash on boot up with the nvida driver installed and bumblebee removed:

[B}First the boot log[/B]

[https://pastebin.com/embed_js/in2MDBJV]("https://pastebin.com/embed_js/in2MDBJV")

**2nd xorg.0.log**
[https://pastebin.com/embed_js/sd2XX8pm]("https://pastebin.com/embed_js/sd2XX8pm")

**and finaly xorg.1.log**

[https://pastebin.com/embed_js/FnKJss63]("https://pastebin.com/embed_js/FnKJss63")

---

### Post by 23dornot23d on 2018-11-29
> 
[  7339.782] (EE) NVIDIA(GPU-0): The NVIDIA kernel module does not appear to be receiving
[  7339.782] (EE) NVIDIA(GPU-0):     interrupts generated by the NVIDIA GPU at PCI:2:0:0. 
[  7339.783] (EE) NVIDIA(GPU-0):     Please see Chapter 8: Common Problems in the README for
[  7339.783] (EE) NVIDIA(GPU-0):     additional information.
[  7339.783] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA graphics device!
[  7339.783] (EE) NVIDIA(0): Failing initialization of X screen 0
[  7339.783] (II) UnloadModule: "nvidia"
[  7339.783] (II) UnloadSubModule: "wfb"
[  7339.783] (II) UnloadSubModule: "fb"
[  7339.783] (EE) Screen(s) found, but none have a usable configuration.
[  7339.783] (EE) 
Fatal server error:
[  7339.783] (EE) no screens found(EE) 
[  7339.783] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  7339.783] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  7339.783] (EE) 
[  7340.077] (EE) Server terminated with error (1). Closing log file.


Still not talking to the graphics card ........ by the looks ..... of the above ....... maybe someone else understands why ?

I do not understand the other log with Systemd ....... have tried to look at my own log and it means nothing ........

Would be interesting if it said something like ------ >>> using nvidia driver 390.87 ....... now and its still not communicating with the graphics card

Instead it just says NVIDIA .......

> 
[  7339.782] (EE) NVIDIA(GPU-0): **The NVIDIA kernel module does not appear to be receiving**
[  7339.782] (EE) NVIDIA(GPU-0):     **interrupts** generated by the NVIDIA GPU at PCI:2:0:0. 
[  7339.783] (EE) NVIDIA(GPU-0): **    Please see Chapter 8: Common Problems in the README **for   *( what README - where is it ? )
[  7339.783] (EE) NVIDIA(GPU-0):     additional information.
[  7339.783] (EE) NVIDIA(GPU-0): **Failed to initialize the NVIDIA graphics device! ......... ***( Yep - Tell us something we do not know ) like why !!!


Sorry I cannot help anymore ..... with this ..... the developers and the Systemd creators should be able to give information as to how and where to look for clues.

I tried with my own system using the journal ....... reading binary files and not easily being able to search them ....... seems a great idea if we are to make it impossible to find things.
Especially once you have no screen to work with ....... how do you search them and cut and paste any errors from them .......

The file name on mine is .............. 

base@base-K53SV:/var/log/journal$ ls
a4c1ef66793547858edcca867235194b

and doing what it explains in the documentation gives this back

base@base-K53SV:/var/log/journal$ journalctl -b a4c1ef66793547858edcca867235194b
Journal file /var/log/journal/a4c1ef66793547858edcca867235194b/system@00057a15e851463e-b2463febfee66d2a.journal~ is truncated, ignoring file.
Data from the specified boot (a4c1ef66793547858edcca867235194b) is not available: No such boot ID in journal

It gets even better when using their own examples .....

base@base-K53SV:~$ journalctl --since 09:00 --until "1 hour ago"

**--since= must be before --until=.**

I think you will find since is before until ..... computer ...... systemd ...... what are you telling me here ... another useless message back from it.

Found a command that works ....... note this down

**journalctl --boot**

From my own system - I get to see this - which I have never seen before

> 
nov. 29 23:15:14 base-K53SV kernel: nvidia: loading out-of-tree module taints kernel.
nov. 29 23:15:14 base-K53SV kernel: nvidia: module license 'NVIDIA' taints kernel.
nov. 29 23:15:14 base-K53SV kernel: Disabling lock debugging due to kernel taint
nov. 29 23:15:14 base-K53SV kernel: nvidia: module verification failed: signature and/or required key missing - tainting kernel
nov. 29 23:15:14 base-K53SV kernel: nvidia-nvlink: Nvlink Core is being initialized, major device number 238
nov. 29 23:15:14 base-K53SV kernel: nvidia 0000:01:00.0: enabling device (0000 -> 0003)
nov. 29 23:15:14 base-K53SV kernel: nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=none
nov. 29 23:15:14 base-K53SV kernel: NVRM: loading NVIDIA UNIX x86_64 Kernel Module  390.87  Tue Aug 21 12:33:05 PDT 2018 (using threaded interrupts)


Yet mine seems to be working ...... but the log is giving me doubts about how well its working ...........

[https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs](https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs)

---

### Post by CatKiller on 2018-11-29
> **23dornot23d said:**
> what README - where is it ?

[This one](http://us.download.nvidia.com/XFree86/Linux-x86_64/390.87/README/commonproblems.html).

---

### Post by 23dornot23d on 2018-11-29
Thanks CatKiller ......... for the link .........

[http://us.download.nvidia.com/XFree86/Linux-x86_64/390.87/README/commonproblems.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/390.87/README/commonproblems.html)

> 
This can be caused by a variety of problems, such as PCI IRQ routing errors, I/O APIC problems, conflicts with other devices sharing the IRQ (or their drivers), or MSI compatibility problems.
 If possible, configure your system such that your graphics card does not share its IRQ with other devices (**try moving the graphics card to another slot if applicable**, **unload/disable the driver(s) for the device(s) sharing the card's IRQ,** or remove/disable the device(s)).




only one slot for the graphics card though - so it cannot be moved ....... 

[https://soggi.org/motherboards/asrock/4CoreDual-VSTA.htm#bios](https://soggi.org/motherboards/asrock/4CoreDual-VSTA.htm#bios)
Internal I/O 
[LIST]
[*]1 PCI Express Graphics (x4) 
[/LIST]

I might be heading in the wrong direction now .......... stop and think some more about why the signal is not
getting to the card  -  

Did we remove any dross that might be affecting what is happening with the drivers before loading in the latest driver ? 

we removed bumblebee but also Bashing Om gave a list of things to check - [B]

1) would it be better to just purge all nvidia drivers and start clean again
[/B]
```

ls -al /lib/modules/4.18.0-11-generic/updates/dkms
ls -al /usr/lib/xorg/modules/drivers
ls -al /usr/lib/x86_64-linux-gnu/nvidia/xorg
ls -al /usr/share/X11/xorg.conf.d
ls /lib/modprobe.d |grep nvidia
lsmod | grep nvidia
ls -al /dev/nvidia*

```


have we got the latest driver in place now ?
**2)**
**sudo ubuntu-drivers autoinstall**

have we checked to make sure its still not blacklisted ?
have we done [B]
3)
dkms status[/B]

---

### Post by roadrash on 2018-11-30
> **23dornot23d said:**
> Thanks CatKiller ......... for the link .........

[http://us.download.nvidia.com/XFree86/Linux-x86_64/390.87/README/commonproblems.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/390.87/README/commonproblems.html)



only one slot for the graphics card though - so it cannot be moved ....... 

[https://soggi.org/motherboards/asrock/4CoreDual-VSTA.htm#bios](https://soggi.org/motherboards/asrock/4CoreDual-VSTA.htm#bios)
Internal I/O 
[LIST]
[*]1 PCI Express Graphics (x4) 
[/LIST]

I might be heading in the wrong direction now .......... stop and think some more about why the signal is not
getting to the card  -  

Did we remove any dross that might be affecting what is happening with the drivers before loading in the latest driver ? 

we removed bumblebee but also Bashing Om gave a list of things to check - [B]

1) would it be better to just purge all nvidia drivers and start clean again
[/B]
```

ls -al /lib/modules/4.18.0-11-generic/updates/dkms
ls -al /usr/lib/xorg/modules/drivers
ls -al /usr/lib/x86_64-linux-gnu/nvidia/xorg
ls -al /usr/share/X11/xorg.conf.d
ls /lib/modprobe.d |grep nvidia
lsmod | grep nvidia
ls -al /dev/nvidia*

```


have we got the latest driver in place now ?
**2)**
**sudo ubuntu-drivers autoinstall**

have we checked to make sure its still not blacklisted ?
have we done [B]
3)
dkms status[/B]

OK .tried that.:

**dkms staus:**

> bbswitch, 0,8,  4.15.0-39-generic, x86_64: installed
nvidia 390.77, 4.15.0-39-generic, x86_64: installed

driver installed but after reboot I got that usual black screen and little cursor top left which is it waiting for a process to finish (what?? & who knows when?? this is the question)

---

### Post by 23dornot23d on 2018-11-30
> 
 waiting for a process to finish (what?? & who knows when?? this is the question) 				 			  			   		 			 			 			

We need someone else to say how you get that information when you cannot get in - other than in safe mode - without any drivers loaded.

I am not sure why it is still showing bbswitch still installed .......... 

Ok it needs this command ...... its bbswitch-dkms not just bbswitch as I wrote earlier .... sorry about  that ..... maybe this will help.

**sudo apt remove bbswitch-dkms**

> 
**bbswitch, 0,8,  4.15.0-39-generic, x86_64: installed**
nvidia 390.77, 4.15.0-39-generic, x86_64: installed 			 		


---

### Post by roadrash on 2018-11-30
> We need someone else to say how you get that information when you cannot get in - other than in safe mode - without any drivers loaded.

Thats the message i get (see post #18) when it stops with just a black screen and flashing cursor in top left corner.  This is usually not visible only the cursor blinking then pausing a few seconds before blinking again.  Then when I installed another driver I think it was the nvidia 384 in ubuntu 18.04.1 (has same issues) and the text was visible for me to see in this version.  I got those logs by runnung a live dvd of ubuntu and accessing the computerts hard disk with the error logs after a failed boot with the Nvidia driver.  That way I didnt need to boot the pc (which would change the logs)  to get the logs as they were last boot up.  Easier than turming on perstance logs and finding the one you want.  Will go try remove bbswitch-dkms now and if it improves I will let you know.

---

### Post by 23dornot23d on 2018-11-30
> 
  Will go try remove bbswitch-dkms now and if it improves I will let you know. 


I hope it works .... because we are running out of new ideas ......

1) You have tried multiple new installs even on different versions of Ubuntu 18.04 - 18.10 ....... with most of the drivers available for that card GTX 480
2) You have tried other versions of Linux ........ Mint ....... same outcome flashing cursor top left ...... on hold.
3) You have managed to get something working but only under nouveau ......

Where to go next ......... might be a faulty graphics card - but I would have expected errors to show up - even when booting
your computer - it would probably beep to let you know there is a problem. ( as I say though nothing is really showing in the logs )

[B]journalctl --boot

[/B]is the only command I have seen that seems to show the information from systemd ............I always try the commands on my own computer before asking anyone to do things[B] -
 systemd seems odd to be in a format that is not easily captured[/B] unless of course everything is running ok **........... especially the graphics driver.** 

( Could I suppose **chroot** in from another system that is running ok - but none have as yet run very well - all sluggish and using massive amounts of CPU )[B] 

  So how you get information from systemd when the graphics card is not running - I am not sure ..........
[/B]

---

### Post by roadrash on 2018-11-30
Removing bbswitch wasn't any better nto be honest and actually it was worse in a way because I didnt even see the little flashing cursor just a black screen and I could not get out of it any way at all except kill th e PC with power switch. I might have to install Windows then just to check the graphics card is working properly.  I dont think it is faulty because this all started when I was using a Nvidia 9800GT graphics card and only bought this one because somone said the age of my graphics card was the problem and yet I still have the same error.  It did exactly the same with the 9800GT card as well.  Ive spent well over a year trying to sort this myself and forked out on another card because I was desperate now to uise my desktop where most of my work is on (Now backed up on external drive).  I did also check the other day if there was a bios update but I have already done it and its up to date.  I can probably install a earlier linux mint or ubuntu 17.04 or 17.10 when it was working and then maybe we can read all the logs and get info from that or do you think I should put this forward as a bug report to see if it can be sorted.

---

### Post by 23dornot23d on 2018-11-30
With it doing it with 2 graphics cards and also multiple Operating Systems ...... it is sounding like there is another fault somewhere ....
maybe even on the motherboard itself ........ but again we are seeing no errors to support that as a theory.

I did think about maybe trying the graphics card in another machine ...... as that would at least let you know if the graphics card is ok
easy for me to say that - as I used to always have a spare desktop to try things in ...... sometimes its a case of one thing interfering with
another ....... we used to take items out and leave the one that had a problem ...... to isolate the problem ..... 

If you know Windows used to pick it up ok ......... then yes that is one  way - because if it does not work with that then it is a fault.

Unless someone else wants to give you some more advice ......... but after a year of trying and so many things you have tried and it
still does not work ..... it does seem to be pointing to a fault somewhere ........

Putting it forward as a bug report ..... there is not enough information to show where the bug lies ..... it could be the motherboard - it could be the graphics card
you have to rule those out first ...... maybe Windows would let you know ....... because if it does not work in Windows and it used to work in Windows - then
there is a problem somewhere else ......... then if it does work in Windows ...... then a bug report could be put in saying that none of the drivers you have used
work with that card .... which could be a possibility.

I must admit I did searches on the GTX480 and solved ........ not a lot came up ........ other than really old posts on it. 

Found this too which is not good ....
[http://www.tomshardware.co.uk/answers/id-3551178/gtx-480-disables-newer-drivers.html](http://www.tomshardware.co.uk/answers/id-3551178/gtx-480-disables-newer-drivers.html)

Could wait a while for more replies on here - maybe someone has spotted something I have not done - or that needs doing ....... to help you .... but
as I say - the only thoughts I am having now are to do with a problem elsewhere ..... possibly a clash of items on the motherboard but if Windows works
then that would rule that out.

---

### Post by CatKiller on 2018-11-30
> **23dornot23d said:**
> With it doing it with 2 graphics cards and also multiple Operating Systems ...... it is sounding like there is another fault somewhere ....
maybe even on the motherboard itself ........ but again we are seeing no errors to support that as a theory.

To me it seems most likely related to

> VIA Universal Graphics Interface: The unique VIA Universal Graphics Interface allows connection of both AGP and PCI Express graphics cards on the same motherboard, truly bridging the gap between the two standards. Furthermore, users can enable advanced VIA DualGFX Express technology by running AGP and PCI Express graphics cards simultaneously, opening up a new expanse of user options.

coupled with the OP having had Bumblebee installed throughout.

---

### Post by 23dornot23d on 2018-11-30
> 
coupled with the OP having had **Bumblebee** installed **throughout**. 


mmm ...... at what post did that happen ....... and the op has had the problem for a year now ........

at post #17 we were only just getting information together from the command line .........

But if you have solved the problem ...... please be specific .......

---

### Post by CatKiller on 2018-11-30
> **23dornot23d said:**
> mmm ...... at what post did that happen .....

Each time the OP says they've done a fresh install, they say they've installed Bumblebee. At no point after that are they free of Bumblebee bits. What does Bumblebee do? It stops Nvidia chips being initialised, unless specifically invoked, in favour of the integrated Intel graphics. But the OP doesn't have Intel graphics, apparently.

When not using Bumblebee, when booting into Live, for example, there is no direct access to the card. Something is acting as an intermediary. That feature on the motherboard is specifically to act as an intermediary, so that it can redefine what the graphics card is doing on the fly. The other graphics card the OP had? Installed in the same motherboard with the same feature.

Maybe there's something else wrong too, but either of those individually would break Nvidia graphics.

---

### Post by roadrash on 2018-11-30
i will have to give up on XP.  I tried to boot into it and its been so long since i last used it there have been a few different graphics cards in before and it keeps crashing apart from as soon as it booted up it I was getting lots of stuff from something.ru so myst be infected with a virus or something.  The very reason I quit windows for Linux and how glad I was to be free of that.  Shows how long since I used windows with XP being my mpost up to date system. Well to test the card on XP I would have to do a reinstall and might even have to upgrade to windows 7 or something because there are other complaints that xp is not compatable that cause issues.  What I migh do is swap back to the previous 9800GT.  The 9800GT has been working great in the past with the nvida driver on this motherboard but that was back at ubuntu 17.04, or maybe even earlier.  I would have to install. them all one by one to find out which version it was.  I know for a fact the last time I had a nvidia driver running on it was with linux mint using the mate desktop so must be around mint 18 or 18.1 which would be Ubuntu 16.04 (Xenial Xerus) time period. This is definitely a lot more involved than I expected.  Now you can see why its been doing my head in.

---

### Post by 23dornot23d on 2018-11-30
Yes - you could try with a clean install of [B]Ubuntu 16.04 (Xenial Xerus)

I did look at the end of life for that too ......... April 2021 ......[/B] I hope you have success with it .......
[TABLE]
[TR]
[TD="bgcolor: #762852"]Ubuntu **16.04.5 LTS**[/TD]
[TD="bgcolor: #f1f1dd"][Xenial Xerus]("https://wiki.ubuntu.com/XenialXerus")[/TD]
[TD="bgcolor: #f1f1dd"] [Changes]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/ChangeSummary/16.04.5")[/TD]
[TD="bgcolor: #f1f1dd"] [August 2, 2018]("https://lists.ubuntu.com/archives/ubuntu-announce/2018-August/000235.html")[/TD]
[TD="bgcolor: #f1f1dd"] [April 2021]("https://lists.ubuntu.com/archives/ubuntu-announce/2016-April/000207.html")[/TD]
[/TR]
[/TABLE]

Post back when you have it installed ......  maybe it will automatically pick up the card.

You have a lot of patience .....

---

### Post by roadrash on 2018-11-30
Before i give up on ubuntu 18.04.1 i swapped back to my 9800GT card which has worked before. Soon as i booted to the desktop and tried  to start reconfiguring things i got lots of errors and decided to scrap that install and do a clean one and do to this card what we did with the other one.  The result was it almost mirrored exactly what happened with the GTX4800 rigjt down to that little cursor flashing which is that waiting for a process error.  So its either the motherboard or its Ubuntu dont like my setup. Might have try another motherboard although it has worked with the nvidia driver in Ibuntu in  the past.  Thanks  for all your help ive learned at lot from this. Will let you know if i ever make a breakthrough.

---

### Post by 23dornot23d on 2018-11-30
Ok - well best of luck ....... with whatever you do try out next .......

---

### Post by roadrash on 2018-12-01
In case you are interested I have managed to get my system fully working like perfect with the Nvidia driver.  I put the Geforce 9800GT card back in and worked my way back through all the distros & versions ive used over tywo years installing them all and installing all versipns of the nvidia driver.  I found out the last system I had working was Linux mint 18.01.1 Sylvia with the Nvidia 3.04 driver.  Using the DVI output only gave me 800x600 resolution and no attemps at using xrandr and modelines could get me a decent resolution from the DVI connection so I tied the VGA connection & I get all resolutions 14440 and higher.
I have taken a screenshot of it displaying some info like inxi -Fz.  If you want me so get anything else let me know.  At least I have a usable system again.

---

### Post by 23dornot23d on 2018-12-01
Excellent result .............. just seen the screenshot - everything looks good ...........
[B]Yep - can see its using the Nvidia Driver too ...... well done ... give the man a cigar ....... and popcorn ;)    :popcorn:


the 304 driver is being used ....... I read something on the Nvidia site about older cards not using the newer drivers
but its good to see it works ok ....... nvidia settings and everything .... ;)
[/B]

---

### Post by roadrash on 2018-12-01
> **23dornot23d said:**
> Excellent result .............. just seen the screenshot - everything looks good ...........
[B]Yep - can see its using the Nvidia Driver too ...... well done ... give the man a cigar ....... and popcorn ;)    :popcorn:

[/B]

Rganks but still hoping now its working again we can use this info to find out why it wont work in the latest Ubuntu versions post 18.04.
I went and ordered another more up to date (for me) Asus  motherboard to experiment with as well

---

### Post by 23dornot23d on 2018-12-01
Yes well its up to you - when you want to carry on - or if you are happy and have a good system now - why not stick with it for a while

or if you want to try a separate install alongside what you have we can still keep going .........

Looks like you have got the bug again ....

> 
I went and ordered another more up to date (for me) Asus  motherboard to experiment with as well 				


Which board have you ordered ? ( you have to make sure your power supply can handle things etc ..... )

==================================================================

Have a read here though - I found this later on when looking through the bugs list .... for drivers

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1790219](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1790219)

---

### Post by CatKiller on 2018-12-01
> **23dornot23d said:**
> 
the 304 driver is being used ....... I read something on the Nvidia site about older cards not using the newer drivers
but its good to see it works ok ....... nvidia settings and everything .... ;)
The 9800 is supported up till the 340 branch. Support was dropped for the 390 branch.

---

### Post by roadrash on 2018-12-01
> Which board have you ordered ? ( you have to make sure your power supply can handle things etc ..... )
Its a s/h Asus P5G41 T-MLX (coming with proccesor and ram) nothing much better than this one just a bit newer and more mainstream although i wish it had been ATX not uatx.
Its will either be my main desktop now or for experiementing on. Ive got a Acer laptop I use Ubuntu on as well.  The desktop is my work pc that i use with my vintage equipment.

> **CatKiller said:**
> The 9800 is supported up till the 340 branch. Support was dropped for the 390 branch.
I did try the 3.40 driver but it failed. only the 304 would work.  I havent tried the GTX4800 with this mint version or its ubuntu equivilent yet.

---

### Post by 23dornot23d on 2018-12-01
[https://en.wikipedia.org/wiki/MicroATX](https://en.wikipedia.org/wiki/MicroATX)

Thus, microATX motherboards can be used in full-size ATX cases.  Furthermore, most microATX motherboards generally use the same power  connectors as ATX motherboards,[SUP][[4]]("https://en.wikipedia.org/wiki/MicroATX#cite_note-4")[/SUP] thus permitting the use of full-size ATX power supplies with microATX boards. 


> 
Ive got a Acer laptop I use Ubuntu on as well.  The desktop is my work pc that i use with my vintage equipment.



As long as it works ......... what was the cpu monitor like when using the nvidia driver ......... 

I should imagine it was really low .......

---

### Post by roadrash on 2018-12-01
> **23dornot23d said:**
> [https://en.wikipedia.org/wiki/MicroATX](https://en.wikipedia.org/wiki/MicroATX)

As long as it works ......... what was the cpu monitor like when using the nvidia driver ......... 

I should imagine it was really low .......


Its just 36c and its been on for couple of hours.
These things are like star wars to me as I started on computers when they were cp/m thing with 7" floppies. I repair/restore old computers for fun.

---

### Post by 23dornot23d on 2018-12-01
> 
 I started on computers when they were cp/m thing with 7" floppies. I repair/restore old computers for fun.                 


No wonder you have loads of patience ............. then .............. 
I started building them when moving from 5 1/4 to 3.5 inch disks 720k to 1.44 meg
 .......... seems like yesterday ..... mmm ............. separate co-processor and main CPU ....
first one I bought cost a arm and leg and you had to be ever so careful to line all the pins up and get them
to go in parallel .... must admit though starting my old desktop up - I did not realise how slow it was back
then as everything was comparable ..... well back to the problem at hand ...... if it still is one now. ;)

---

### Post by roadrash on 2018-12-01
Yep the good ol days when ram was measured in kilobytes.

Here is something for you to get your teeth into if your intersted.  I took out the 9800GTX and put the GTX480SE in again and no matter what driver I tried it failed just at the login point either with a error message or that annoying balck sceeen with the little cusor top right.  I did managed one of the errors gave me a suggestion to look at systemctl so ive put it in a pastbin for you to see.

The errors were

>  Failed to start Light Display manager.
Started Thermal Daemon services
Started LSB: load kernel modules needed to enable cpufreq scaling

[quote] Failed to start Light display manager
see 'systemctl' status lightdm.service.for details.

Systemctl output here :[https://pastebin.com/embed_js/nzQM2cZy]("https://pastebin.com/embed_js/nzQM2cZy")

---

### Post by 23dornot23d on 2018-12-01
Nothing really showing up in that ..... everything seems to have loaded .... this is the only line I can see that relates to graphics.

> 
graphical.target                                                                          loaded active active    Graphical Interface


Its probably not communicating with the graphics card for whatever reason - it knows its there or something is there ...... maybe a fault on that graphics card ......
but still not enough information to rule it out as bad for sure yet - that systemd log would be useful if there is a way to get it !!!

**pybootchart** - was something we used to be able to run .... showed what was happening at boot and through to the desktop .... all processes ...
seems its gone now .... a nice chart was produced .... not sure if it would have given more clues or not ........ [http://www.bootchart.org/](http://www.bootchart.org/)

What does this show for what you have set to load at the moment - although - the second one might not work.

[B]dkms status

[/B]and if you can get this to work ....in any way[B] ....

journalctl --boot[/B]

---

### Post by roadrash on 2018-12-01
Will do it in the morning. Ive been at yhis solid for 13 hours and need some sleep now.  Night night

---

### Post by 23dornot23d on 2018-12-01
ok night ..... am messing with Devuan at the moment - so keep swapping distros ..... cheers .... will look again tomorrow .... sleep well

There is a xorg log in here too .... might be interesting to see it ....

/var/log/lightdm/x-0.log

---

### Post by roadrash on 2018-12-02
Been having a few more attempts to try and solve whats going on.  I thonk i am beginning to see what you have been saying being confirmed in some logs and messages.
Here is a picture of the most obvious part of a log. I think this is saying its enabled 2d graphics but cant tell the card to turn on 3d accelerated graphics.  I thought if it had any graphical display iy meant the card what working.  I bought this off ebay as a working one and when i got it displaying a desktop i gathered it was and left him good feedback.  Now looks like could be faulty.

---

### Post by 23dornot23d on 2018-12-02
From post #33 .... conetents of my Xorg.0.log

Yes post no 41 we had this in that log 

> 
[    47.032] (==) modeset(0): DPMS enabled
[    47.032] (II) modeset(0): [DRI2] Setup complete
[    47.032] (II) modeset(0): [DRI2]   DRI driver: i965
[    47.032] (II) modeset(0): [DRI2]   VDPAU driver: i965
[    47.032] (--) RandR disabled
[    47.054] (II) SELinux: Disabled on system
[    47.060] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    47.060] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    47.060] (II) AIGLX: enabled GLX_INTEL_swap_event
[    47.060] (II) AIGLX: enabled GLX_SGI_swap_control
[    47.060] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    47.060] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    47.060] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    47.060] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    47.060] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    47.061] (II) AIGLX: **Loaded and initialized i965                      **


What does 

**dkms status **

and 

**inxi -F**

give back now you have a display again ......... I have a feeling it will say something like i965 is being used for the display ..... possibly vesa

did you have a look at the logs too for 

**/var/log/lightdm/ ** there may be 2 files in here - both would be good to see ......

does this command now ..... work also seeing we have a display ...... its a double - -   dash before boot

**journalctl --boot**

---

### Post by roadrash on 2018-12-02
I currently have that GTX480 back in trying to find out a bit more info.  Do want me to run dkms staus and give the logs from this card or do you want it all from the 9800 GTX with nvidia driver working?  I can put it back in if you want. I was just going to do a windows 7 or 10 install just to test this GTX480 with the windows driver and compare.

---

### Post by 23dornot23d on 2018-12-02
Try this command too while the GTX480 is in it ..... need to see what is happening with it .......... as we know the other card works now.

So the solution is still needed for the GTX480 - I have looked all over the web to find more information on 

GTX480 and the motherboard [SIZE=2]ASRock 4CoreDual-VSTA - still not found anything that gives a clear answer as to how to check for
a fault though ..... the logs are the only clue ..... and if it picks information from a chip up on the board and runs the graphics in low res
from what seems to be the i965 .... yet I cannot see that intel documented anywhere on your motherboard ......
[/SIZE]
[B][https://soggi.org/motherboards/asrock/4CoreDual-VSTA.htm](https://soggi.org/motherboards/asrock/4CoreDual-VSTA.htm)

lspci -v -q

[/B][B]journalctl --boot



[/B]Then do the tests with these ...... as the graphics card seems to be the only thing we have not fully ruled out ......
as the motherboard must be ok to run the other graphics card  (9800 GTX with nvidia driver) as it goes into the same **PCI-e slot** ......
Unless the Power Supply is not man enough to run the GTX480 ..... but then it should still come back with a error ....
[http://www.tomshardware.co.uk/forum/291544-33-power-supply-requirements](http://www.tomshardware.co.uk/forum/291544-33-power-supply-requirements)

> 

I was just going to do a windows 7 or 10 install just to test this GTX480 with the windows driver and compare. 



---

### Post by roadrash on 2018-12-02
here you go:

dkms status

> bbswitch, 0.8, 4.4.0-53-generic, x86_64: installed
ndiswrapper, 1.60, 4.4.0-53-generic, x86_64: installed
nvidia-304, 304.135, 4.4.0-53-generic, x86_64: installed
[1;34mCPU[0;37m~Dual core Intel Core2 6400 (-MCP-) [1;34mspeed[0;37m~2049 MHz (max) [1;34mKernel[0;37m~4.4.0-53-generic x86_64 [1;34mUp[0;37m~2 min [1;34mMem[0;37m~76.4/1999.8MB [1;34mHDD[0;37m~453.0GB(2.0% used) [1;34mProcs[0;37m~127 [1;34mClient[0;37m~Shell [1;34minxi[0;37m~2.2.35 [0;37m [0;37m
[0m

inxi

> [1;34mSystem:   [0;37m [1;34mHost:[0;37m jon-desktop [1;34mKernel:[0;37m 4.4.0-53-generic x86_64 (64 bit)[0;37m
[1;34m          [0;37m [1;34mConsole:[0;37m tty 1 [1;34mDistro:[0;37m Linux Mint 18.1 Serena[0;37m
[1;34mMachine:  [0;37m [1;34mMobo:[0;37m N/A [1;34mmodel:[0;37m 4CoreDual-VSTA[0;37m
[1;34m          [0;37m [1;34mBios:[0;37m American Megatrends [1;34mv:[0;37m P2.30 [1;34mdate:[0;37m 02/26/2008[0;37m
[1;34mCPU:      [0;37m [1;34mDual core[0;37m Intel Core2 6400 (-MCP-)[0;37m [1;34mcache:[0;37m 2048 KB[0;37m 
[1;34m          [0;37m [1;34mclock speeds:[0;37m [1;34mmax:[0;37m 2049 MHz [1;34m1:[0;37m 2049 MHz [1;34m2:[0;37m 2049 MHz[0;37m
[1;34mGraphics: [0;37m [1;34mCard:[0;37m NVIDIA GF100 [GeForce GTX 480][0;37m
[1;34m          [0;37m [1;34mDisplay Server:[0;37m X.org 1.18.4 [1;34mdriver:[0;37m N/A[0;37m
[1;34m          [0;37m [1;34mtty size:[0;37m 80x25 [1;34mAdvanced Data:[0;37m N/A for root out of X[0;37m
[1;34mAudio:    [0;37m [1;34mCard-1[0;37m VIA VT8237A/VT8251 HDA Controller [1;34mdriver:[0;37m snd_hda_intel[0;37m
[1;34m          [0;37m [1;34mCard-2[0;37m NVIDIA GF100 High Definition Audio Controller[0;37m
[1;34m          [0;37m [1;34mdriver:[0;37m snd_hda_intel[0;37m
[1;34m          [0;37m [1;34mSound:[0;37m Advanced Linux Sound Architecture [1;34mv:[0;37m k4.4.0-53-generic[0;37m
[1;34mNetwork:  [0;37m [1;34mCard:[0;37m VIA VT6102/VT6103 [Rhine-II] [1;34mdriver:[0;37m via-rhine[0;37m
[1;34m          [0;37m [1;34mIF:[0;37m enp0s18 [1;34mstate:[0;37m down [1;34mmac:[0;37m 00:13:8f:fd:82:1f[0;37m
[1;34mDrives:   [0;37m [1;34mHDD Total Size:[0;37m 453.0GB (2.0% used)[0;37m
[1;34m          [0;37m [1;34mID-1:[0;37m /dev/sda [1;34mmodel:[0;37m Maxtor_7L250R0 [1;34msize:[0;37m 251.0GB[0;37m
[1;34m          [0;37m [1;34mID-2:[0;37m /dev/sdb [1;34mmodel:[0;37m ST3200826A [1;34msize:[0;37m 200.0GB[0;37m
[1;34m          [0;37m [1;34mID-3:[0;37m USB /dev/sdc [1;34mmodel:[0;37m Flash_Disk [1;34msize:[0;37m 2.0GB[0;37m
[1;34mPartition:[0;37m [1;34mID-1:[0;37m / [1;34msize:[0;37m 136G [1;34mused:[0;37m 6.8G (6%) [1;34mfs:[0;37m ext4 [1;34mdev:[0;37m /dev/sda6[0;37m
[1;34m          [0;37m [1;34mID-2:[0;37m swap-1 [1;34msize:[0;37m 2.15GB [1;34mused:[0;37m 0.00GB (0%) [1;34mfs:[0;37m swap [1;34mdev:[0;37m /dev/sda5[0;37m
[1;34mRAID:     [0;37m No RAID devices: /proc/mdstat, md_mod kernel module present[0;37m
[1;34mSensors:  [0;37m [1;34mSystem Temperatures: cpu:[0;37m 43.0C [1;34mmobo:[0;37m N/A[0;37m
[1;34m          [0;37m [1;34mFan Speeds (in rpm): cpu:[0;37m N/A[0;37m
[1;34mInfo:     [0;37m [1;34mProcesses:[0;37m 127 [1;34mUptime:[0;37m 4 min [1;34mMemory:[0;37m 77.4/1999.8MB [1;34mInit:[0;37m systemd[0;37m
[1;34m          [0;37m [1;34mClient:[0;37m Shell (bash) [1;34minxi:[0;37m 2.2.35[0;37m [0;37m
[0m

lightdm.log

[https://pastebin.com/embed_js/YeYrCkzy](https://pastebin.com/embed_js/YeYrCkzy)

journalctl

[https://pastebin.com/embed_js/86ALtqqX](https://pastebin.com/embed_js/86ALtqqX)

lspci

[https://pastebin.com/embed_js/eCx6m4Tr](https://pastebin.com/embed_js/eCx6m4Tr)

hope these are interesting.  going to pop off and try a windows driver test.

---

### Post by oldfred on 2018-12-02
To get a readable inxi you need another parameter.

       Need -c 0 on redirect to eliminate extra ASCII chars.
inxi -Fxz -c 0 > inxi_list.txt

---

### Post by CatKiller on 2018-12-02
```
bbswitch, 0.8, 4.4.0-53-generic, x86_64: installed
```

You've still got Bumblebee there. You really don't want to have Bumblebee.

Use CODE tags for output: quote tags make the text disappear if someone tries to reply to you.

---

### Post by 23dornot23d on 2018-12-02
I have just gone through all the information you have given ..... have just tried to pick out the things that relate to the graphics

and as CatKiller says .... do not load Bumblebee in/up you do not need it for that system .... think this keeps getting mentioned.
its for laptops and power saving and may be causing the computer to look for files that are not there ...... seen it in a few places
where files are missing .....

```


From dkms status

This should not be here now - we do not need bumblebee .... do not load it up .....
bbswitch, 0.8, 4.4.0-53-generic, x86_64: installed

From lightdm

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=1251
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: **Loading configuration from /usr/share/lightdm/lightdm.conf.d/90-nvidia.conf**
[+0.00s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration


From journalctl ....

Dec 02 14:08:20 jon-desktop kernel: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-**4.4.0-53-generic** root=UUID=f42e1b53-cef4-4151-97d5-e57af4d0763f ro **recovery nomodeset**


Dec 02 14:08:20 jon-desktop kernel: aer 0000:00:02.0:pcie02: service driver aer loaded
Dec 02 14:08:20 jon-desktop kernel: pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
Dec 02 14:08:20 jon-desktop kernel: pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Dec 02 14:08:20 jon-desktop kernel: pci 0000:02:00.1: Signaling PME through PCIe PME interrupt
Dec 02 14:08:20 jon-desktop kernel: pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
Dec 02 14:08:20 jon-desktop kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 02 14:08:20 jon-desktop kernel: pciehp 0000:00:02.0:pcie04: Slot #16 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl- LLActRep+
Dec 02 14:08:20 jon-desktop kernel: pciehp 0000:00:02.0:pcie04: service driver pciehp loaded
Dec 02 14:08:20 jon-desktop kernel: pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 02 14:08:20 jon-desktop kernel: intel_idle: does not run on family 6 model 15
Dec 02 14:08:20 jon-desktop kernel: input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 02 14:08:20 jon-desktop kernel: ACPI: Power Button [PWRB]
Dec 02 14:08:20 jon-desktop kernel: input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 02 14:08:20 jon-desktop kernel: ACPI: Power Button [PWRF]
Dec 02 14:08:20 jon-desktop kernel: GHES: HEST is not enabled!
Dec 02 14:08:20 jon-desktop kernel: Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 02 14:08:20 jon-desktop kernel: 00:06: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Dec 02 14:08:20 jon-desktop kernel: Linux agpgart interface v0.103
Dec 02 14:08:20 jon-desktop kernel: agpgart: Detected VIA PT880 Ultra chipset
Dec 02 14:08:20 jon-desktop kernel: agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000

This is all related to bumblebee .... no such file is being recorded ....
Dec 02 14:08:23 jon-desktop ureadahead[347]: ureadahead:/usr/bin/start-nvidia-persistenced: **No such file or directory**
Dec 02 14:08:23 jon-desktop ureadahead[347]: ureadahead:/usr/lib/nvidia-340/libnvidia-glcore.so.340.104: **No such file or directory**
Dec 02 14:08:23 jon-desktop ureadahead[347]: ureadahead:/usr/bin/stop-nvidia-persistenced: **No such file or directory**
Dec 02 14:08:23 jon-desktop ureadahead[347]: ureadahead:/usr/lib/nvidia-340/tls/libnvidia-tls.so.340.104: **No such file or directory**
Dec 02 14:08:23 jon-desktop systemd[1]: Started udev Kernel Device Manager.

This in lightdm too no such file or directory ...
Dec 02 14:08:24 jon-desktop ureadahead[347]: ureadahead:/usr/share/lightdm/lightdm.conf.d/90-nvidia.conf: **No such file or directory**

This seems to say its being initialize ...
Dec 02 14:08:27 jon-desktop kernel: [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:02:00.0 on minor 0
Dec 02 14:08:27 jon-desktop kernel: NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.135  Tue Jan 17 15:26:26 PST 2017

From lspci

02:00.0 VGA compatible controller: NVIDIA Corporation GF100 [GeForce GTX 480] (rev a3) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation GF100 [GeForce GTX 480]
    Physical Slot: 16
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f4000000 (32-bit, non-prefetchable) [size=32M]
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at d8000000 (64-bit, prefetchable) [size=64M]
    I/O ports at cc00 [size=128]
    Expansion ROM at f7d80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
[B]    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_304[/B]

From inxi

Graphics: Card: NVIDIA GF100 [GeForce GTX 480]
Display Server:X.org 1.18.4 **driver: N/A**
tty size:80x25 Advanced Data: N/A for root out of X

```


Will come back to this later ..... but would like to see what results you have with your latest installs ...... 

to see if the graphics card is working or not.

---

### Post by oldfred on 2018-12-02
My notes say it was nVidia 3.19 that started to support the switching and obsoleting bumblebee. So installing an older nVidia on a laptop may still install by default the bumblebee drivers. But if not laptop, you would not need them, anyway, regardless of nVidia version.
I thought Ubuntu 18.04 stopped offering the 304.xx driver for very old nVidia cards.

This shows which driver goes with which nVidia card. And any other driver probably will not work or work correctly.
[https://www.nvidia.com/object/IO_32667.html](https://www.nvidia.com/object/IO_32667.html)

---

### Post by 23dornot23d on 2018-12-02
I think he is using something older now OldFred looking at the kernel in the journal file

vmlinuz-[B]4.4.0-53-generic

[/B]Quite possible that its the Xenial install that was being used 16.04 for the last set of information .....

@roadrash ..... 

1 ) Did you use 16.04 ( xenial ) with the card that works ok the 9800 GTX ......

Then when you found it was working ok - did you leave that same system in place and just swapped the card over
to the GTX 480 ..... and found it would not work .......

or did you do a fresh install of linux again ....

---

### Post by roadrash on 2018-12-02
Dont now whether to be happy or sad.  I forgot how tedious it was installing windows.  Tried windows 10 and it crashed with a error right at the ned and after a long time installiong  "windows cant be installed on this system".  So tried windows 7, it installed but i downloaded recent driver for GTX480 and when it restarted after installing I lost the screen display and the monitor went into standby.  I fitted in the 9800GT and got a dispay back and uninstalled everything.  I then refitted the GTX480 and this time found the oldest driver I could find for the GTX480 (rumours of newer drivers not working) I installled it and rebooted again and its all working perfectly playing Hi-def movies everything.  So sorry to say its ubuntu or more likely the current Nvidia driver thats at fault.  Is there a source of old versions of the Linux nvidia driver as a .deb file anywhere we can try.
here is proof of it working with the driver in widows.

at least I know the card is all working OK.  By the way I didnt install bumblebee unless it installed somehow with the Nvidia driver.
Know what do we do?????? a hell of a lot of work but finally we know the problem is a system or driver issue and not a hardware one.

---

### Post by 23dornot23d on 2018-12-02
Ok that is brilliant - like you say a lot of work ..... but at least you proved the graphics card is ok ............ and it does need older drivers ......

> 
at least I know the card is all working OK.**  By the way I didnt install  bumblebee unless it installed somehow with the Nvidia driver**.

Now what do we do?????? a hell of a lot of work but finally **we know the  problem is a system or driver issue and not a hardware one**.                 


> 
  Is there a source of old versions of the Linux nvidia driver as a .deb file anywhere we can try.


Old Fred may know how to get the correct driver ..... hopefully ....... he seems to have notes on when things changed .....

> 
  I then refitted the GTX480 and this time found the oldest driver I  could find for the GTX480 (rumours of newer drivers not working) 
I  installled it and rebooted again and its all working perfectly playing  Hi-def movies everything.


Me I just use what is available usually and do not go hunting around too much as I never quite know what the ones from other sites will do
and if I can trust them ............ there was some on the Nvidia site itself .... but which one to use ..... or whether things may need altering
or not for the latest Ubuntu I do not know ............

Is your windows a 32bit or 64bit install ........... ?

---

### Post by roadrash on 2018-12-02
> **oldfred said:**
> To get a readable inxi you need another parameter.

       Need -c 0 on redirect to eliminate extra ASCII chars.
inxi -Fxz -c 0 > inxi_list.txt

Sorry abaout that I will remeber in future.

> **CatKiller said:**
> ```
bbswitch, 0.8, 4.4.0-53-generic, x86_64: installed
```

You've still got Bumblebee there. You really don't want to have Bumblebee.

Use CODE tags for output: quote tags make the text disappear if someone tries to reply to you.

I dont know how bumbleee got there unless it somehow installed with the nvidia drive when I had to keep installing then puging it go post  back here sometimes because with the driver installed I have no display.

> **CatKiller said:**
> ```
bbswitch, 0.8, 4.4.0-53-generic, x86_64: installed
```

You've still got Bumblebee there. You really don't want to have Bumblebee.

Use CODE tags for output: quote tags make the text disappear if someone tries to reply to you.

I dont know how that happened unless it was installed someow with the nviidia driver.  I had to sometimes install the driver, save a copy of te logs and then purge the driver oro get a display to post them up here.  \i gety no screen display with the driver installed.  How do I use tyhe code tags you mention?

> **23dornot23d said:**
> I think he is using something older now OldFred looking at the kernel in the journal file

vmlinuz-[B]4.4.0-53-generic

[/B]Quite possible that its the Xenial install that was being used 16.04 for the last set of information .....

@roadrash ..... 

1 ) Did you use 16.04 ( xenial ) with the card that works ok the 9800 GTX ......

Then when you found it was working ok - did you leave that same system in place and just swapped the card over
to the GTX 480 ..... and found it would not work .......

or did you do a fresh install of linux again ....


Yes I did use a Xenial install

---

### Post by 23dornot23d on 2018-12-02
Did you see post #99 ...... mainly to say - I am not sure about a .deb file for the driver ....... but Old Fred might know .......

Was the windows 7 install a 32 bit or 64bit system .... ?

---

### Post by roadrash on 2018-12-02
> **23dornot23d said:**
> Ok that is brilliant - like you say a lot of work ..... but at least you proved the graphics card is ok ............ and it does need older drivers ......





Old Fred may know how to get the correct driver ..... hopefully ....... he seems to have notes on when things changed .....



Me I just use what is available usually and do not go hunting around too much as I never quite know what the ones from other sites will do
and if I can trust them ............ there was some on the Nvidia site itself .... but which one to use ..... or whether things may need altering
or not for the latest Ubuntu I do not know ............

Is your windows a 32bit or 64bit install ........... ?

The drivers on the nvidia site don't go back far enough now to get around the problems they had at one time with more up to date drivers so I found this site that has a archive of all drivers releases and found one of the first they released for thet card.  I am not worried about security at the moment because i am using a temp install of winows 7 on the desktop we are trying to sort and if it gets messed up well it dont matter cos I am going to delete windows very soon and go back to ubuntu.  With a working Nvidia driver install I hope.

Its a 64bit version  windows 7 install and a 64 bit nvidia driver I used.

---

### Post by 23dornot23d on 2018-12-02
> 
 I found this site that has a archive of all drivers releases and found one of the first they released for thet card.


Do you have the link for it and the name of the file you downloaded ......... might help trace it - that's all.

Ok thanks for that - all 64bit - was just for information while you have it up and running ..........

For the code tags that CatKiller mentioned - all you have to do is use QUOTE ....... tags - but replace the word QUOTE for **code** in both but leave the / backslash in the second one
instances in the square brackets .......... cannot show you as the editor will automagically change them .........

> 
 I am going to delete windows very soon and go back to ubuntu.  With a working Nvidia driver install I hope.


I hope so too ..... but if you have the version of the driver you used - we may be able to track something down between us ........ just a thought
more hands to the job the better so to say.

---

### Post by oldfred on 2018-12-02
The ppa has old drivers as well as newest ones, by Ubuntu version.
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
But you should only be installing the correct driver for your card.

You can look up what is correct driver, and then down load that using ppa. I do not think the 304.xx is correct for either of your cards.
       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
    
# this is the defaults included in the Ubuntu version.
       # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
With 18.04, the only way I can get to this now is with Software Updater & Settings.
ubuntu-drivers devices 
    
       # make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
# should show newest versions available in addition to defaults
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

# to uninstall ppa later if you do not want it, do not run now
sudo add-apt-repository --remove ppa:graphics-drivers/ppa 

The purge instructions I have seen before also remove bumblebee if it is there.
       If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
  
  sudo service lightdm stop

---

### Post by mc4man on 2018-12-02
If inclined to try again at some point - 
For starters try Ubuntu 18.04 (not mint...
Do not install bumblebee
Try the default repo package, i.e nvidia-driver-390

Looking at *all* your inxi & xorg.0 logs not once was the nvidia driver in use, not on 18.04 nor 18.10 (installed but not in use.
If posting any inxi command just use this for relevant, uncluttered info, put in a code box, not quote box
(-try to do from desktop instead of tty though I guess shouldn't matter much.. Some of your inxi's where from tty, some from desktop. 
```
inxi -SG
```

Ex. here, have a m gpu so nvidia is 2nd device, blue  line is what matters.. the line below that  semi matters, 
```
$ inxi -SG
System:
  Host: doug-Lenovo-IdeaPad-Y510P Kernel: 4.15.0-39-generic x86_64 bits: 64 
  Desktop: Gnome Distro: Ubuntu 18.04.1 LTS 
Graphics:
  Card-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 
  v: kernel 
  Card-2: NVIDIA GK107M [GeForce GT 755M] driver: nvidia v: 410.73 
  [COLOR="#0000CD"]Display: x11 server: X.Org 1.19.6 driver: modesetting,nvidia [/COLOR]
  unloaded: fbdev,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GT 755M/PCIe/SSE2 v: 4.6.0 NVIDIA 410.73 
```

---

### Post by roadrash on 2018-12-03
> **23dornot23d said:**
> Do you have the link for it and the name of the file you downloaded ......... might help trace it - that's all.

Ok thanks for that - all 64bit - was just for information while you have it up and running ..........

For the code tags that CatKiller mentioned - all you have to do is use QUOTE ....... tags - but replace the word QUOTE for **code** in both but leave the / backslash in the second one
instances in the square brackets .......... cannot show you as the editor will automagically change them .........



I hope so too ..... but if you have the version of the driver you used - we may be able to track something down between us ........ just a thought
more hands to the job the better so to say.

The site with all the old grapgics drivers is: [https://www.guru3d.com/](https://www.guru3d.com/)
The driver I used was 197.75 from 18th May 2010.

Thanks for that info on the drivers oldfred thats very useful.

Ok I am ready for a fresh start now we know the graphics card ik OK.  So I have now put on a fresh install of Ubuntu 18.04.1 LTS on the compter and done all updates.

Normaly now I would usually start by:

1) install lightdm and make it default
2) install Mate desktop, log out and back into Mate desktop.
3) in terminal, purge nvida.
4) open drivers and install driver of choice and reboot
5) in recovery root terminal do "nvidia-xconfig" +reboot

Can you converse with each other and come up with a list of steps you want me to take this time and I will get to work on it.
Cheers everyone and fingers crossed.

---

### Post by CatKiller on 2018-12-03
We're trying to eliminate variables, so I wouldn't do the first two, and I wouldn't do the last one.

What I would do is add the graphics drivers PPA and install nvidia-graphics-drivers-340, since that is the most recent that supports your graphics cards, IIRC. Keep an eye on whether Bumblebee gets pulled in as a recommendation, and remove if it does.

---

### Post by mc4man on 2018-12-03
> **roadrash said:**
> Thanks for that info on the drivers oldfred thats very useful.

Ok I am ready for a fresh start now we know the graphics card ik OK.  So I have now put on a fresh install of Ubuntu 18.04.1 LTS on the compter and done all updates.

Normaly now I would usually start by:

1) install lightdm and make it default
2) install Mate desktop, log out and back into Mate desktop.
3) in terminal, purge nvida.
4) open drivers and install driver of choice and reboot
5) in recovery root terminal do "nvidia-xconfig" +reboot

Can you converse with each other and come up with a list of steps you want me to take this time and I will get to work on it.
Cheers everyone and fingers crossed.
My view is to not complicate it.

Fresh install 18.04
Run these commands
sudo apt update
sudo apt upgrade
sudo apt install inxi
reboot

Then run inxi -SG & post results, comment on how it performs.

After that run
sudo apt install nvidia-driver-390
reboot

If it boots up ok run inxi command again, ect.
If it boots to greeter but then not to the desktop go to a tty, login & run these 4 separate commands

```
cat /var/log/Xorg.0.log > x.log
journalctl -b -0 > jct.log
sudo apt purge nvidia*
sudo apt autoremove
reboot
```

If it doesn't boot up (black screen, then reboot > go to recovery > fsck > root shell prompt
run these 4 separate commands, replacing username with your username
```
cat /var/log/Xorg.0.log > /home/username/x1.log
**removed, log useless from reovery console**
sudo apt purge nvidia*
sudo apt autoremove
reboot
```

Post saved logs, will be in home folder

---

### Post by roadrash on 2018-12-03
> **mc4man said:**
> My view is to not complicate it.

Fresh install 18.04
Run these commands
sudo apt update
sudo apt upgrade
sudo apt install inxi
reboot

Then run inxi -SG & post results, comment on how it performs.

Ive done apt-get upgrade as I hadnt done that
here are the results of inxi -SG
```
System:    Host: jon-desktop Kernel: 4.15.0-39-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Graphics:  Card: NVIDIA GF100 [GeForce GTX 480]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 128 bits)
           version: 3.3 Mesa 18.0.5
```

Not sure about the latest Nvidia 390 driver because it was the later Windows drivers that played havoc with the GTX480.  I did notice that the 9800GT & the GTX480 utilise the same driver.

> **mc4man said:**
> My view is to not complicate it.

After that run
sudo apt install nvidia-driver-390
reboot

If it boots up ok run inxi command again, ect.
If it boots to greeter but then not to the desktop go to a tty, login & run these 4 separate commands



Sorry for delay I had a doctors appointment and I have been having a nightmare trying to get these pastes done.  Got a whole reply typed it then couldn't get pastebin to work because I only have a resolution on the desktop of 640x400 and there was no embed option I ended up losing it all.
Anyway after installing the 390- driver it got stuck with the message "waiting for boot process to finish" or something and I had to press reset.
here is paste of jornalct;.  xorg for some reason didnt work so will try again.
[https://pastebin.com/embed_js/KV7rCfQD](https://pastebin.com/embed_js/KV7rCfQD)

---

### Post by 23dornot23d on 2018-12-03
There is a problem here - that I have not seen show up before ..... others are reporting similar on the nvidia site too ...

> 
Dec 03 17:28:45 jon-desktop kernel: NVRM: RmInitAdapter failed! (0x26:0x65:1123)
Dec 03 17:28:45 jon-desktop kernel: NVRM: rm_init_adapter failed for device bearing minor number 0
Dec 03 17:28:45 jon-desktop systemd-udevd[267]: Process \'/usr/bin/nvidia-smi\' failed with exit code 6.


---

### Post by roadrash on 2018-12-03
Hey guys I think we are onto something here.  After that last failure and no log file.  I went to recovery root terminal and did a apt purge nvidia* then did a apt autoremove and it took a lot out. So I rebooted and installed the 390 driver again, rebooted and this time it booted to a desktop although very low res again. So I checked the drivers again and it showed the 390 driver installed.  I then looked in the /etc/X11/ folder but there was no xorg.conf or xorg.0.log so i opened  terminal and issued a sudo nvidia-xconfig.  This created a xorg.conf file and then rebooted again.
Its still in low res but went to utube and videos played smooth so hardware acceleration is working.
Here is the output of inxi -SG

```
 System:    Host: jon-desktop Kernel: 4.15.0-39-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Graphics:  Card: NVIDIA GF100 [GeForce GTX 480]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 128 bits)
           version: 3.3 Mesa 18.0.5

```

here is the xorg.conf.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 390.77  (buildmeister@swio-display-x64-rhel04-14)  Tue Jul 10 23:19:22 PDT 2018

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

A result I think.  What do we do to cure the resolution, edit xorg.config like in the past?  The nvidia settings only give information and some stuff about profiles but nothing to change any settings or the resolution.

---

### Post by 23dornot23d on 2018-12-03
You could try arandr if you are happy with what you have - but its still using 

> 
[B]drivers: fbdev,nouveau
[/B]
[B]

sudo apt install arandr

arandr

[/B]Post a screen shot of what you see too please ........ it may just say default .... with no other choices.

---

### Post by roadrash on 2018-12-03
Oh damn I thought it was working. If thats the case then I bet if i increase the resolution the video playback suffers hugely.  I still want to get the proper driver installed and enabled if we can.  I think there is a little progress but it needs a bit more work.  What is arandr?  i did have a play with some use of of xrandr & changing xorg.conf earlier in my attempts to get a usable resolution when i first started with trying to get the driver to work but got nowhere.  I don't want so break anything now or mess anything up really by editing config files etc.
What is this error youve seen all about? is the same problem i have?

---

### Post by 23dornot23d on 2018-12-03
Well I was trying to stay off the thread - to let the one person show the way - so to speak ...... otherwise - we may go off on a tangent .....

**arandr** is a graphical display of your sceen and there is no editing of files involved in it ......... 
[https://christian.amsuess.com/tools/arandr/](https://christian.amsuess.com/tools/arandr/)
but if you want to wait for Mc4man to add some more
and just follow the one lead then do so ... as I do not want to move you away from what you are doing ........ but had to say its not using nvidia yet
and the errors I have seen have been discussed in many places on the web ........

---

### Post by mc4man on 2018-12-03
> **roadrash said:**
> Hey guys I think we are onto something here.  After that last failure and no log file.  I went to recovery root terminal and did a apt purge nvidia* then did a apt autoremove and it took a lot out. So I rebooted and installed the 390 driver again, rebooted and this time it booted to a desktop although very low res again. So I checked the drivers again and it showed the 390 driver installed.  I then looked in the /etc/X11/ folder but there was no xorg.conf or xorg.0.log so i opened  terminal and issued a sudo nvidia-xconfig.  This created a xorg.conf file and then rebooted again.
Its still in low res but went to utube and videos played smooth so hardware acceleration is working.
Here is the output of inxi -SG

```
 System:    Host: jon-desktop Kernel: 4.15.0-39-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Graphics:  Card: NVIDIA GF100 [GeForce GTX 480]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 128 bits)
           version: 3.3 Mesa 18.0.5

```


Well you are not using the nvidia drivers, seems to be just nouveau. As far as OpenGl it's using llvmpipe. So after all that it's just the same as what you'd see after a fresh install (compare your inxi -SG  from this post (106)  & post 103, exactly the same.


I've only laptops now so can't say why the driver won't load for your machine, maybe look into removing all of the packaged nvidia driver and install the upstream driver
(- different process, research on how to do so before attempting.

This is the upstream driver for your card
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)

---

### Post by mc4man on 2018-12-03
Out of curiosity what does this report?
```
cat /proc/cmdline
```

---

### Post by roadrash on 2018-12-04
> **mc4man said:**
> Out of curiosity what does this report?
```
cat /proc/cmdline
```

her you go...

[cat]cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.15.0-39-generic root=UUID=21ee5a99-e0d6-4062-b94b-2c8ff4ec7d34 ro nomodeset quiet splash vt.handoff=1
[/code]

Cant nvidia be forced if its possible maybe blacklist nouveau or something?
Can you give me a easy way of getting a higher resolution to work with 640x480 is awkward

I just did a check for updates and noticed there was a message pop up saying "configuring nvidia-dkms-390" should it do that checking for updates?  I didnt do the updates because it was a "Ubuntu base" and I know this in the past has broke the nvidia driver.

---

### Post by oldfred on 2018-12-04
You need to remove the nomodeset from boot in grub menu once nVidia driver is installed.
The nomodeset often was required to get video with nVidia before driver was installed.

And this should show if installed into kernel.
       dkms status

---

### Post by roadrash on 2018-12-04
> **oldfred said:**
> You need to remove the nomodeset from boot in grub menu once nVidia driver is installed.
The nomodeset often was required to get video with nVidia before driver was installed.

And this should show if installed into kernel.
       dkms status

After that message "configuring nvidia-dkms-390" during a check for updates and did not do, I shut the computer down.  When I returned and booted it up it crashed again like before with the message "waiting for a process to end etc etc" and it was locked up.  I had to reboot to a recovery terminal and do a purge nvidia* to get back again to a desktop.  If I try to install the nvidia driver it doesn't kow show installed like it did that one time and is just as usual not booting past the "waiting etc etc" message.  I have purged the nvidia driver again and have applied the Ubuntu system update now, seeing as its not going to break anything now and its back to where we have always been.  I know what you say about the "nomodeset" setting and I usually have to put that into the boot parameters or my screen crashes like in the attached picture and I hear it booting but there is nothing I can see on the screen and cant find a way ouit of it until i press reset button.  Your right that when the nvidia driver is installed, nomodeset is not needed but I am back with the nouveau driver again and when I did as you asked oldfred, it just crashed the display as it normally does without a nvidia driver installed.
Here is trhe picture of the crashed screen I get when booting without nomodeset.

---

### Post by oldfred on 2018-12-04
Recovery mode boot has nomodeset built in. And then you can get terminal (with or without Internet) to repair or add drivers.
Does this show nVidia fully installed?
dkms status

---

### Post by roadrash on 2018-12-04
> **oldfred said:**
> Recovery mode boot has nomodeset built in. And then you can get terminal (with or without Internet) to repair or add drivers.
Does this show nVidia fully installed?
dkms status

Sorry no.  for some reason I cant boot my pc without the nomodeset put into the startup.  If its not there luke when I am using the live insall dvd I have to put it in.  Its the same after I have installed ubuntu, I have to add it before every boot or my screen lockls like in that picture.  Its always been a nuisance.

Is it possible to try one of the older nvidia drivers like I had to do in windows.

---

### Post by mc4man on 2018-12-04
With nomodeset you'll never use the nvidia drivers. (and some other less than ideal like resolution..
Typically some people have to initially enable it to boot, then they install the prop drivers, remove nomodeset if on the kernel command line and go on their merry way.


Does your computer have a setting in the bios/setup to disable integrated graphics ( iGPU) or to only use discrete graphics?  If so disable it or set to only use discrete and then maybe you can boot with nvidia drivers without nomodeset.

---

### Post by roadrash on 2018-12-05
My motherboard does not have onboard graphics.
I  only use nomodest when installing ubuntu.
Once installed i dont use it.

I tried yesterday to get some of the older drivers from nvidia's site to install but they refused.  I did also try installing their latest driver 390 using their install script but it too does the exact same as when its done through the repos and when rebooting after it installs it stops with that same message "waiting for a process to end" this follows messages about "failed to initialize nvidia module" or something similar.
Anyway ive now done another clean install and done all updates so I now have a up to date fresh install again to use.  Whatever is wrong is very difficult to find.  Oldfred I think mentioned we might have to configure and compile our own kernel or somehting very involved like that.  This is something I fancied trying sometime but is beyond at this time.  Please can someone help me sort this, I really dont want to have to use windows on my desktop after all these years of using ubuntu.

May I again say how grateful I am to everyone who has contributed to helping me and surely we must find a answer soon.  mc4man, catkiller, 23dornot23d and oldfred I owe you huge gratitude for your incredible patience right from the start with this.  Fingers crossesd we will win in th end.

**Another fresh start:**
My desktop as it is now has Ubuntu 18.04.1 installed
All updates done
nothing extra installed yet.

**My opinion so far:**
The best results we had so far were when using lightdm and mate desktop. ( I was Using Ubuntu Mate or Mint Mate edition in the past too when i had the nvidia installed)
I personally think we should be using the nvidia 304 driver as we have had it working this that one. Anything newer has failed.

We now have another clean slate to work with so would someone who has followed this make a suggestion as to what we do first.  My direction would be to install lightdm & mate desktop as they have worked and then maybe use the nvidia 304 driver.  But I am not going to lead on this as I am not the expert here so please tell me what your opinion is on this?

---

### Post by 23dornot23d on 2018-12-05
>  

Searching the web for this gives nothing in my own search results. **304 driver gtx480 solved**  I have searched high and low for solutions to the gtx 480 and the last 2 links to it were not good. 

    

You posted this screen shot ........ early on in the thread ...... which was the only place I thought you had almost got there as **it did say at the bottom of the screen shot that it was using the proprietory driver** .... we found in the logs that it was not the case. ( if indeed the logs were correct ) **something was not or it was being blacklisted for use after the reboot.**

Maybe it was the screenshot - as the screenshot and remarks back are not as detailed as any logs are )  [https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818](https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818)  

I would like you to choose this again now that you do not have anything blacklisting the nvidia card ........  So you just basically choose the 340 driver ....... and see what happens.  ...... this will then rule out that it was not being blacklisted. ( one more tick in a box to say that it was tested properly ) as it may have been blacklisted back then by another configuration file ....... 

Now it should not be **blacklisted** as you have done a totally fresh install again ........  Possibly the last chance at getting the card going .... unless anyone else has any other ideas -  I am no expert on Ubuntu as such - because I use many Operating Systems and try to keep my own systems working .... which nowadays are nearly all without systemd and run on my laptops.   

( so if you want to wait for more replies by people that are experts and use Desktop systems then please do so )  

They may also know how to get the older driver working the 304 ..... but on windows I found this link also. [https://us.download.nvidia.com/Windows/309.08/309.08-win7-winvista-desktop-release-notes-whql.pdf](https://us.download.nvidia.com/Windows/309.08/309.08-win7-winvista-desktop-release-notes-whql.pdf)  We also still do not know which driver it was that you used to get it working in Windows 7 ..... maybe that was the last one that it ever did work properly with - who knows.

The very best of Luck .....

---

### Post by roadrash on 2018-12-05
The drivers it looks like it was the 340.52 - 64 bit driver I used in windows 7 but its showing in the settings its 342.## so it must have updated itself after install.

23dornot23d I thought you were an expert, you have been one of the most helpful and right from the start.  You certainly learn't me a lot.
I sat down earlier and read right through everything We & I have done making notes and we have pretty much covered all drivers Ubuntu offer and I even tried some from Nvidia themselves.

I have tried to replicate that time I got one of the drivers showing installed even though in reality it wasn't but cant seem to do it again. It got messed up when i accidentally launched the updater and it did some automatic re-configuring itself even though I never did the updates.  The next time I booted it up the driver was gone.
I can try using the 340 driver in Ubuntu on a clean install just to eliminate it but pretty sure it wont work.  But to tick another box I will do it and let you know the result.

So no lightdm or mate then?  Should I do a purge nvidia* first. Also do you want me to run a nvidia-xconfig from a terminal after installing it and should I do it before or after rebooting.

---

### Post by oldfred on 2018-12-05
I think all the posts that 23dornot23d has given you should have worked.
But installing incorrect driver then creates more issues.
I would only install the one correct driver for whichever nVidia recommends for your card. And you have two cards that need different drivers.
If you change drivers you must purge, or the nuclear option of a new clean install.
And be sure to purge everything related to nVidia including bumblebee & xorg configuration files.
 Then check if nVidia fully installer with this, as it must be part of kernel.
       dkms status 
    
Then you must not use nomodeset as that is telling system not to use any driver.

---

### Post by 23dornot23d on 2018-12-05
> 

So no lightdm or mate then?  Should I do a purge nvidia* first. 
Also do  you want me to run a nvidia-xconfig from a terminal after installing it  and should I do it before or after rebooting.                 



[https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818](https://ubuntuforums.org/attachment.php?attachmentid=281810&d=1543434818)

These are the commands I would like you to follow to check the 340 driver out again ... 
just check that no bbswitch has managed to get in there - then you can continue once sure of that.

**dkms status**

> 
Should I do a purge nvidia* first. 


You can do that - ( if you think after doing the next things it will cause you problems if you do not )

It may be better to leave it though as you will then get in using nouveau ( possibly )

Looking at the background in the screenshot - you were using Mate .... so we shall install that.
We will also load lightdm as that gets rid of the wayland problem.

[B]sudo apt install lightdm
[/B]
[B]sudo apt install mate

reboot here .... you may still have to go in using the second menu option at boot ..... but hopefully not ........[/B]

Then go into mate and load/select the driver in **additional drivers** as before and post back a screenshot or let us know its the same as the one in this thread.

Then we will check some things out before we go any further - do not reboot and do not purge anything ...... at this point .... 

possibly - we will be able to check the systemd journalctl here and see if it has installed or what it is actually using at this point.

Anybody watching - that sees any problems with any of the above - please speak out now ..... thank you.

I have just realized that the time is late now - so if you want to do this tomorrow - let us know and I will try to get
on at a time when you are on tomorrow ..... because ..... we do not want to reboot till we know a few things about what is
actually happening and it may be in the logs and easy to post back while you have a screen up and running.

---

### Post by roadrash on 2018-12-05
> **oldfred said:**
> I think all the posts that 23dornot23d has given you should have worked.
But installing incorrect driver then creates more issues.
I would only install the one correct driver for whichever nVidia recommends for your card. And you have two cards that need different drivers.
If you change drivers you must purge, or the nuclear option of a new clean install.
And be sure to purge everything related to nVidia including bumblebee & xorg configuration files.
 Then check if nVidia fully installer with this, as it must be part of kernel.
       dkms status 
    
Then you must not use nomodeset as that is telling system not to use any driver.

Ok did everything you suggested oldfred. Here are the steps I took & resultes:

1) opened teminal - apt-get purge nvidia*
2) checked for xorg,config - none 
2) opened driver mangager and installed Nvidia 340.
3) dkms status confirmed Nvida driver installed.
4) reboot
5) At startup press "e" and check script - I found nomodeset was present so I removed it and pressed F10 to continue.
6) Starts to boot but stalls before desktop with the usual waiting for a process (see picture)
7) Pressed reset
8) Entered Recovery mode root terminal and did dkms status and nvidia driver still loaded (see picture) (Stupid picture uploader wont upload picture for some rteason)
anyhow it says:  **NVIDIA-340, 340.107, 4.15.0-42-generic, x86_64: installed**
9) Now what??

---

### Post by 23dornot23d on 2018-12-05
Its stopped on gdm .......... ( so its the wayland problem now ..... )

I think I managed to break out of this once too using **Ctrl+alt+escape**  repeatedly - to get to a console login ... [B]Ctrl+alt+F1
[/B]( you could nearly always break out here before Systemd was implemented )
But it looks like it might work this time ....... ;) ...... if the driver is ok ....... and you can get to load lightdm up ....

Option 2 - at boot ..... **Advanced options** ..... go in safe mode ........ but do not remove anything now .....

Load up **lightdm** ....... ( one step at a time ) ..... 

**sudo apt install lightdm**

see if when you reboot it gets past the gdm problem ...... really should have had lightdm in place before the boot process was initiated that last time.

---

### Post by roadrash on 2018-12-05
I tried that but for some reason when try to install lightdm from the root terminal it complains it cant find some packages and suggest adding --fix-missing to the comand.  Ive had this hapen quite a few times.  But if i try to install telhe same item from a desktop terminal it finds everything.

---

### Post by 23dornot23d on 2018-12-05
Yes - maybe the network is not connected at this point ..... sorry to say

[B]Unless you can get in from the boot menu 2nd option Advanced options .... then the second option on there .... safe mode or whatever it is called.
[/B]
or Old Fred is still on and can see any other ways to get past the problem you have ........ 

Try again tomorrow ........ but load lightdm up before reboot and see what happens ...... see post #125 ....

or we can have a go when we are both on ..... needs a clean install then load/setup lightdm ..... then we will see if the driver will load in ok

I prefer to load mate then go into additional drivers to select the nvidia card too ..... but if you can get to additional drivers from another desktop
environment - then that is your choice - as god only knows how many times you have been through the routine now ...... suppose you could do
it all in your sleep at the moment too,

---

### Post by CatKiller on 2018-12-05
> **23dornot23d said:**
> I prefer to load mate then go into additional drivers to select the nvidia card too
Installing with apt from the terminal will give more information. We had at least one report in the thread of the driver installation being hard terminated because of a lack of information about what the install scripts were doing at that point.

---

### Post by 23dornot23d on 2018-12-05
I tell you what CatKiller ..... you describe exactly how you would like to do it .......... 

your turn now ...... please give the commands you want to see the OP do.

I will sit it out again .......

---

### Post by CatKiller on 2018-12-05
> **23dornot23d said:**
> I tell you what CatKiller ..... you describe exactly how you would like to do it .......... 

your turn now ...... please give the commands you want to see the OP do.

I will sit it out again .......

Nah, you're good. I think I gave my suggestions a few pages back. More information is better than less information, that's all.

---

### Post by 23dornot23d on 2018-12-06
> 
More information is better than less information, that's all.                 


Yes you are right ..... the logs give the clues to what to do next .......

One thing that seems to keep happening is the lock up before getting into the desktop manager ....... 

But the cause was shown last time to be possibly be gdm ..... then maybe the devs know exactly why it would do that.

If it could be programmed to post the log back for the user automatically to a pastebin for use on the forum - that would be good.

Maybe .... the error is easy to find ....... but so far everytime it gets to using the screen driver for nvidia - it stalls or goes on hold.

@CatKiller .... your comments are useful .... but more information would also be good to find out exactly what commands could be
used to get to information after the on permanent hold appears on the screen - its something I do not know enough about.

the journalctl --boot ........... looks interesting ...... if it can give information directly to the user for posting after the computer
gets to the point of no return ....... in a format ...... or **one simple command that the user can type in to put the information onto the forum**. 

knowing how to use systemd and get the information required out of it - at hold ...... many times now the threads show the graphics
problems for Nvidia GTX cards ..... maybe its just these cards with GTX ..... so is the driver not quite right yet.

Maybe only a dev could answer that and know **exactly how to track down what is going on** when it is possibly a graphics driver failure.

Which seems to be increasingly looking like the case after all of these posts .....

If we do a search on **nvidia gtx ubuntu solved - **we will see how many have been solved .... 

This search probably also shows the consistency of problems with that type of gtx card - 
seeing so many seem to be having to find solutions for
these cards[B] ... 
[/B]

---

### Post by CatKiller on 2018-12-06
> **23dornot23d said:**
> @CatKiller .... your comments are useful .... but more information would also be good to find out exactly what commands could be
used to get to information after the on permanent hold appears on the screen - its something I do not know enough about. 

The install scripts would generally add the *nvidia* kernel module and blacklist the others. That hasn't been happening. Using the graphical tools hides a lot of useful information to make it friendlier. At the point the OP interrupted it, the script could have been doing *something*, or it could have a problem we can fix, or it could have hung as the OP thought. There's no way to know, because it's hidden.

Running an apt install from the command line reveals that information. That's the beginning and end of my point there.

If the OP has another computer they can SSH from, that might be useful, too. That way, they wouldn't need to reset everything to be able to post information here. The terminal output and logs would be displayed on an unaffected machine.

---

### Post by roadrash on 2018-12-06
Hate to say it we are no further forward and I eneded up having to do yet another complete re-install.  Basically when after I installed the Mate desktop through recovery mode I could not find a way of switching from the default Gnome to Mate.  Normally its done by logging out and logging into Mate from the login screen but there is no way to do it from a terminal.  I spent hours today trying to do its searching the we everywhere but it seems there is no simple way.  Anyway after the re-install I did everything again and had the nvidia driver showing as installed and then installed mate desktop and logged out of gnome and into mate desktop & then installed lightdm.  I then rebooted and check in recovery mode root terminal if the nviida driver was still there ad it was.  So I carried oin andf rebooted only to be greeted with the usual black screen with little cursuor flasging which we know now is that dumb waiting for a process to finish message.
It seems we cant get to any graphical desktop with the driver installed.
Look I wonder can we try this with the nvidia 304 driver as we have had it working in earler ubuntu xenial.  Can you tell me how I get the driver to show in driver manager?

---

### Post by 23dornot23d on 2018-12-06
> 
I did everything again and had the **nvidia driver showing as installed ** 
and then** installed mate desktop** 
and** logged out **of gnome 
and **into mate  desktop** 
& then **installed lightdm**.  

I then rebooted and check in  recovery mode root terminal if the nviida driver was still there 
and it  was.  

So I carried on and rebooted only to be greeted with the usual  black screen with little cursor flashing 


Sounds like the graphics driver failed as it should have gone into lightdm here ........... 
but if anyone knows of another reason it did not go in - please say ....... if any suspicion of something else ....

> 
Normally its done by logging out and logging into Mate from the login screen but there is no way to do it from a terminal.  


**$ startx mate**

might have got you directly into mate ...... but if its the graphics driver then that also would fail ..... with a message though that might be useful.

-----------------------------------------------------------------------------------------------------------------

This is the only thread I can see where they might have had success ....... 

I am not saying to use it though as everything is in your own hands and responsibility for such an old driver .....

The discussion mentions all the problems and its only at the end they do come up with a solution - but its for a different card to yours ........... you takes your own risks with things
like this ......... they mention security risks ....... but there may be others too ....... have a read - that is all I can say for this. There are 3 pages to the full link below .... for info only

[https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787?page=3](https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787?page=3)

---

### Post by roadrash on 2018-12-06
I did notice something in comon with me and that was they used the 304 driver which is the driver i was using when i got it working with the 9800GT. They also used the mate desktop again like me.  I was using Xenial then but when I use 18.04 and the GTX480 i dont get given the option of using the 304 driver and only offerd 340, 348, & 390.  The 304 driver does support the GTX480 as well so I reckon there is a much better chance it will work with the 304 driver if I could get it to show up in the driver manager.  What do you think?

---

### Post by CatKiller on 2018-12-06
The graphics drivers PPA has a build of 304. I think 340 would be a better bet, though, since it still supports both cards.

---

### Post by roadrash on 2018-12-06
> **CatKiller said:**
> The graphics drivers PPA has a build of 304. I think 340 would be a better bet, though, since it still supports both cards.

I am only going to use one of the cards, The GTX as its the newest and most powerful.  Ive never had any driver after 304 working even with the 9800GT that worked in ubuntu for years before all this started a couple of years ago.  I notice in that install 23dornot23d found they had to put the ubuntu version of libvdpau into the kernal.  This was because they did a manual install from a terminal but if they had done it from ubuntu's own driver manager it would have done that automatically.  What changes to the repos or exra repos do i need to add to get the 304 driver to show up in Ubuntu 18.04.
Its a box we havent ticked yet either using the 304 driver and its easier to do it through ubuntus driver manager than do it manually and of course it can be undone & purged too if it doesnt work.  If I do it manually myself and it doesn't work like I did recently there is no eay way to undo it and i ended up doing another re-install.   What do you think??

---

### Post by CatKiller on 2018-12-06
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Gives instructions on how to add the PPA. You can use ppa-purge to remove everything that you've installed from a particular PPA. No need to reinstall everything. 

Use ```
sudo apt install nvidia-graphics-drivers-304
``` to install the drivers rather than the graphical tool for the reasons I've already said.

---

### Post by oldfred on 2018-12-06
Are you sure the 304 driver is what you want. 
It really is only for much older cards.
[https://www.nvidia.com/object/IO_32667.html](https://www.nvidia.com/object/IO_32667.html)

---

### Post by roadrash on 2018-12-07
> **23dornot23d said:**
> Sounds like the graphics driver failed as it should have gone into lightdm here ........... 
but if anyone knows of another reason it did not go in - please say ....... if any suspicion of something else ....



**$ startx mate**

might have got you directly into mate ...... but if its the graphics driver then that also would fail ..... with a message though that might be useful.

-----------------------------------------------------------------------------------------------------------------

This is the only thread I can see where they might have had success ....... 

I am not saying to use it though as everything is in your own hands and responsibility for such an old driver .....

The discussion mentions all the problems and its only at the end they do come up with a solution - but its for a different card to yours ........... you takes your own risks with things
like this ......... they mention security risks ....... but there may be others too ....... have a read - that is all I can say for this. There are 3 pages to the full link below .... for info only

[https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787?page=3](https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787?page=3)

Well I had a good go at this and I ran into the exact same troubles the the article you found 23dornot23d with unmet dependencies problems for packages like "xorg-video-abi-11" so I will obviously have to follow that guide to get the 304 driver installed.  That was very helpful and I learned why they had to do oit that way too.

> **oldfred said:**
> Are you sure the 304 driver is what you want. 
It really is only for much older cards.
[https://www.nvidia.com/object/IO_32667.html](https://www.nvidia.com/object/IO_32667.html)

I really dont know oldfred but as nvidia dropped support for some older cards it makes sense to use a driver that we have had working along with others too and had had success with. If it dont work and even breaks my system again, whats another clean re-install for the ?????teenth time and if it gets results it will have all been worth it.
Here goes let you know the results

Bit unsure what to do a this bit of the instructions:

> 
# cat << END > /etc/modprobe.d/disable-nouveau.conf
blacklist nouveau
blacklist vga16fb
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist amd76_edac
options nouveau modeset=0
END
# update-initramfs -u
# reboot


I obviously execute sudo -i

Then I added each line one at a time into the file and then when finished type END to exit
then executed from the command line:
update-initramfs -u
reboot

I get errors and the file /etc/modprobe.d/disable-nouveau.conf is empty.

Or was I supposed to enter the sudo -i
then select everything as a block down to and including "reboot" and enter it at the command line as one long command. I tried this but also got errors.

either way I get errors.  When I got the errors I googled the sudo -i command which made me realise I may have been meant to enter everything after it as one single command.

its not made obvious to someone not fluent in all linux command line conventions.
Ive got the drive extracted into a and patched it but the "update-initramfs " option did something so I dont want to reboot in case its broke something so I am leaving my PC turned on at this point until someone responds.

---

### Post by CatKiller on 2018-12-07
That command is to use cat to insert everything before the word END into that file, which is a very weird way of doing it.

```
sudo nano /etc/modprobe.d/disable-nouveau.conf
``` would simply open the file in a text editor.

Edit: when the system is pulling itself up by its bootstraps (which is where the term booting comes from) it is not yet able to do anything complicated like run a complex program or traverse to arbitrary files. It needs everything it's able to use to be made available and simply organised in an Initial RAM FileSystem. That's what you're doing there.

I'm not sure *why* you're doing that, rather than letting the install scripts work, but that is what you're doing.

---

### Post by roadrash on 2018-12-07
So i dont need the word END in the file and i execute those other 2 comands with a # in front from the command line after saving the file.

---

### Post by CatKiller on 2018-12-07
> **roadrash said:**
> So i dont need the word END in the file and i execute those other 2 comands with a # in front from the command line after saving the file.

That is correct.

---

### Post by roadrash on 2018-12-07
Well that didnt work either and it all seemed to go as it should. It boot up to login and then the screen goes black and then the monitor loses signal and goes on standby.  What a shame.  Well had to try it just to eliminate that possibility.

I have had that Asus motherboard arrive but there is no guaratee it will work as it has onboard nvidia graphics.  Still it would be nice to resolve this if possible mainly because this asrock motherboard is rock solid reliable and has plenty of  connectivity for me testing things.  What do you say??

> **23dornot23d said:**
> Sounds like the graphics driver failed as it should have gone into lightdm here ........... 
but if anyone knows of another reason it did not go in - please say ....... if any suspicion of something else ....



**$ startx mate**

might have got you directly into mate ...... but if its the graphics driver then that also would fail ..... with a message though that might be useful.

-----------------------------------------------------------------------------------------------------------------

This is the only thread I can see where they might have had success ....... 

I am not saying to use it though as everything is in your own hands and responsibility for such an old driver .....

The discussion mentions all the problems and its only at the end they do come up with a solution - but its for a different card to yours ........... you takes your own risks with things
like this ......... they mention security risks ....... but there may be others too ....... have a read - that is all I can say for this. There are 3 pages to the full link below .... for info only

[https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787?page=3](https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787?page=3)

That was a great find 23dornot23d and i read all through the 2nd part and like with me it didnt work for everyone. It probaby would have worked with the geforce 9800GT but not with the GTX480.  But even at the very end there was someone who succeeded with a GTX750 so i am going to try a few of these.  Has everyone else given us on this now?   Anyway thanks for the help everyone  23dornot23d there is still a chance this could still work even trying this process using the latest drivers like the 340 one as someone else did.  What do you think?

[QUOTE=CatKiller;13822008]/quote

Well I have had to give up myself now after trying everything in those articles 23dornot23d found.  It seems there must be a possible issue with the way that motherboard handles its PCI/e & 2 AGP sockets.  I have now changed over to that Asus P5G41T-MLX motherboard and its running nice using its onboard intel graphics chip so may not need those Nvidia GTX4800 or 9800GT grahics cards.

Well thanks anyway everyone but even my extreme patience eventually ran out.

---

### Post by 23dornot23d on 2018-12-09
Well glad to hear you have a system running now ..... no doubt it picked up the intel quite easily - which should always be the case.
Glad you are sorted now and can use Ubuntu .... best of luck and thanks for all the nice comments throughout as well as being patient
the new board sounds good too ..... :popcorn:

---

### Post by roadrash on 2018-12-09
> **23dornot23d said:**
> Well glad to hear you have a system running now ..... no doubt it picked up the intel quite easily - which should always be the case.
Glad you are sorted now and can use Ubuntu .... best of luck and thanks for all the nice comments throughout as well as being patient
the new board sounds good too ..... :popcorn:

you were a better expert on linux than i will ever be.  lol.  cheers!

---

