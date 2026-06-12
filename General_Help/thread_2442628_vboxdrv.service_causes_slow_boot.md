---
title: "vboxdrv.service causes slow boot"
date: 2020-05-05
forum: General Help
---

### Post by ajgreeny on 2020-05-05
My fairly new install of Xubuntu-20.04 on a dual core Intel (important parts of inxi output shown below), and with 4G RAM, is booting to a usable desktop quite slowly, though systemd-analyze blame suggests that it is simply vboxdrv.service that is taking all the time; top few lines shown here.  This install is not a VM but a host system running other linux OSs when I need them; they do not run most of the time and certainly not at boot of the host.
```
user@Xubuntu-Laptop:~$ systemd-analyze blame
[COLOR="#FF0000"]2min 1.101s vboxdrv.service[/COLOR]                                                                          
    20.110s snapd.service                                                                            
    15.557s udisks2.service                                                                          
    14.675s networkd-dispatcher.service                                                              
    11.224s NetworkManager-wait-online.service                                                       
    10.697s dev-sda4.device                                                                          
     7.323s accounts-daemon.service                                                                  
     6.593s NetworkManager.service   
```
```
user@Xubuntu-Laptop:~$ inxi -Fzx
CPU:       Topology: Dual Core model: Intel Core i3-4100M bits: 64 type: MT MCP arch: Haswell rev: 3 L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 19952 
           Speed: 798 MHz min/max: 800/2500 MHz Core speeds (MHz): 1: 798 2: 798 3: 798 4: 798 
Graphics:  Device-1: Intel 4th Gen Core Processor Integrated Graphics vendor: CLEVO/KAPOK driver: i915 v: kernel 
           bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 4600 (HSW GT2) v: 4.5 Mesa 20.0.4 direct render: Yes
```
Is it possible to disable the vboxdrv.service from starting at boot and manually start it when needed?

I know it can be stopped and then restarted using commands ```
systemctl stop vboxdrv.service
systemctl start vboxdrv.service
```
as I have run those successfully, but is it possible to stop it running automatically at boot using command ```
systemctl disable vboxdrv.service
``` and then when I want to run VBox use
```
systemctl start vboxdrv.service
```or do I have to enable the vboxdrv.service first with ```
systemctl enable vboxdrv.service
```
Can anyone see problems with doing any of this; I don't see why it should be a problem but don't want to completely mess up my system doing something silly.

---

### Post by ajgreeny on 2020-05-07
Updates and upgrades since installing seem to have sorted out and solved this problem.  I now await an update by Oracle of their repos to include focal versions so I can remove the eoan version, which is all that's  available at present, unless things have moved on since yesterday.

---

