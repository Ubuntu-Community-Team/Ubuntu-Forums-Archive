---
title: "touchpad not working"
date: 2014-10-28
forum: General Help
---

### Post by Phil Binner on 2014-10-28
I have an acer one, currently running Ubuntu 14.04.  It has previously run both Windows 7 and Mint.  While I was running mint I tried to change the touchpad settings to reverse the scroll direction, and it stopped working altogether.  Nothing I tried had any effect, so I changed the software, first to Ubuntu and then to Windows 7, and neither the reloads or subsequent adjustments to the settings has any effect.  I have also looked in the bios, but nothing is apparent.

It is always possible that the hardware just failed, and the fact that this happened while I was fiddling with the settings is just a coincidence.  Before I give in to that, however, is there anything I can do at a deeper level to try to fix it.  It is quite a handy machine for doing Sudoku in bed.

I have tried to find some diagnostic in the hope it will mean more to you than to me.

bigbin@Tinybin-Ubuntu:~$ cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0001 Version=0000 
N: Name="Power Button" 
P: Phys=PNP0C0C/button/input0 
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0 
U: Uniq= 
H: Handlers=kbd event0 
B: PROP=0 
B: EV=3 
B: KEY=10000000000000 0 

I: Bus=0019 Vendor=0000 Product=0003 Version=0000 
N: Name="Sleep Button" 
P: Phys=PNP0C0E/button/input0 
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1 
U: Uniq= 
H: Handlers=kbd event1 
B: PROP=0 
B: EV=3 
B: KEY=4000 0 0 

I: Bus=0019 Vendor=0000 Product=0005 Version=0000 
N: Name="Lid Switch" 
P: Phys=PNP0C0D/button/input0 
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2 
U: Uniq= 
H: Handlers=event2 
B: PROP=0 
B: EV=21 
B: SW=1 

I: Bus=0019 Vendor=0000 Product=0001 Version=0000 
N: Name="Power Button" 
P: Phys=LNXPWRBN/button/input0 
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3 
U: Uniq= 
H: Handlers=kbd event3 
B: PROP=0 
B: EV=3 
B: KEY=10000000000000 0 

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41 
N: Name="AT Translated Set 2 keyboard" 
P: Phys=isa0060/serio0/input0 
S: Sysfs=/devices/platform/i8042/serio0/input/input4 
U: Uniq= 
H: Handlers=sysrq kbd event4 
B: PROP=0 
B: EV=120013 
B: KEY=10000 c020000000000 0 0 700f02000003 3802078f870f401 febfffdfffefffff fffffffffffffffe 
B: MSC=10 
B: LED=7 

Any help would be appreciated.

Phil B

---

### Post by JazzPotato on 2014-10-28
Sorry if I have misunderstood, but you're saying that the touchpad no longer works, even in Ubuntu 14.04 and windows seven?

---

### Post by Phil Binner on 2014-10-28
Yes.  It stopped working while I was adjusting the settings while running Linux Mint. Adjusting back did not help so I re-installed the software. I then tried installing Windows 7 and Ubuntu.  No joy.  The fact that I was adjusting the settings when the fault occurred suggests that it is  a software, or at least a firmware, problem, so I looked in Bios.  Still nothing.  I suppose the hardware could just have chosen that moment to fail.

---

