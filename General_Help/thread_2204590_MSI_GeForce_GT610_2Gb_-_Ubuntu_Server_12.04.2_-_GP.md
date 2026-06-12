---
title: "MSI GeForce GT610 2Gb - Ubuntu Server 12.04.2 - GPU problem BOINC"
date: 2014-02-09
forum: General Help
---

### Post by danhansendenmark on 2014-02-09
I have a problem. It has really become a problem. I run several Ubuntu Server 12.04 computers as webservers, mail servers etc. And then I'm running some 6-8 computers with BOINC (SETI/Asteroid).

I just started building a new computer, which has a newer technology, so that the GPU will be used by BOINC as well. Please notice, I'm NOT using any kind of graphical interface.

What I need help for, is how to install the driver for the MSI GeForce GT610 2Gb graphic card on Ubuntu Server 12.04 so that the GPU will run in BOINC.

Please help me install the Linux driver on Ubuntu Server 12.04.2 for use with MSI GeForce GT610 2Gb.

Please notice, that almost everybody who has an idea how to do this, is using the graphical edition, the Ubuntu Desktop 12.04.

I will be forever grateful if someone can fix this issue ;)
And sorry for this newbie question o)

Kind Regards
Dan Hansen
Denmark

---

### Post by oldfred on 2014-02-09
See method #2 for command line install.

I would not recommend any PPA or direct download of nVidia, unless you need the bleeding edge driver from nVidia. But you then have to reconfigure after every kernel update.

       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root


 #To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
#Then for verson installed
sudo apt-cache policy nvidia-319-updates 

You probably want the newest, so not current, nor current-updates, but nvidia-current-experimental-XXX that is available for the Ubuntu version you have installed. Do not mix versions without totally purging an older version before attempting a different one.

 # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett* 
nvidia-settings-experimental-310

---

### Post by danhansendenmark on 2014-02-09
First I tried to install a repository but it went wrong. I now repository from BOINC updates. Then I fixed it by using the purge *nvidia command. And the I did this:

32bit:
wget [http://us.download.nvidia.com/XFree86/Linux-x86/331.38/NVIDIA-Linux-x86-331.38.run](http://us.download.nvidia.com/XFree86/Linux-x86/331.38/NVIDIA-Linux-x86-331.38.run)
sudo chmod 0755 *.run
sudo ./NVIDIA-Linux-x86-331.38.run

Then the letters looked normal again. The problem is, that I dont know anything about the graphic card drivers in Linux. I read a lot about X and DKMS. But its all a very big blur to me. 
I can't understand why its nessesary to install desktop utilities for the Ubuntu Server 12.04 to work with MSI GeForce GT610. To make the GPU useable in BOINC

The results from the first commands you showed me, just in case you can see something wrong:

Command: lshw -c display

 ```
 *-display
       description: VGA compatible controller
       product: GF119 [GeForce GT 610]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
```


Command: sudo lshw | grep -A 11 display

            ```
*-display
                description: VGA compatible controller
                product: GF119 [GeForce GT 610]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
```


Command: lspci | grep VGA

 ```
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 610] (rev a1)
```


Command: xwininfo -root

 ```
The program 'xwininfo' is currently not installed.  You can install it by typing:
apt-get install x11-utils

```

Well, I'm grateful for your help. Any kind of idea how to do this will be a lot better than anything I come up with. I tried 12-14 different ways. But I just don't understand it.


Kind Regards,
Dan Hansen
Denmark

---

### Post by oldfred on 2014-02-09
Did you not install Ubuntu with 64bit?

Do not know anything about BOINC.

I have a GT610 card I am not using and wish I had not purchased it. Should have checked comparisons before purchase. 
The performance is about equal to my old 9600GT card. And even the built in Intel video had similar performance with a lot less power.

---

### Post by danhansendenmark on 2014-02-09
Hi,

No, I didn't install 64bit. I'm a little "out of date" Just didn't think about it. But I too learned, that maybe I should have done that. I can try that, but I don't think it will make a difference. 

BOINC is a worldwide network looking for little green men and large stones up in the air ;) No, much more than that, but it's that too ;)

