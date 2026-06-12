---
title: "Can't Solve Nvidia Drivers Issue..."
date: 2015-04-27
forum: General Help
---

### Post by cold-m4il on 2015-04-27
one pic = 1000 words.
[http://postimg.org/image/ol2aa4rpn/](http://postimg.org/image/ol2aa4rpn/)
i got the geforce gtx 970 gpu card.
tried everything... installed a lot of things to try and solve this. and nothing...
installed nvidia drivers. and did a lot of config' and etc and just can't solve this thing. it's annoying. i can't use my highest resolution. any solutions?
thank you very much.

---

### Post by QDR06VV9 on 2015-04-27
See if this link [http://askubuntu.com/questions/561295/how-to-use-nvidia-gtx-970-gpu](http://askubuntu.com/questions/561295/how-to-use-nvidia-gtx-970-gpu)
Post #9 solves your problem The Driver nvidia-343 has been replaced with nvidia-346 so note to that.
You may have to remove any of other drivers you have installed to make a clean install.
Regards:D

---

### Post by efflandt on 2015-04-27
The xorg-edgers ppa now has **nvidia-349** package which should work, assuming you do not have remnants from trying any .run scripts directly from nvidia.com. I am using that with my GTX 750 Ti which has the new Maxwell chip.

---

### Post by cold-m4il on 2015-04-28
didn't work, except                                    my system can't start now. trying to connect to my user but it pops back to the log in screen...
usually removing the nvidia drivers solves it but now it's not... lol why is everything is so complicated in ubuntu? can't even install a driver and if i try all the system get messed up...

---

### Post by dino99 on 2015-04-28
'removing' is not enough to get rid of previous install settings, you need to 'purge' the installed driver 

> sudo apt-get purge nvidia*
sudo apt-get install nvidia-349 

349 is from xorg-edgers ppa, 346 is from vivid archive

---

### Post by cold-m4il on 2015-04-28
I DELETED ALL. there is nothing. "bla bla blah" is not installed, so not removed
0 to remove and 18 not upgraded. that's it.
I did everything but it doesn't work. disabled nouveau and all the others. the nvidia driver gives me an error that some driver is still there and can't install, but i did do the blacklist on all the possible drivers and still doesn't work.
i mean it's just a driver ? and no i can't log in and can't turn on the nouveo cause the blacklist needs it to be running... but the nouveo is in the blacklist and black list needs the nouveo to run? XDDD 
That's the problem with ubuntu... you try to solve one problem and on the problem you trying to solve another 10 problems and errors will come... god

---

### Post by cold-m4il on 2015-04-29
help anybody?

---

### Post by Bashing-om on 2015-04-29
cold-m4il; Yeh :

I will give my try at it.
1)
> 
0 to remove and 18 not upgraded.

Let's get the system upgraded so that those '18' are not a factor.
Let's see what is: Post back the outputs - between code tags, please - of terminal commands:
```

sudo apt-gt update
sudo apt-get upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
depending on that output  then comes the next 'upgrade' command .

2) Let's see what you have for fetching the nvidia driver and that there are no conflicts:
post back:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Then we see what we can do to get a driver(s) installed.

it's ubuntu
[INDENT][INDENT][INDENT]where there are solutions, there are no problems
[/INDENT][/INDENT][/INDENT]

---

### Post by cold-m4il on 2015-04-30
i've just formated and installed ubuntu again, new and fresh without any problems. did updates and upgrades. now how to install this cursed driver? i don't want to try again as i did 100 times to do as all the tutorials says cause it only got the system stoping to work.
sorry for my bad english.

---

### Post by Bashing-om on 2015-04-30
cold-m4il; Hello;

A new install and do not want to break it again is completely understandable.
What release did you install ? As 15.04 probably has support for your graphics card, whereas 14.04 does not.

Confirm what we are working with, post back the outputs of terminal commands:
```

lsb_release -a
lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
And then we load up the correct driver modules.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by cold-m4il on 2015-04-30
i installed the 14.04. and i'm using vmware.
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

00:0f.0 VGA compatible controller [0300]: VMware SVGA II Adapter [15ad:0405] (prog-if 00 [VGA controller])
    Subsystem: VMware SVGA II Adapter [15ad:0405]
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at 1070 [size=16]
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at fe000000 (32-bit, non-prefetchable) [size=8M]
    [virtual] Expansion ROM at c0000000 [disabled] [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: vmwgfx

00:10.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI [1000:0030] (rev 01)
    Subsystem: VMware LSI Logic Parallel SCSI Controller [15ad:1976]
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at 1400 [size=256]

PCI (sysfs)  

  *-display               
       description: VGA compatible controller
       product: SVGA II Adapter
       vendor: VMware
       physical id: f
       bus info: pci@0000:00:0f.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=vmwgfx latency=64
       resources: irq:16 ioport:1070(size=16) memory:e8000000-efffffff memory:fe000000-fe7fffff memory:c0000000-c0007fff



 
```
do you recommend to switch to 15.04?

---

### Post by Bashing-om on 2015-04-30
cold-m4il; Yikes 

Exit stage left .. I have no experience with graphics in a VM environment.
That output does show that graphics are identified and a graphics driver is loaded.
As to what is on the host machine to interact with, we do not know .

Regrets;
When I do not know
[INDENT][INDENT][INDENT]can not give advise
[/INDENT][/INDENT][/INDENT]

---

### Post by cold-m4il on 2015-04-30
the only thing i need is to install a driver that support my gtx 970 nvidia card. that's it.
i don't think the problem is related to vmware.

---

### Post by Bashing-om on 2015-04-30
cold-m4il; Well ..
OK;
On the host box .. running ubuntu 14.04;
If you have not to this time installed the PPA;
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346

```

IF you have an alternate PPA installed ( or the OEM driver installed ) purge prior to adding this PPA !

Reboot and see if it works in the host, then see about the VM .

[INDENT][INDENT]should be a YES. it workie
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-04-30
Now I'm understanding the problem, "VM" 
From what i have found.
> VMware VMs don't use native Nvidia or ATI drivers. They basically have a VMware driver that supports accelerated 3D.
 This accelerated 3D uses the native driver on your host machine to improve 3D performance, for example play games, etc.
From Here [http://stackoverflow.com/questions/2260931/cuda-program-on-vmware](http://stackoverflow.com/questions/2260931/cuda-program-on-vmware)
Forgive me Bashing-om I did not mean to jump in, but I thought the information was important:D

---

### Post by Bashing-om on 2015-04-30
runrickus; Hey ...


You do good !
Like:
> 
Forgive me Bashing-om I did not mean to jump in, but I thought the information was important


You are doing better than I . As said, I have no experience in this ares .

[INDENT][INDENT]we are all in this together
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-04-30
> **Bashing-om said:**
> runrickus; Hey ...

[INDENT]_we are all in this together_
[/INDENT]

+1 Agreed ;)

---

### Post by Tulsapoke on 2015-04-30
I hit the upgrade button to 15.04 and also failed to boot after due to my Nvidia card.  I ended up getting to the command terminal and doing a *sudo apt-get purge nvidia** to get rid of all the Nvida drivers and then was able to boot with the generic.  After booting I was able to add back the proprietary driver with the software update GUI.  Hope this helps someone.

This upgrade also busted my sound as well as my DVD drive has disappeared, so far not a fan of 15.04.  I cant remember ever having problems this bad even with betas in the past.

---

