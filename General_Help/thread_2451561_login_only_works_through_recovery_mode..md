---
title: "login only works through recovery mode."
date: 2020-10-06
forum: General Help
---

### Post by adelpozoman-f on 2020-10-06
Hello! This morning I was trying to launch Steam and the screen went black and got stuck (No tty2,3,4,...). I restarted the hard way and got to the login screen, put my password and then the black screen again. If before entering my password y go to tty2 and put my username it gets stuck.
The funny thing is that everything works ok if I start in recovery mode (but not the graphics).
I have not done any modification this week, so I dont know what is happening. The system is at date.


[FONT=monospace][COLOR=#000000]Linux RyzenKDE 5.4.0-49-generic #53-Ubuntu SMP Fri Sep 18 09:54:57 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
RX 580, Ryzen 1400, 16GB Ram.[/FONT]

The hardware is allright as I dual boot and gpu and everything works ok on WIN10.

 
lshw -short:
```

[FONT=monospace][COLOR=#000000]H/W path            Device      Class          Description [/COLOR]
========================================================== 
                                system         AB350M-Gaming 3 (Default string) 
/0                              bus            AB350M-Gaming 3-CF 
/0/0                            memory         64KiB BIOS 
/0/26                           memory         16GiB System Memory 
/0/26/0                         memory         Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012- 
/0/26/1                         memory         4GiB DIMM DDR4 Synchronous Unbuffered (Unregistered) 2800 MHz (0,4 ns) 
/0/26/2                         memory         8GiB DIMM DDR4 Synchronous Unbuffered (Unregistered) 2800 MHz (0,4 ns) 
/0/26/3                         memory         4GiB DIMM DDR4 Synchronous Unbuffered (Unregistered) 2800 MHz (0,4 ns) 
/0/28                           memory         384KiB L1 cache 
/0/29                           memory         2MiB L2 cache 
/0/2a                           memory         8MiB L3 cache 
/0/2b                           processor      AMD Ryzen 5 1400 Quad-Core Processor 
/0/100                          bridge         Family 17h (Models 00h-0fh) Root Complex 
/0/100/0.2                      generic        Family 17h (Models 00h-0fh) I/O Memory Management Unit 
/0/100/1.3                      bridge         Family 17h (Models 00h-0fh) PCIe GPP Bridge 
/0/100/1.3/0                    bus            300 Series Chipset USB 3.1 xHCI Controller 
/0/100/1.3/0/0      usb1        bus            xHCI Host Controller 
/0/100/1.3/0/0/1                input          USB Keyboard 
/0/100/1.3/0/0/5                input          USB Receiver 
/0/100/1.3/0/0/6                generic        BCM920702 Bluetooth 4.0 
/0/100/1.3/0/1      usb2        bus            xHCI Host Controller 
/0/100/1.3/0.1      scsi0       storage        300 Series Chipset SATA Controller 
/0/100/1.3/0.1/0    /dev/sda    disk           240GB SanDisk SDSSDA24 
/0/100/1.3/0.1/0/1  /dev/sda1   volume         162GiB Windows NTFS volume 
/0/100/1.3/0.1/0/2  /dev/sda2   volume         563MiB Windows NTFS volume 
/0/100/1.3/0.1/0/3  /dev/sda3   volume         60GiB EXT4 volume 
/0/100/1.3/0.1/1    /dev/sdb    disk           3TB WDC WD30EZRZ-00G 
/0/100/1.3/0.1/1/1  /dev/sdb1   volume         1084GiB Windows NTFS volume 
/0/100/1.3/0.1/1/2  /dev/sdb2   volume         1706GiB EXT4 volume 
/0/100/1.3/0.1/1/3  /dev/sdb3   volume         3502MiB Linux swap volume 
/0/100/1.3/0.2                  bridge         Advanced Micro Devices, Inc. [AMD] 
/0/100/1.3/0.2/0                bridge         300 Series Chipset PCIe Port 
/0/100/1.3/0.2/0/0  enp3s0      network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
/0/100/1.3/0.2/1                bridge         300 Series Chipset PCIe Port 
/0/100/1.3/0.2/4                bridge         300 Series Chipset PCIe Port 
/0/100/1.3/0.2/4/0  wlp5s0      network        BCM4360 802.11ac Wireless Network Adapter 
/0/100/3.1                      bridge         Family 17h (Models 00h-0fh) PCIe GPP Bridge 
/0/100/3.1/0                    display        Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] 
/0/100/3.1/0.1                  multimedia     Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590] 
/0/100/7.1                      bridge         Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B 
/0/100/7.1/0                    generic        Zeppelin/Raven/Raven2 PCIe Dummy Function 
/0/100/7.1/0.2                  generic        Family 17h (Models 00h-0fh) Platform Security Processor 
/0/100/7.1/0.3                  bus            Family 17h (Models 00h-0fh) USB 3.0 Host Controller 
/0/100/7.1/0.3/0    usb3        bus            xHCI Host Controller 
/0/100/7.1/0.3/0/1              multimedia     USB PnP Sound Device 
/0/100/7.1/0.3/0/3              multimedia     EyeToy USB camera Namtai 
/0/100/7.1/0.3/1    usb4        bus            xHCI Host Controller 
/0/100/8.1                      bridge         Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B 
/0/100/8.1/0                    generic        Zeppelin/Renoir PCIe Dummy Function 
/0/100/8.1/0.2                  storage        FCH SATA Controller [AHCI mode] 
/0/100/8.1/0.3                  multimedia     Family 17h (Models 00h-0fh) HD Audio Controller 
/0/100/14                       bus            FCH SMBus Controller 
/0/100/14.3                     bridge         FCH LPC Bridge 
/0/101                          bridge         Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge 
/0/102                          bridge         Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge 
/0/103                          bridge         Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge 
/0/104                          bridge         Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge 
/0/105                          bridge         Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge 
/0/106                          bridge         Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge 
/0/107                          bridge         Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 0 
/0/108                          bridge         Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 1 
/0/109                          bridge         Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 2 
/0/10a                          bridge         Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 3 
/0/10b                          bridge         Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 4 
/0/10c                          bridge         Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 5 
/0/10d                          bridge         Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 6 
/0/10e                          bridge         Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 7 
/0/1                            system         PnP device PNP0c01 
/0/2                            system         PnP device PNP0c02 
/0/3                            system         PnP device PNP0b00 
/0/4                            system         PnP device PNP0c02 
/0/5                            printer        PnP device PNP0400 
/0/6                            communication  PnP device PNP0501 
/0/7                            communication  PnP device PNP0501 
/0/8                            system         PnP device PNP0c02 
/1                  virbr0-nic  network        Ethernet interface 
/2                  virbr0      network        Ethernet interface
[/FONT]
```

Any help is appreciated

---

### Post by TheFu on 2020-10-06
A troubleshooting technique is to create a new userid, then login using that new userid.  If the GUI  works with the new userid, we know  the problem is with the normal userid, not the system.  There are lots and lots of settings for each individual userid. Sometimes those can get screwed up.

---

### Post by TheFu on 2020-10-06
Another common problem for people new to linux/unix is to mess with permissions in a way that breaks things.  
Using sudo with GUI programs can break things, usually permissions. 
I don't think that matches with the description above, but may help someone in a few months seeking an answer who finds this thread.
The fix for this issue often is ```
sudo chown -r $LOGNAME ~/
``` Lots of assumptions with that command. It only works for a user in the sudo group and only for that 1 userid. It doesn't fix other accounts.

---

### Post by adelpozoman-f on 2020-10-06
> **TheFu said:**
> A troubleshooting technique is to create a new userid, then login using that new userid.  If the GUI  works with the new userid, we know  the problem is with the normal userid, not the system.  There are lots and lots of settings for each individual userid. Sometimes those can get screwed up.

You are right, I created another user and it works ok, glxgears gives 15.000fps on that user, whereas on my regular user on recovery mode I only get 2.000fps.
What can I do??
I havent mess with anything about permissions

---

### Post by TheFu on 2020-10-06
I said, 
 > There are lots and lots of settings for each individual userid. Sometimes those can get screwed up.
So, you need to figure out which settings screwed things up.  I use a very simple GUI, not gnome and not kde and not LXQt and not Mate or any other DE, so I doubt I can help.  For my GUI, there is 1 directory that controls all the settings used. The settings are contained in plain text files.  I have daily backups, so I can use those backups to compare all the changes made over the last .... let me see ... from today going back to ... Sun Jun  7 01:35:05 2020.  Do you have versioned backups?

A quick search of the backup areas:
```
./increments/u/thefu/.fvwm.2020-09-07T01:35:04-04:00.dir
./increments/u/thefu/.fvwm.2020-09-08T01:35:07-04:00.dir
./increments/u/thefu/.fvwm.2020-09-06T01:35:04-04:00.missing
./increments/u/thefu/.fvwm.2020-09-19T01:35:05-04:00.dir
./increments/u/thefu/.fvwm.2020-09-09T01:35:04-04:00.dir
```
shows only a few changes to my GUI settings all this time. Doing manual compares for 6 differences wouldn't take long.

I have no idea how to accomplish that with gnome which stores settings inside a DB. Maybe get the DB backups and dump the DB to text, then compare that?  You do have versioned backups, right?

---

### Post by adelpozoman-f on 2020-10-06
> **TheFu said:**
> I said, 
 
So, you need to figure out which settings screwed things up.  I use a very simple GUI, not gnome and not kde and not LXQt and not Mate or any other DE, so I doubt I can help.  For my GUI, there is 1 directory that controls all the settings used. The settings are contained in plain text files.  I have daily backups, so I can use those backups to compare all the changes made over the last .... let me see ... from today going back to ... Sun Jun  7 01:35:05 2020.  Do you have versioned backups?

A quick search of the backup areas:
```
./increments/u/thefu/.fvwm.2020-09-07T01:35:04-04:00.dir
./increments/u/thefu/.fvwm.2020-09-08T01:35:07-04:00.dir
./increments/u/thefu/.fvwm.2020-09-06T01:35:04-04:00.missing
./increments/u/thefu/.fvwm.2020-09-19T01:35:05-04:00.dir
./increments/u/thefu/.fvwm.2020-09-09T01:35:04-04:00.dir
```
shows only a few changes to my GUI settings all this time. Doing manual compares for 6 differences wouldn't take long.

I have no idea how to accomplish that with gnome which stores settings inside a DB. Maybe get the DB backups and dump the DB to text, then compare that?  You do have versioned backups, right?

I use Kubuntu so I dont think I have that option. Is there a way to log whatever happens to see the error?? I am getting crazy

---

### Post by TheFu on 2020-10-06
> **adelpozoman-f said:**
> I use Kubuntu so I dont think I have that option. Is there a way to log whatever happens to see the error?? I am getting crazy

Kubuntu is just KDE. I haven't touched KDE in about 18 yrs. Sorry.  The errors are probably in the system logs.  Did you check those already?  Google found these:
[LIST]
[*][https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#1-overview](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#1-overview)
[*][https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
[*][https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located)
[/LIST]

Backups are a completely different thing. If you want them, they must be setup. They are never automatic. The way I do it seems to be a method that people without significant Unix skills cannot replicate, unfortunately. Sorry. I was disappointed with all the "easier" methods, since they didn't actually meet my needs.  I tried a bunch and each failed at some level, but none failed as bad as the Windows backup tool.  All would backup data just fine, but most didn't also capture permissions, ACLs, and xattrs as those change over time too.

---

### Post by adelpozoman-f on 2020-10-06
I know how to see Ksystemlog and some of the others you linked, but they dont log the information of the crashed session, or at least I dont know which one.

---

### Post by TheFu on 2020-10-06
> **adelpozoman-f said:**
> I know how to see Ksystemlog and some of the others you linked, but they dont log the information of the crashed session, or at least I dont know which one.

Have you tried logging in using the other account then using **su - {original account}** from a terminal to see if that shows any issues?

You can try moving the ~/.config/ directory for the original account - say to ~/.config-old/ and see if you can login then.  I don't know where kde keeps settings. Sorry.

---

### Post by adelpozoman-f on 2020-10-06
Will try tomorrow.
By the moment I tried adding nomodeset at grub and I can use my main account but graphics doesnt work...

EDIT: glxinfo shows that I'm using vmware llvmpipe, is that because my user isnt loading the graphics driver?? what can I do about that?? Or is that because of nomodeset?

---

### Post by TheFu on 2020-10-06
> **adelpozoman-f said:**
> Will try tomorrow.
By the moment I tried adding nomodeset at grub and I can use my main account but graphics doesnt work...

We already eliminated system-wide issues.  The problem is specific to 1 username.  The problem is inside the HOME directory for that user. That is a fact.  If the X11.log file doesn't have any errors, then the only answer will come from figuring out the problem in the HOME directory.

---

### Post by adelpozoman-f on 2020-10-07
> **TheFu said:**
> We already eliminated system-wide issues.  The problem is specific to 1 username.  The problem is inside the HOME directory for that user. That is a fact.  If the X11.log file doesn't have any errors, then the only answer will come from figuring out the problem in the HOME directory.

I got this at the end of xorg.1.log file at /var/log. Maybe its the fatal error or something related


```
[   157.918] (II) modeset(0): EDID for output DVI-D-1
[   157.918] (II) modeset(0): Output DP-1 disconnected
[   157.918] (II) modeset(0): Output DP-2 disconnected
[   157.918] (II) modeset(0): Output DP-3 disconnected
[   157.918] (II) modeset(0): Output HDMI-1 connected
[   157.918] (II) modeset(0): Output DVI-D-1 disconnected
[   157.918] (II) modeset(0): Using exact sizes for initial modes
[   157.918] (II) modeset(0): Output HDMI-1 using initial mode 1920x1080 +0+0
[   157.918] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[   157.918] (==) modeset(0): DPI set to (96, 96)
[   157.918] (II) Loading sub module "fb"
[   157.918] (II) LoadModule: "fb"
[   157.918] (II) Loading /usr/lib/xorg/modules/libfb.so
[   157.918] (II) Module fb: vendor="X.Org Foundation"
[   157.918]     compiled for 1.20.8, module version = 1.0.0
[   157.918]     ABI class: X.Org ANSI C Emulation, version 0.4
[   157.918] (II) UnloadModule: "radeon"
[   157.918] (II) Unloading radeon
[   157.918] (EE) modeset(0): drmSetMaster failed: Invalid argument
[   157.918] (EE) 
Fatal server error:
[   157.918] (EE) AddScreen/ScreenInit failed for driver 0
[   157.918] (EE) 
[   157.918] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   157.918] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   157.918] (EE) 
[   157.918] (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
[   157.918] (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
[   157.918] (WW) xf86CloseConsole: VT_ACTIVATE failed: Input/output error
[   157.918] (EE) Server terminated with error (1). Closing log file.


```

PD: su - (mainaccount) from the other accounts works ok and i can enter commands (outside recovery mode)

---

### Post by TheFu on 2020-10-07
```
[   157.918] (EE) AddScreen/ScreenInit failed for driver 0
```
could be the error. 

Was anyone trying to add a 2nd screen recently?  When I do that, it is manually through a system-wide text file setting, but I don't run a fancy GUI like all the kids use today. That would explain why it is only for 1 userid and only for GUI sessions.

I put that error into google to see what it meant. 
Looks like more recently people with multiple video GPUs are getting it when the settings want to use a driver for 1 GPU, the that isn't the GPU the system has decided to use.  Does that make any sense on your side?  I think it is more common when there's an Intel iGPU and one of the nVidia or AMD GPUs in the system too. I don't have anything like that.
There were some 12+ yr old answers too, but I doubt those would apply today.

If you login on the console, but without X/Wayland, then run **startx**, perhaps the errors on the screen will show more?  I don't know if these new DEs even work with startx.

---

### Post by adelpozoman-f on 2020-10-08
> **TheFu said:**
> ```
[   157.918] (EE) AddScreen/ScreenInit failed for driver 0
```
could be the error. 

Was anyone trying to add a 2nd screen recently?  When I do that, it is manually through a system-wide text file setting, but I don't run a fancy GUI like all the kids use today. That would explain why it is only for 1 userid and only for GUI sessions.

I put that error into google to see what it meant. 
Looks like more recently people with multiple video GPUs are getting it when the settings want to use a driver for 1 GPU, the that isn't the GPU the system has decided to use.  Does that make any sense on your side?  I think it is more common when there's an Intel iGPU and one of the nVidia or AMD GPUs in the system too. I don't have anything like that.
There were some 12+ yr old answers too, but I doubt those would apply today.

If you login on the console, but without X/Wayland, then run **startx**, perhaps the errors on the screen will show more?  I don't know if these new DEs even work with startx.

No, I am the only user of the computer. I am trying to do a deep research on the error, but the results usually are not related... And I only have 1 gpu so...
When I get to the login screen, go to tty, then login, and then startx I get to the same black screen stuck, without any feedback...
Only nomodeset lets me enter, I will keep trying

---

### Post by TheFu on 2020-10-08
Are you 100% certain there is only 1 GPU?  Most Intel "desktop" and "laptop" CPUs include an iGPU. Add in a Radeon card and now the system has 2.

---

### Post by adelpozoman-f on 2020-10-08
100% percent sure. Ryzen 1400 CPU and RX580 GPU.

---

### Post by TheFu on 2020-10-08
> **adelpozoman-f said:**
> 100% percent sure. Ryzen 1400 CPU and RX580 GPU.

That's pretty definite!  I don't know anything about AMD GPU drivers. Sorry.
If it was nvidia, I'd suggest blacklisting the current driver and using either the proprietary one or nouveau driver , depending on which was being tried.  But I think AMD GPU drivers are completely different.

---

### Post by adelpozoman-f on 2020-10-12
SOLVED!!!!!
I followed the instructions on this web (god bless system76): [https://support.system76.com/articles/login-loop-ubuntu/](https://support.system76.com/articles/login-loop-ubuntu/)
And my computer started working. I moved back all the folders to its original name except .local, and it kept working. Then moving by little bulks I discovered that I couldnt login anymore if I moved back from .old the folder ~/.local/share/kscreen.
So then kscreen is the culprit. I just deleted it.
pd: dont know how to mark as solved btw

---

### Post by TheFu on 2020-10-12
> **adelpozoman-f said:**
> SOLVED!!!!!
 ...
pd: dont know how to mark as solved btw

Happy you found a solution.

"Thread Tools" button near the top of the screen - SOLVED.

---