About the graphic card, yes, I found out about that too. Here's a much better choice, and not so pricey as well. [https://www.asus.com/Graphics_Cards/GT6401GD5L/](https://www.asus.com/Graphics_Cards/GT6401GD5L/)

Well, I just dont know what to do.. I'll hope someone who use Ubuntu Server Edition notice our little talk here ;)

Thanks for your post...

Kind Regards,
Dan Hansen
Denmark

---

### Post by danhansendenmark on 2014-02-09
Hi again Mr. Olfred,

I'm downloading the 64bit version and installing it all over again. Looking for the 64bit driver af Nvidias site. All good so far.
Thanks for the great commands by the way! Really helpful 

[COLOR=#0000cd]*I would not recommend any PPA or direct download of nVidia, unless you  need the bleeding edge driver from nVidia. But you then have to  reconfigure after every kernel update.*[/COLOR]
These things I don't know much about. But I heard about "repository", a little that is, this is small scripts that help you update or is it not?
I would very much like to install the driver in a way that doesn't mean manual driver update every time.. If this can be done. 

Well, I'll get back to you with the results. Please take a look here, and let med know, which is the right way forward. If there is a right way forward of course ;)

[http://www.r-tutor.com/gpu-computing/cuda-installation/cuda5.5-ubuntu](http://www.r-tutor.com/gpu-computing/cuda-installation/cuda5.5-ubuntu)

[http://www.noobslab.com/2011/07/graphical-user-interface-on-ubuntu-11.html](http://www.noobslab.com/2011/07/graphical-user-interface-on-ubuntu-11.html)

Thanks a lot for your help. Thank you!

Kind Regards,
Dan Hansen
Denmark

---

### Post by danhansendenmark on 2014-02-10
Hello again,

A little problem. When I download Ubuntu Server and choose 64bit, its called "ubuntu-12.04.4-server-amd64.iso". WHy is this and is it the right file? I can't find anything else. 

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

[ubuntu-12.04.4-server-amd64.iso]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.iso")            04-Feb-2014 12:18  679M  Server install CD for 64-bit PC (AMD64) computers (standard download)
[ubuntu-12.04.4-server-amd64.iso.torrent]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.iso.torrent")    06-Feb-2014 17:12   27K  Server install CD for 64-bit PC (AMD64) computers ([BitTorrent]("https://help.ubuntu.com/community/BitTorrent") download)
[ubuntu-12.04.4-server-amd64.iso.zsync]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.iso.zsync")      06-Feb-2014 17:12  1.3M  Server install CD for 64-bit PC (AMD64) computers ([zsync]("http://zsync.moria.org.uk/") metafile)
[ubuntu-12.04.4-server-amd64.jigdo]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.jigdo")          06-Feb-2014 17:12  123K  Server install CD for 64-bit PC (AMD64) computers ([jigdo]("http://atterer.org/jigdo") download)
[ubuntu-12.04.4-server-amd64.list]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.list")           04-Feb-2014 12:18   89K  Server install CD for 64-bit PC (AMD64) computers (file listing)
[ubuntu-12.04.4-server-amd64.metalink]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.metalink")       06-Feb-2014 17:26   39K  Ubuntu 12.04.4 LTS (Precise Pangolin)
[ubuntu-12.04.4-server-amd64.template]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-amd64.template")       04-Feb-2014 12:18  5.9M  Server install CD for 64-bit PC (AMD64) computers ([jigdo]("http://atterer.org/jigdo") template)
[ubuntu-12.04.4-server-i386.iso]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-i386.iso")             04-Feb-2014 12:20  661M  Server install CD for PC (Intel x86) computers (standard download)
[ubuntu-12.04.4-server-i386.iso.torrent]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-i386.iso.torrent")     06-Feb-2014 17:12   26K  Server install CD for PC (Intel x86) computers ([BitTorrent]("https://help.ubuntu.com/community/BitTorrent") download)
[ubuntu-12.04.4-server-i386.iso.zsync]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-i386.iso.zsync")       06-Feb-2014 17:12  1.3M  Server install CD for PC (Intel x86) computers ([zsync]("http://zsync.moria.org.uk/") metafile)
[ubuntu-12.04.4-server-i386.jigdo]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-i386.jigdo")           06-Feb-2014 17:12  120K  Server install CD for PC (Intel x86) computers ([jigdo]("http://atterer.org/jigdo") download)
[ubuntu-12.04.4-server-i386.list]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-i386.list")            04-Feb-2014 12:20   86K  Server install CD for PC (Intel x86) computers (file listing)
[ubuntu-12.04.4-server-i386.metalink]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-i386.metalink")        06-Feb-2014 17:26   39K  Ubuntu 12.04.4 LTS (Precise Pangolin)
[ubuntu-12.04.4-server-i386.template]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-server-i386.template")        04-Feb-2014 12:20  4.3M  Server install CD for PC (Intel x86) computers ([jigdo]("http://atterer.org/jigdo") template)


No i386 in 64 bit. ???

Any suggestions ;)

Kind Regards,
Dan Hansen
Denmark

---

### Post by danhansendenmark on 2014-02-10
Hello again,

I found some answers here. Just find it funny to name it AMD. I'll guess I'm not the only one to think this ;)

[http://askubuntu.com/questions/125751/ubuntu-12-04-lts-64-bit-for-intel-core-2-duo-laptop](http://askubuntu.com/questions/125751/ubuntu-12-04-lts-64-bit-for-intel-core-2-duo-laptop)


Any suggestions ;)

Kind Regards,
Dan Hansen
Denmark

---

### Post by danhansendenmark on 2014-02-10
Hello again Mr. Oldfred,

Sorry for all the messages. Now I have  installed and setup Ubuntu 12.04.4 64bit and BOINC again. Still same  result. So now all there is to do, is to try the 64bit driver. But I  know it will not work. I pretty sure. But if you hear from anyone or  find out anything about server edition and graphic cards, please let me  know.

Kind Regards,
Dan Hansen
Denmark

---

### Post by oldfred on 2014-02-10
It is the amd version for 64 because a bit of history. Intel released a totally new 64 bit chip that was not backwards compatible with 32. AMD had a license for Intel 32 bit and built a new 64 bit chip with backwards compatibility. After a few legal squabbles and Intels new chip not doing well, Intel released a 64 chip that was similar to the AMD with backwards compatibility.
 [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)


If you run the commands to install from repository then dpkg will always update kernel to use current driver.

It just is that repository has several versions, current, current-updates and an experimental.
You should check on available versions and then install the one you prefer. See post #2.

---

### Post by danhansendenmark on 2014-02-11
Hello Mr. Oldfred

The processor I chose for my project is: [http://ark.intel.com/products/68316/](http://ark.intel.com/products/68316/)

OK, regarding the driver. I learned that it might be because of "nouveau" which conflicts with the Nvidia driver. From another Linux OS/a friend from SETI, I found a way to "exclude" the nouveau so that the driver could be properly installed, but new issues occurred. Because it's a todo for Fedora there's some differences which I have to solve, before I can make a proper todo for ubuntu server 12.04 (I need myself a todo because I'm building several RACK-mounted servers for my project). 
The Problem is, that to make the GPU work in Boinc (a peace of software  which uses CPU/GPU for crunching numbers and e.g. finding little green  men and asteroids in the univ.), I apparently have to shutdown nouveau,  but then the screen goes crazy. Large letters and a rainbow in the top  of the screen. I use Putty to control my Ubuntu Servers, so it's not a  problem, but something is wrong and I don't like errors. It's a very big  question to me, how the most popular Linux OS in the world and one of  the most used graphic cards type (Nvidia) not has solved these issues  long time ago. I've been searching the web for more than a week now and  still not found the solution. It's a little weird I think ;)
And then there's all this about the many types of drivers and which one is the right one to use. To quote you *"...It just is that repository has several versions, current, current-updates and an experimental.."*.

*"...You should check on available versions and then install the one you prefer. See post #2..*"
Yes, and I'm getting there thanks to you and my friends at SETI. But I only worked with Linux for 1 year+ . So I'm still very much a learner ;)

What is PPA? Exactly what is repository? I read 2 sites about it and is more confused than ever ;(

Maybe I can show you the todo for Fedora, and then maybe you could help me find the Ubuntu commands and paths? I thinks its 3 lines only. And I have suggestions for it, because I'm really trying before I ask. I can get help in here, yes, but you have to read and try before asking. Or at least, that's what I think ;)

---

### Post by oldfred on 2014-02-11
The repository is Ubuntu software which you download with Software Center, command line, or synaptic. It is the standard software that Ubuntu offers and is huge.
Some want the newer version of software particularly kernels & often drivers. Ubuntu repository has been tested and occassionally slightly modified to work with your current version of Ubuntu. But most software is not updated as that is what is a rolling release. But if you want the very newest you can download and compile yourself. But it may or may not work well. Others may compile the software, but has to match your version and that is a ppa. You have to trust the source, just do not download some unknown software. 
I have almost always used just the repository. The only ppa I use is Boot-Repair.

Nouveau is the open source software for nVidia cards. It usually works and recently nVidia has started to help the developers improve nouveau. Otherwise you download the proprietary nVidia driver which is not open source. Some only want to use open source software. Usually they do not conflict, but I have seen where some suggest black listing the nouveau driver to prevent issues.

---

### Post by danhansendenmark on 2014-02-17
Almost solved. Wrong edition, right result!

New attempt to solve the issue "Ubuntu **Server** 12.04.4 64bit - BOINC using GPU - Nvidia driver/GeForce GT610"
Tried installing the desktop edition to see if it really works, when X is installed.

Just finishing the clean installation of Ubuntu **Desktop** 12.04.4  (Desktop, not Server!) Not being able to install the file from BOINC's  download site, I did this instead "apt-get install boinc-client  boinc-manager" which is showed on BOINC helping pages. But this does not  install the newest boinc version. And now a notice tells me to download  and install the new version.... etc. etc. never mind that right now.

But, after installing this desktop version, and installing boinc-client  and boing-manager, and attaching to project using the manager, I checked  to see if the GPU was running. Not yet, so I went on DL the newest  driver from Nvidia 64bit 331.38. and making it bootable "chmod +x  filename.run". Running the file gave me the same problems as when doing  this on the Ubuntu Server Edition! So I went on, doing the same as I did  there, almost.
I started a terminal, ctrl-alt-f2 and logged in, the claiming sudo  rights "sudo su", then "stop lightdm", then running the Nvidia installer  "sh NVIDIA-Linux-x86_64-331.38.run". Some questions are asked during  the installation, I answered "Yes" to [install 32bit libraries etc.],  "Yes" to [reconfigure X-server or something like that] (I will make a  better todo when this is all finished!!)
Rebooting the system and updating the project from Boinc Manager showed  me a 5 running unit. (CPU i5-3470 has 4 cores) and this 5 unit is named:  (0.01 CPUs + 1 NVIDIA GPU). This I also found when doing it with Ubuntu  Server 12.04.4, but the GPU ran for 7 minutes and the the temp. of the  GPU suddenly dropped. This meaning the crunching also stopped. But not  with the Ubuntu Desktop 12.04.4, here the GPU has been running now for  47 minutes and the GPU is still 47 degrees Celsius! 
Here's the log file from Boinc Manager and a screen-dump of Boinc  Manager showing the GPU crunching still after more than 10 minutes.:
```
GPU temp.:
# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 44 C
# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 44 C
# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 45 C
# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 45 C
# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 45 C
# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 46 C


Mon 17 Feb 2014 04:07:24 PM CET |  | Starting BOINC client version 7.0.27 for x86_64-pc-linux-gnu
Mon 17 Feb 2014 04:07:24 PM CET |  | log flags: file_xfer, sched_ops, task
Mon 17 Feb 2014 04:07:24 PM CET |  | Libraries: libcurl/7.22.0 OpenSSL/1.0.1 zlib/1.2.3.4 libidn/1.23 librtmp/2.3
Mon 17 Feb 2014 04:07:24 PM CET |  | Data directory: /var/lib/boinc-client
Mon 17 Feb 2014 04:07:24 PM CET |  | Processor: 4 GenuineIntel Intel(R)  Core(TM) i5-3470 CPU @ 3.20GHz [Family 6 Model 58 Stepping 9]
Mon 17 Feb 2014 04:07:24 PM CET |  | Processor: 6.00 MB cache
Mon 17 Feb 2014 04:07:24 PM CET |  | Processor features: fpu vme de pse  tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts  acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc  arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf  eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16  xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave  avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow  vnmi flexpriority ept vpid fsgsbase smep erms
Mon 17 Feb 2014 04:07:24 PM CET |  | OS: Linux: 3.11.0-15-generic
Mon 17 Feb 2014 04:07:24 PM CET |  | Memory: 3.81 GB physical, 3.95 GB virtual
Mon 17 Feb 2014 04:07:24 PM CET |  | Disk: 54.68 GB total, 48.59 GB free
Mon 17 Feb 2014 04:07:24 PM CET |  | Local time is UTC +1 hours
Mon 17 Feb 2014 04:07:24 PM CET |  | NVIDIA GPU 0: GeForce GT 610  (driver version unknown, CUDA version 6.0, compute capability 2.1,  134215680MB, 134215667MB available, 134 GFLOPS peak)
Mon 17 Feb 2014 04:07:24 PM CET |  | OpenCL: NVIDIA GPU 0: GeForce GT  610 (driver version 331.38, device version OpenCL 1.1 CUDA, 2048MB,  134215667MB available)
Mon 17 Feb 2014 04:07:24 PM CET |  | Config: GUI RPC allowed from:
Mon 17 Feb 2014 04:07:24 PM CET |  | A new version of BOINC is  available. <a href=http://boinc.berkeley.edu/download.php>Download  it.</a>
Mon 17 Feb 2014 04:07:24 PM CET | Asteroids@home | URL http://asteroidsathome.net/boinc/; Computer ID xxxxx; resource share 100
Mon 17 Feb 2014 04:07:24 PM CET | Asteroids@home | General prefs: from Asteroids@home (last modified 15-Oct-2013 16:31:32)
Mon 17 Feb 2014 04:07:24 PM CET | Asteroids@home | Computer location: work
Mon 17 Feb 2014 04:07:24 PM CET |  | General prefs: using separate prefs for work
Mon 17 Feb 2014 04:07:24 PM CET |  | Reading preferences override file
Mon 17 Feb 2014 04:07:24 PM CET |  | Preferences:
Mon 17 Feb 2014 04:07:24 PM CET |  | max memory usage when active: 1949.73MB
Mon 17 Feb 2014 04:07:24 PM CET |  | max memory usage when idle: 3509.52MB
Mon 17 Feb 2014 04:07:24 PM CET |  | max disk usage: 0.00GB
Mon 17 Feb 2014 04:07:24 PM CET |  | (to change preferences, visit the  web site of an attached project, or select Preferences in the Manager)
Mon 17 Feb 2014 04:07:24 PM CET |  | Not using a proxy
Mon 17 Feb 2014 04:07:24 PM CET | Asteroids@home | Restarting task  ps_140207_16280_78_1 using period_search version 10210 (sse3) in slot 0
Mon 17 Feb 2014 04:07:24 PM CET | Asteroids@home | Restarting task  ps_140207_16280_32_0 using period_search version 10210 (sse2) in slot 1
Mon 17 Feb 2014 04:07:24 PM CET | Asteroids@home | Restarting task  ps_140207_16280_73_0 using period_search version 10210 (sse2) in slot 2
Mon 17 Feb 2014 04:07:24 PM CET | Asteroids@home | Restarting task  ps_140207_16280_22_1 using period_search version 10210 (sse2) in slot 3
Mon 17 Feb 2014 04:07:24 PM CET | Asteroids@home | Restarting task  ps_140207_16088_26_2 using period_search version 10111 (cuda55) in slot 4
Mon 17 Feb 2014 04:08:03 PM CET | Asteroids@home | update requested by user
Mon 17 Feb 2014 04:08:05 PM CET | Asteroids@home | Sending scheduler request: Requested by user.
Mon 17 Feb 2014 04:08:05 PM CET | Asteroids@home | Requesting new tasks for CPU
Mon 17 Feb 2014 04:08:07 PM CET | Asteroids@home | Scheduler request completed: got 1 new tasks
Mon 17 Feb 2014 04:08:09 PM CET | Asteroids@home | Started download of input_16304_3
Mon 17 Feb 2014 04:08:11 PM CET | Asteroids@home | Finished download of input_16304_3
```

The  reason I would like to show you this screendump is because when 4 work  units were done after about 50 minutes, the GPU had only completed about  5-6% of it's work unit.
I know this card GT610 is a "not very fast" card. We discussed this at berkeley.edu. But I also learned that GPU's would be much faster doing data  crunching that ordinary CPU's !! I will replace the GT610 with the  faster Asus GeForce GT640 which I was told would be a much better  choice. But how much better will it be?

What is the reason for doing all this work, if GPU's are so much  "slower" than an ordinary Intel i5 CPU? How fast is a "fast" graphic  card" compared to e.g. i5-3470?

We now know that the hardware in this test works, and we know that it  runs on Ubuntu **Desktop** 12,04.4. OK, then why will it not run on Ubuntu  **Server** 12.04.4? The only difference is the graphical environment,  X-server! According to Ubuntu, there's not the difference of the Desktop  Edition and the Server Edition as earlier on, e.g. Ubuntu Server 10.04  v. Ubuntu Desktop 10.04! 
So why is this? Why will the GPU not work properly?

Any suggestions will be greatly appreciated ;)

---

### Post by oldfred on 2014-02-17
If you install the .run from nVidia you are on you own as far as getting it to work correctly. With every kernel update you also have to recompile or actually create a new initramfs. If installed from repository it may not be quite as new from nVidia but will work with Ubuntu and dpkg will auto update on each new kernel.
Perhaps since server does not expect any gui, it is missing some support files?

This site has done a lot of comparisons of the open source drivers for AMD, nVidia & Intel and the closed source drivers with various cards. Just a couple of links but you may need to search for what comparisons you want.
 Ubuntu 13.04 Desktop Comparison: 6 Desktops, 5 Driver/GPU Combinations
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1)
Open Source only drivers - 16-Way Graphics Card Comparison On Open-Source Linux
[http://www.phoronix.com/scan.php?page=article&item=haswell_linuxgpu_16way&num=1](http://www.phoronix.com/scan.php?page=article&item=haswell_linuxgpu_16way&num=1)

 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

 NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)


