---
title: "Help!!!!! :("
date: 2007-10-28
forum: General Help
---

### Post by TekMek on 2007-10-28
:confused::confused:Hi,


I have a normal pentium 4 (2.80ghz) processor but the system monitor says i have 2 cpu's (cpu 1 and cpu 2 )and under hardware it says i have 2 pentium 4's under processor 0 and processor 1. I only have one proccesor. My cpu history says i have 2 proccesors running and both are bouncing between 50%-90%. This is a fresh copy of ubuntu that i just installed its not the 64 bit version or the server version just the normal 7.10 version. how can i fix this problem and make it only recognize that i only have one processor. Its causing everything to run extremely slow as far as me opening up applications or doing anything for that matter. I also have 4 gigs of ram and the video card is good to go as far as drivers and stuff. I am a new linux user so any help will be greatly appreciated and you'll maybe have to explain a few things to me barney style so i understand but please help cause i really wanna learn more about this os cause im sick and tired of windows and dont have the cash yet for a mac. Thanx again to anyone who can help. :confused::confused::confused:

---

### Post by TekMek on 2007-10-28
bump:(

---

### Post by hessiess on 2007-10-28
has the p4 got hyperthreding?

in the future, try naming your threds so it gives a breef outline of the problem :)

---

### Post by TekMek on 2007-10-28
no it does not have hyperthreading.

---

### Post by TekMek on 2007-10-28
sorry ill name the threads next time](*,)

---

### Post by GrammatonCleric on 2007-10-28
Are you sure that you don't have a dual core P4 (P4 D)?  Each of the cores will show as a separate processor.   This should speed things up rather than slow them down. What applications are running slow?  What type of hard drive do you have SATA or ATA?

-GC

---

### Post by GrammatonCleric on 2007-10-28
If you drop to a command prompt..

Applications -> Accessories -> Terminal

And type... top.

What processes are showing the most CPU usages?

-GC

---

### Post by TekMek on 2007-10-28
I am positive its a normal single core p4 and im running a 40 gig sata hard drive. I have a dell poweredge 800 server you can go online and check the specs and i have actually looked at the processor before . everything runs slow and i mean everything from the time it boots up to anything i try and run.

---

### Post by GrammatonCleric on 2007-10-28
According to...

