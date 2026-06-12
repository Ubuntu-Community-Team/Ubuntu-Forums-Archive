---
title: "Graphics problem sometimes on boot"
date: 2019-05-20
forum: General Help
---

### Post by hans12345 on 2019-05-20
My wife has a Lenovo All-in-one which has regular (say 1 in 3) Graphics problems on boot.
This is a new problem, the system has been stable for a long time.
System: Xubuntu 18.04 LTS fully up to date. Not using proprietary drivers. Intel hardware, built in graphics.

On those boots that it fails, it is OK at the start, GRUB menu OK, then colored snow.
With the good boots, there is never a graphic problem later

I do not know where to start. I did check RAM, it is good. Plenty of disk space free.
Hardware? It is an all-in-one so this is tricky.
Drivers?
Should I re-install?
Which logs should I look at / post ?

Your advice appreciated.

---

### Post by cruzer001 on 2019-05-20
Lets have a look at your computer specs for a start.  In terminal:
```
sudo apt install inxi
```
Then please post the output of:
```
inxi -b
```

---

### Post by dino99 on 2019-05-20
Sometimes i get such an issue (for a short while at boot time); usually it is related to temperature/humidity weather changes.
It can also be a video cable oxydation; in such a case, unplug/plug is enough to solve the problem.

---

### Post by hans12345 on 2019-05-24
Now I'm in trouble with the wife for not treating her problem with the urgency it needs !

Cruzer : thanks for the idea and here is the output:

```
       
    family@Lenovo-C260:~$ inxi -b
    System:    Host: Lenovo-C260 Kernel: 4.15.0-50-generic i686 bits: 32
               Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.2 LTS
    Machine:   Device: desktop System: LENOVO product: 10160 v: Lenovo C260 serial: 
    N/A
               Mobo: LENOVO model: INVALID v: SDK0F82993 WIN serial: N/A
               UEFI [Legacy]: LENOVO v: IXKT24AUS date: 09/19/2014
    CPU:       Dual core Intel Celeron J1800 (-MCP-) speed/max: 1919/2582 MHz
    Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
               Display Server: x11 (X.Org 1.19.6 )
               drivers: modesetting (unloaded: fbdev,vesa)
               Resolution: 1600x900@59.97hz
               OpenGL: renderer: Mesa DRI Intel Bay Trail x86/MMX/SSE2
               version: 4.2 Mesa 18.2.8
    Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
               driver: r8169
               Card-2: Realtek RTL8188EE Wireless Network Adapter
               driver: rtl8188ee
    Drives:    HDD Total Size: 500.1GB (8.7% used)
    Info:      Processes: 193 Uptime: 3:16 Memory: 1915.0/3935.8MB
               Client: Shell (bash) inxi: 2.3.56 
    family@Lenovo-C260:~$ 
```

Dino: useful comment
It seems to happen mostly on the first boot in the morning.
But strangely, it is Summer now, so why would the temperature be a problem now?
As for "in such a case, unplug/plug is enough to solve the problem", this is an All-In-One so not so easy to unplug.

Your further comments/ideas are welcome (and may help to save my relationship with my wife)

---

### Post by hans12345 on 2019-05-26
Pressure from wife.

So Bump

---

### Post by cruzer001 on 2019-05-26
Sorry for not getting back sooner, I don't always get a email notification.

Since your on the latest kernel and this recently started try going back to the previous kernel.  This can be done at boot in the grub menu.

[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

And I would like a closer look at your video, please post the output of:
```
lshw -c video
```

---

### Post by hans12345 on 2019-05-27
Here it is:

```
family@Lenovo-C260:~$ sudo lshw -c video
[sudo] password for family:
  *-display                 
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:92 memory:90000000-903fffff memory:80000000-8fffffff ioport:3050(size=8) memory:c0000-dffff
family@Lenovo-C260:~$
```

---

### Post by cruzer001 on 2019-05-27
Hello

Did you try the previous (older) kernel?

Something else that is worth a try is "nomodeset".

[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

These suggestions are off the top of my head.  I'm hoping to get lucky.  There may be bug reports on this and I need to take a look around the internet for that and other possibilities related to Lenovo and your graphic card.  However being Memorial Day here I will not have the time for this right now.  So maybe someone else will chime in with ideas or I'll be back with you later.

---

### Post by hans12345 on 2019-05-30
IMPORTANT NEW INFORMATION

The problem remains as described, but it appears it is provoked by a shutdown problem.

My wife had described the problem as one that affected the first boot in the morning. Thereafter, it seemed OK. So I was mislead into thinking of hardware, heating etc.

This morning, as a test, I did 8 boots.

1st,3,5 and 7 failed. 2nd,4,6 and 8 worked.

Now I need to add another fact which seemed irrelevant at the time of my first post.

As noted the PC runs Xubuntu 18 LTS fully up to date. The shutdown process does not complete, and never has. The PC shutdown gets to the final screen and then freezes. So for a couple of years she has closed down by holding down the power switch. Until 1 month ago this did not create a new boot failure. But now it does.

Let me go carefully through the test of this morning.

START
Start boot, Lenovo screen OK, peeps OK, grub screen OK, then coloured snow.
Force shutdown by using power switch.
Start boot, Lenovo screen OK, peeps OK, grub screen OK, then normal Xubuntu start.
Normal Xubuntu shutdown initiated.
Shutdown start OK, then freezes on final Xubuntu screen.
Force shutdown by using power switch.
Go to START

So the problem appears to be created by a partial Xubuntu shutdown. Something must be left in an error state which then provokes the next boot to stop with coloured snow.

This is a strange one. Any ideas?

---

### Post by CatKiller on 2019-05-30
By default, processes are given 90 seconds to finish before they are killed and the shutdown can finalise properly. It is possible to shorten this period. It does seem likely that there is something still running when you yank the power.

---

### Post by dino99 on 2019-05-30
The first place to glance at identfying problem(s) is 'journalctl'

---

### Post by hans12345 on 2019-06-07
The journalctl for the previous boot with the graphics fail is on :

[https://paste.ubuntu.com/p/zYdYXGRX9m/](https://paste.ubuntu.com/p/zYdYXGRX9m/)

---