I also look at this, but it is not Linux. Chart on next to last page gives some idea of relative performance. If within two sections, performance may not be noticeably different. But often you have to read reviews and comments for extra info.

[http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107.html](http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107.html)

---

### Post by danhansendenmark on 2014-02-17
> If you install the .run from nVidia you are on you own as far as getting  it to work correctly. With every kernel update you also have to  recompile or actually create a new initramfs. If installed from  repository it may not be quite as new from nVidia but will work with  Ubuntu and dpkg will auto update on each new kernel.
I see.. This means when updating ubuntu the Nvidia driver will not be updated? If I use repository, it will. is this like the *.nvidia-current? (can't remember the whole line) 

> Perhaps since server does not expect any gui, it is missing some support files?
I made several installation of both the Desktop and the Server, and the GPU can't be recognized before I blacklisted nouveau and others, stopped lightdm and installed the Nvidia driver 331.38. The difference in result between the 2 types of Ubuntu 12.04.4 is, that it runs continuously on Desktop but freezes of don't run at all on the Server edition. Did the same things on both Desktop and Server.  Here's a text-file I made, testing the Server Setup by temp. of GPU and output from "boinccmd --get_tasks". What goes wrong with the Server Setup, is that it seems to run. You can see at [http://asteroidsathome.net/boinc/hosts_user.php](http://asteroidsathome.net/boinc/hosts_user.php) and the same for SETI, that the GPU has been recognized after using my "ToDo". But after some time, the GPU temp. drops! It drops to idle temp.! And the boinccmd output CPU time looks funny, until the temp. drops, then it looks normal for some time, then it freezes, I guess, and suddenly the CPU time starts to increase. The Estimated CPU time gets larger and larger. GPU cold as a ice cube ;(

Here's the text file/my test of the clean installed Ubuntu Server 12.04.4:

```
*****************************************************************************************************
AFTER CLEAN INSTALLATION OF UBUNTU SERVER 12.04.4 64BIT - NVIDIA DRIVER FROM MANUFACTURER - BOINC....
IT LOOKS LIKE IT'S RUNNING. LOOK AT THE CURRENT CPU-TIME, ESTIMATED CPU TIME, GPU TEMP. THE GPU TEMP. 
DROPS WHEN CURRENT CPU-TIME STARTS INCREASING!

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 35 C

1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 0.698044
   current CPU time: 1.010883  <-- IS IT RUNNING? FUNNY TIME STAMP!
   fraction done: 0.004049
   swap size: 17324924928.000000
   working set size: 23929983.999999
   estimated CPU time remaining: 46193.601236  <-- LOOKS LIKE IT'S RUNNING OR SO IT SEEMS AT LEAST!


After 30 sek.:

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 39 C

1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 1.159562
   current CPU time: 1.265546  <-- IS IT RUNNING? FUNNY TIME STAMP!
   fraction done: 0.007859
   swap size: 17325019136.000000
   working set size: 23998459.820312
   estimated CPU time remaining: 46051.810281  <-- LOOKS LIKE IT'S RUNNING OR SO IT SEEMS AT LEAST!


After 1 min.:

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 40 C

1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 1.296961
   current CPU time: 1.395721  <-- IS IT RUNNING? FUNNY TIME STAMP!
   fraction done: 0.009764
   swap size: 17325019136.000000
   working set size: 23998463.967346
   estimated CPU time remaining: 45978.306833  <-- LOOKS LIKE IT'S RUNNING OR SO IT SEEMS AT LEAST!


After 2 min.:

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 41 C

1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 1.431833
   current CPU time: 1.502592  <-- IS IT RUNNING? FUNNY TIME STAMP!
   fraction done: 0.011669
   swap size: 17325019136.000000
   working set size: 23998463.999490
   estimated CPU time remaining: 45916.704743  <-- LOOKS LIKE IT'S RUNNING OR SO IT SEEMS AT LEAST!


After 5min.:

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 42 C

1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 1.705611
   current CPU time: 1.825205  <-- IS IT RUNNING? FUNNY TIME STAMP!
   fraction done: 0.015480
   swap size: 17325019136.000000
   working set size: 23998464.000000
   estimated CPU time remaining: 45735.682079  <-- LOOKS LIKE IT'S RUNNING OR SO IT SEEMS AT LEAST!


After 7 min.:

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 40 C  <-- TEMP. DROPS FAST !!


1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 1.846315
   current CPU time: 24.267430  <-- AND NOW IT LOOKS LIKE NORMAL, COUNTING. BUT FIRST WHEN TEMP. DROPS ON GPU!?!?
   fraction done: 0.017385
   swap size: 17325019136.000000
   working set size: 23998464.000000
   estimated CPU time remaining: 45661.043715  <-- STILL LOOKS NORMAL, BUT THIS WILL STOP DECREASING AND START INCREAS LATER!?!?!?


After 9 min.:

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 37 C  <-- TEMP. DROPS FAST !!

1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 1.846315
   current CPU time: 179.339600  <-- AND NOW IT LOOKS LIKE NORMAL, COUNTING. BUT FIRST WHEN TEMP. DROPS ON GPU!?!?
   fraction done: 0.017385
   swap size: 17325019136.000000
   working set size: 23998464.000000
   estimated CPU time remaining: 45508.722678  <-- STILL LOOKS NORMAL, BUT THIS WILL STOP DECREASING AND START INCREAS LATER!?!?!?


After 10 min.:

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 35 C  <-- TEMP. DROPS FAST !!

1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 1.846315
   current CPU time: 332.599800  <-- AND NOW IT LOOKS LIKE NORMAL, COUNTING. BUT FIRST WHEN TEMP. DROPS ON GPU!?!?
   fraction done: 0.017385
   swap size: 17325019136.000000
   working set size: 23998464.000000
   estimated CPU time remaining: 45357.533616  <-- STILL LOOKS NORMAL, BUT THIS WILL STOP DECREASING AND START INCREAS LATER!?!?!?


1 hour later, approxmately:

# nvidia-smi -a |grep Gpu
        Gpu                         : N/A
        Gpu                         : 34 C  <-- SAME GPU TEMP. AS WHEN IDLE!

1) -----------
   name: ps_140207_16179_23_1
   WU name: ps_140207_16179_23
   project URL: http://asteroidsathome.net/boinc/
   report deadline: Thu Feb 27 23:31:38 2014
   ready to report: no
   got server ack: no
   final CPU time: 0.000000
   state: downloaded
   scheduler state: scheduled
   exit_status: 0
   signal: 0
   suspended via GUI: no
   active_task_state: EXECUTING
   app version num: 10111
   checkpoint CPU time: 1.846315
   current CPU time: 4815.600000
   fraction done: 0.017385
   swap size: 17325019136.000000
   working set size: 24051712.000000
   estimated CPU time remaining: 40951.029791  <-- AND NOW IT LOOKS LIKE NORMAL, BUT DOESN'T CRUNCH! GPU TEMP. SAME AS WHEN IDLE!?

```

Here's what I did when installing the Ubuntu Server. Same as I did with the Ubuntu Desktop:
```

Installation Todo:

0. Take sudo rights
# sudo su

1. Make sure "gcc" is installed by checking version "gcc --version". Install "gcc"
# gcc --version
# apt-get install gcc

2. Reboot
# reboot

3. Download newest/best Linux Nvidia driver!? e.g."NVIDIA-Linux-x86_64-331.38.run" from nvidia.com
# wget http://us.download.nvidia.com/XFree86/Linux-x86_64/331.38/NVIDIA-Linux-x86_64-331.38.run
# chmod 0755 *.run
or
# chmod + x NVIDIA-Linux-x86_64-331.38.run

4. Blacklist nouveau and other nvidia modules. Edit  "/etc/modprobe.d/blacklist.conf" and add "blacklist nouveau" etc. to the  bottom.

# vi /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivat

5. Make needed to install Nvidia driver
# apt-get install make

5. Reboot
# reboot

7. Take sudo rights
# sudo su

8. Install the downloaded Nvidia driver
# ./NVIDIA-Linux-x86_64-331.38.run
```


Another problem by using the downloaded Nvidia driver 331.38, is that lm-sensors output looked like this before I installed the Nvidia driver. I need the GPU output for a shell script I made to control & watch CPU/GPU/HDD's:
```
# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +106.0°C)
temp2:        +29.8°C  (crit = +106.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +26.0°C  (high = +85.0°C, crit = +105.0°C)
Core 0:         +26.0°C  (high = +85.0°C, crit = +105.0°C)
Core 1:         +25.0°C  (high = +85.0°C, crit = +105.0°C)
Core 2:         +25.0°C  (high = +85.0°C, crit = +105.0°C)
Core 3:         +22.0°C  (high = +85.0°C, crit = +105.0°C)

nouveau-pci-0100  <-- THIS DISAPPEARS AFTER INSTALLATION OF NVIDIA 331.38 DOWNLOADED DRIVER!!
Adapter: PCI adapter
temp1:        +31.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)
```

---

### Post by danhansendenmark on 2014-03-11
Hi Oldfred,

It took some time, but finally I did it!

I'm now running a headless ubuntu server, crunching data using Nvidia GT640. Next step, to test if it really runs headless with multiple GPU's. And after that, installing a hardware fan controller. Finishing up the shell script watching the temperature of CPU, GPU's and HDD + RAM and PSU ;)

My advice to people who are trying to make a headless system running cuda. Using the .run installer in a CLI based environment will really make you pull your hair. I got this system to work, but I never, never succeeded in using the .run installer to install cuda toolkit and the driver which comes along!!

When I'm done, I will make a ToDo or people who would like to run e.g. Boinc to crunch data in a headless CLI environment ;)

Thanks for your help...

Kind Regards,
Dan

---