[http://www.dell.com/content/products/productdetails.aspx/pedge_800](http://www.dell.com/content/products/productdetails.aspx/pedge_800)

Your processor is Single Intel® Pentium®  4 processors with Hyper-Threading technology.

-GC

---

### Post by TekMek on 2007-10-28
gnome-system-mo @ 41%

update manager @ 90%

xorg @ 52%




those are the top 3 and they keep changing positions on the list

---

### Post by TekMek on 2007-10-28
> **GrammatonCleric said:**
> According to...

[http://www.dell.com/content/products/productdetails.aspx/pedge_800](http://www.dell.com/content/products/productdetails.aspx/pedge_800)

Your processor is Single Intel® Pentium®  4 processors with Hyper-Threading technology.

-GC

so does ubuntu not support hyperthreading?

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> gnome-system-mo @ 41%

update manager @ 90%

xorg @ 52%




those are the top 3 and they keep changing positions on the list

Ok, are you updating or upgrading your server?  If not kill update manager.  from a command line run....

sudo killall update-manager

What does "top" show now?

-GC

---

### Post by TekMek on 2007-10-28
gnome-system-mo @ 85%

Xorg @ 50%

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> so does ubuntu not support hyperthreading?

Yes it does.  Hypertheading is an Inet emulates dual processors.  Here's some info on HTT.

[http://en.wikipedia.org/wiki/Hyperthreading](http://en.wikipedia.org/wiki/Hyperthreading)

-GC

---

### Post by TekMek on 2007-10-28
it was updating something for firefox its done now but its still running slow 


btw Thanks for helping

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> gnome-system-mo @ 85%

Xorg @ 50%

Close system monitor. Look at the processes from the commandline using top.

---

### Post by TekMek on 2007-10-28
ok now

xorg @ 50%



it also says i have a total of

103 tasks

1 running

102 sleeping

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> it was updating something for firefox its done now but its still running slow 


btw Thanks for helping


No Problem.   =)

Now when you say running slow.  Can you give an example?  What are you using the server for?  

-GC

---

### Post by TekMek on 2007-10-28
ok like when i click on applications it takes about 10 sec for the menu to drop dow then i click to open the terminal and it takes about 20 sec for it to open up it does the same for everything graphics wise everything runs fine.

---

### Post by TekMek on 2007-10-28
right now the only thing this server has on it is ubuntu i removed windows and just wanted to run ubuntu to learn on it.

---

### Post by Steveway on 2007-10-28
You should disable desktop-effects.
It seems like your system is not powerfull enough to run these at an acceptable speed.
Also post your system specs.

---

### Post by TekMek on 2007-10-28
Form factor Tower only
Processors Single Intel® Pentium® 4 processor at up to 3.8GHz (3.2GHz and up support
32-bit/64-bit) or single Intel Celeron® processor at up to 2.53GHz
Front side bus 800MHz for Pentium 4; 533MHz for Celeron
Cache Up to 2MB L2 for Pentium 4; 256K L2 for Celeron
Chipset Intel E7221
Memory 256MB/4GB ECC DDR-2 400/533 SDRAM
I/O channels Five total: two PCI Express™ slots (2 x 1 connector); two PCI-X® slots
(64-bit/100MHz, 3.3v); one PCI slot (32-bit/33MHz, 5v)
Drive controller Four channel embedded SATA controller
RAID controller Optional CERC SATA 2s, CERC SATA 6ch, PERC 4/DC, PERC 4/SC
Drive bays Four 1" SCSI (hot-plug or non-hot plug) drives or four 1" cabled
SATA drives
Maximum internal storage Up to 1.2TB
Hard drives1 36GB, 73GB, 146GB and 300GB (10,000 rpm) SCSI
36GB (15,000 rpm) SCSI
40GB, 80GB, 160GB and 250GB (7,200 rpm) SATA
Internal storage 10K/15K RPM SCSI drives; 7.2K RPM SATA drives
External storage Dell PowerVault™ SCSI
Tape backup options Internal: PV100T Travan™, PV110T DLT VS160, PV100T DAT72
External: PV100T DAT72
Network interface card Single embedded Broadcom® 5721 Gigabit2 Ethernet controller
Power supply 1 x 420W non-redundant
Availability Highly serviceable chassis; ECC memory; hot-plug SCSI hard drives;
non hot-plug SCSI EasyExchange hard drives; optional hardware or
software SATA or SCSI RAID
Video Embedded video with 8MB SDRAM
Remote management Baseboard Management Controller with IPMI 1.5 compliance,
accessible via network or serial port; optional DRAC 4/P
Systems management Dell OpenManage™
Rack support 3rd party only
Operating systems Microsoft® Windows® Small Business Server 2003, Standard/Premium;
Microsoft Windows Server™ 2003, Standard Edition; Red Hat®
Enterprise Linux® ES v3; Novell® NetWare® 5.1 and 6.5


also i have a ati x1550 256mb graphics card and 4 gigs of ram

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> right now the only thing this server has on it is ubuntu i removed windows and just wanted to run ubuntu to learn on it.

So you are not running apache, mysql or any other server app?  If that is the case.  Let's see how you hard drive is running.

Drop to the command line and run...

sudo hdparm -tT /dev/sda

and post the results.

-GC

---

### Post by pizzy on 2007-10-28
have you got xgl installed?  xserver-xgl.  If you're running desktop effects without this your computer can run slow like you describe

---

### Post by GrammatonCleric on 2007-10-28
Are desktop-effects turned on?

System -> Preferences - >  Appearance -> Visual Effects

Is yours set to "none?"

-GC

---

### Post by TekMek on 2007-10-28
> **GrammatonCleric said:**
> So you are not running apache, mysql or any other server app?  If that is the case.  Let's see how you hard drive is running.

Drop to the command line and run...

sudo hdparm -tT /dev/sda

and post the results.

-GC


/dev/sda:
 Timing cached reads:   2332 MB in  2.00 seconds = 1166.91 MB/sec
 Timing buffered disk reads:  144 MB in  3.02 seconds =  47.75 MB/sec

---

### Post by TekMek on 2007-10-28
sorry if im taking long im using my laptop to type on the forums cause of the slowness.


visual efects are on none thats how it was when i opened it

---

### Post by hamster_billy on 2007-10-28
This may have no relevance whatsoever, but I'll say it just in case.

When I upgraded my ram from 1 Gb to 2 Gb, I had to specify the amount of ram in the grub option, otherwise I had problems. Ubuntu wouldn't boot at all in normal mode, and would boot and run extremely slowly in recovery mode.

I see you have 4 Gb ram and your system is running slowly, so although the problem appears to be with the processor for the small amount of time it'll take it may be worth trying this. My entry in /boot/grub/menu.lst reads:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ea2fc7bf-8894-4710-bd0a-d69d2d816e1e ro nmi_watchdog=0 mem=2011M quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
Stick something like "mem=4000M" in yours, and see if it makes a difference.

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> /dev/sda:
 Timing cached reads:   2332 MB in  2.00 seconds = 1166.91 MB/sec
 Timing buffered disk reads:  144 MB in  3.02 seconds =  47.75 MB/sec

Drive performance looks good. 

I found the following post...

[http://ubuntuforums.org/showthread.php?t=548496&highlight=hyperthreading](http://ubuntuforums.org/showthread.php?t=548496&highlight=hyperthreading)

Do you have any critical data on this system?  If not try the above post.

-GC

---

### Post by pizzy on 2007-10-28
In Administration-Screen and Graphics is the graphics card driver set to the correct model?

Also, go to a terminal window and type metacity --replace.  Just to make sure XGL/ a previous compiz install isn't running somewhere

---

### Post by TekMek on 2007-10-28
ok so how do i make this entry?

---

### Post by TekMek on 2007-10-28
ok so how do i get to this?


The grub boot menu can be edited via:

Sudo gedit /boot/grub/menu.lst

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> ok so how do i make this entry?

from a command line run...

```

 sudo gedit /boot/grub/menu.lst

```

and add

```

mem=4000M

```

to the **end** of the line...

that looks somthing like...
```

kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e71cfcad-796f-48a6-9854-fbaee6832842 ro quiet splash

```

save the changes and from the command line run 

```

sudo update-grub

```

then reboot.

-GC

---

### Post by TekMek on 2007-10-28
i do this through the terminal?

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> i do this through the terminal?

yup... :smile:

-GC

---

### Post by TekMek on 2007-10-28
do i add a space between splash and mem?


sorry for the newb questions

---

### Post by TekMek on 2007-10-28
still running extremely slow, takes forever to boot up too

---

### Post by TekMek on 2007-10-28
You think i should just wipe out the drive and re install again?

---

### Post by TekMek on 2007-10-28
:confused:

---

### Post by GrammatonCleric on 2007-10-28
> **TekMek said:**
> :confused:

Sorry,  Comcast saw fit to delete my static ip address information from that Cable Modem.  After convincing them to restore my cable modem config...funny that everything works again.  =/

That said...if you don't need anything on the server than re-installing Ubuntu is an option.   

-GC

---

