---
title: "low graphics mode on ubuntu 16.4"
date: 2017-02-28
forum: General Help
---

### Post by weirdygeekpsych on 2017-02-28
Hey friends,

A problem with my computer graphics mode. Before the low graphics problem , whenever I entering into GUI I see an error as " app armor intialization : LSB " which goes off in seconds  
and then I will get GUI login as usual. after the usual login, I checked my SE linux status which is in permissive mode, early it was in enforcing mode. but after making it in enforcing mode, low graphics mode error started to occur.

four options I got, 

1) try to start with normal graphics mode
2) Reconfigure
3) troubleshoot error
4) exit to console login.

1st option starts the process again to low graphics mode.... it does nothing

2nd option reconfigure takes me to two set of options 
       
     2a) generic system
     2b) backedup config

both does nothing .. not even a react


3rd option troubleshoot error takes me to 3 option

    3a) show startup error
    3b) show error log
    3c) seriously I forgot the 3rd option in this issue.

but those 3 also doesn't react a bit.

4th option exit to console login
  
    4a) goes to tty1 login... but when i tried to enter with correct username and password, console logouts immediately with a second

After the lot of searching, 

I updated graphics driver from Xorg video-intel .. but ubuntu said graphics is updated.

when i tried to look /etc/X11/Xorg.conf .. actually there is no file exist so i created it with some commands from stackover flow..

Now that file also doesn't exist. Instead it has a file called xorg.conf.failsafe

and that file has the following thing

```


Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


```

Now I installed GDM . now its prompting me to use single display manager program. I am waiting to press okay for it, still didn't press it.

And this is my **lscpu**


```

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 60
Model name:            Intel(R) Core(TM) i3-4160 CPU @ 3.60GHz
Stepping:              3
CPU MHz:               3594.796
CPU max MHz:           3600.0000
CPU min MHz:           800.0000
BogoMIPS:              7183.69
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K


```

and my computer **lspci **

```


00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)



```

Currently am writing this post via recovery mode **dpkg option**, all other options doesn't make my day luck. 

if I come out of recovery this [B]dpkg recovery option

again the Low graphics mode problem starts.?

Can anybody help me out the trouble ? 

I am waiting for the reply without shutting down the system, because entering in to the dpkg recovering options is kind of big work for me i felt. [/B]

---

### Post by neill-rutherford on 2017-02-28
I have had similar sort of problems i found a solution to my problem 
by typing 

sudo service lightdm restart

but then i am using Lubuntu

---

### Post by weirdygeekpsych on 2017-02-28
did you get the normal GUI login back after executing the command.

because I did and it just restarted and problem still continues ????

---

### Post by neill-rutherford on 2017-02-28
yes I did 
try to <Ctrl><alt><f1> and see if you can login
then 
sudo service lightdm restart

---

