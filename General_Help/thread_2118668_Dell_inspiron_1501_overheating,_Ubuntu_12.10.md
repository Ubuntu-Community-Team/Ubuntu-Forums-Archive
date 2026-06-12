---
title: "Dell inspiron 1501 overheating, Ubuntu 12.10"
date: 2013-02-21
forum: General Help
---

### Post by jackofall1232 on 2013-02-21
Please help I am new to Linux and I like the UBUNTU OS but I have had some set backs. I have got the wireless working and now I am having an over heating problem. I installed Psensor and no load it sits about 65c under light load it jumps to 80 and if I run something intense like hulu it gets so hot it shuts down. I was running win7 and did not have this problem. Please dont tell me to change my thermal paste or anything like that. I know it has something to do with the os or the fans not running at the right speed or something. all the codes that I have found by searching this have been either not working or has screwed up the os to where it wont work. Please help I am a dumb newbie and I never really post in forums because I rarely get answers, but I really need help this time..lol Thanks in advance.

---

### Post by CloakandPigeon on 2013-02-21
I don't really see how Ubuntu would have caused this, if you have overheating issues its likely separate.  Is this a laptop or desktop?

---

### Post by jackofall1232 on 2013-02-21
> **CloakandPigeon said:**
> I don't really see how Ubuntu would have caused this, if you have overheating issues its likely separate.  Is this a laptop or desktop?

I assure you I have googled this problem. and I am not the only one. It is a laptop. Dell inspiron 1501. I had no problems from windows vista or windows 7 only had problems once I installed UBUNTU.

---

### Post by csillva on 2013-02-21
What video card do you have and what driver are you using? For example, if you have an Nvidia card and are using Nouveau (open source driver) it's power management is not as good as the proprietary nvidia one, which could lead to the overheating situation you describe when watching videos.

---

### Post by jackofall1232 on 2013-02-21
> **csillva said:**
> What video card do you have and what driver are you using? For example, if you have an Nvidia card and are using Nouveau (open source driver) it's power management is not as good as the proprietary nvidia one, which could lead to the overheating situation you describe when watching videos.

I believe it is an ati radeon but not positive. ubuntu does not see it that I can tell I am looking on amd website to see. I know there has to be an easy way to put the drivers for my graphics card on here.

---

### Post by csillva on 2013-02-21
```
sudo lspci | grep Display
```

---

### Post by jackofall1232 on 2013-02-21
> **csillva said:**
> ```
sudo lspci | grep Display
```

that did nothing

---

### Post by Molech on 2013-02-21
Check if you have a hybrid GPU (2 video cards - one integrated and one discrete) and are using open source drivers (I assume you are). If you have, perhaps you better turn off one of them (the one is not in use).
I used to get full speed fans all the time, overheating and shorter battery life. In my case it worked (HP laptop).

For the above comments, try on terminal:

sudo lspci | grep VGA

Then try running the following on terminal and see what happens:

sudo su
*type your password*
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

After that exit su mode by typing:

exit

More info at:
[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by csillva on 2013-02-21
Ok, let's be a little more verbose about it then.

```
sudo lspci
```

and

```
cat /var/log/Xorg.0.log | grep module
```

---

### Post by jackofall1232 on 2013-02-21
> **csillva said:**
> Ok, let's be a little more verbose about it then.

```
sudo lspci
```

and

```
cat /var/log/Xorg.0.log | grep module
```

I said I was new I meant VERY New all I know is what I have learned this week thats it so you are going to need to talk to me like I am the biggest idiot that you have ever met and you wont be far off I am Ignorant but wanting to learn. I type in sudo lspci in the terminal and I get

00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)


[    32.047] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    32.192] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    32.228] 	compiled for 1.13.0, module version = 1.0.0
[    32.250] (WW) Warning, couldn't open module fglrx
[    32.250] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    32.251] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    32.275] 	compiled for 1.13.0, module version = 6.99.99
[    32.275] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    32.291] 	compiled for 1.13.0, module version = 6.99.99
[    32.291] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.296] 	compiled for 1.12.99.902, module version = 2.3.2
[    32.297] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    32.327] 	compiled for 1.13.0, module version = 0.5.0
[    32.328] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    32.339] 	compiled for 1.12.99.902, module version = 0.4.3
[    32.340] (WW) Warning, couldn't open module fglrx
[    32.340] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    32.340] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    32.340] 	compiled for 1.13.0, module version = 6.99.99
[    32.340] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.340] 	compiled for 1.12.99.902, module version = 2.3.2
[    32.341] (II) Failed to load module "vesa" (already loaded, 0)
[    32.341] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    32.341] 	compiled for 1.13.0, module version = 0.5.0
[    32.341] (II) Failed to load module "modesetting" (already loaded, 0)
[    32.341] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    32.341] 	compiled for 1.12.99.902, module version = 0.4.3
[    32.341] (II) Failed to load module "fbdev" (already loaded, 0)
[    32.392] (II) Loading sub module "fbdevhw"
[    32.392] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    32.466] 	compiled for 1.13.0, module version = 0.0.2
[    32.467] (II) Loading sub module "dri2"
[    32.467] (II) Loading sub module "exa"
[    32.467] (II) Loading /usr/lib/xorg/modules/libexa.so
[    32.542] 	compiled for 1.13.0, module version = 2.6.0
[    32.588] (II) Loading sub module "fb"
[    32.588] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.668] 	compiled for 1.13.0, module version = 1.0.0
[    32.668] (II) Loading sub module "ramdac"
[    33.755] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.787] 	compiled for 1.13.0, module version = 2.7.3
[    33.796] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.825] 	compiled for 1.12.99.905, module version = 1.6.2

could it be due to fglrx module?
I have seen this come up before in other forum posts and it has something to do with ati drivers. I am just lost so far. I don't want my laptop burning up and I have had to re install ubuntu 3 seperate times due to bad info messing up the OS.I don't have windows on here either anymore (good riddance) so I want this os to work for me. I think you may be right about the graphics driver having something to do with it. I have read a lot about similar problems. I just havent found the solution yet.. thanks

> **Molech said:**
> Check if you have a hybrid GPU (2 video cards - one integrated and one discrete) and are using open source drivers (I assume you are). If you have, perhaps you better turn off one of them (the one is not in use).
I used to get full speed fans all the time, overheating and shorter battery life. In my case it worked (HP laptop).

For the above comments, try on terminal:

sudo lspci | grep VGA

Then try running the following on terminal and see what happens:

sudo su
*type your password*
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

After that exit su mode by typing:

exit

More info at:
[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

this
did not work for me thank you.

---

### Post by lcruz007 on 2013-02-22
I am having exactly the same problem on my Samsung Laptop. When I use Ubuntu the computer gets really hot (about 90-95 degree celsius). It gets really slow and sometimes it just shuts down. This is not a hardware problem, this does not happens on Windows. I have tried many things... I have installed Jupiter, I have tried deactivating one of the graphics card, etc... I have tried many things, but none seems to work!

For some reason my CPUs seem to be working even more when the laptop is hot, look at the screenshot - just had one browser window opened, thee forums, the terminal and the system monitor:

[IMG]http://oi50.tinypic.com/313m0rq.jpg[/IMG]

Are you having the same problem with the CPUs?

---

### Post by jackofall1232 on 2013-02-22
yes I am .. I am having trouble with the cpu getting too hot core reaching 90c+ and shutting down when under a load still have not found how to do it .. I think from everything I have read so far it might have something to do with this  : Failed to load module "fglrx" but I havent found a successful way to fix it yet. I know almost nothing about linux so I am a little handicapped that is why I am here .  I am interested in learning it but I cant get my machine to run  well enough . I am afraid I will burn it up or brick it and loose it all.

Ok apparently no one here has any clue. I have got as far as  it is a bug that wont let module fglrx install making it so ATI propitiatory drivers for the graphics card not load. Therefore the only workaround I have found is to use generic drivers.. Only problem with that is, the generic drivers are probably the ones causing the overheat. I think I have had one too many problems with 12.10. I guess I  will wipe out 12.10 try 12.04 and see if I can get the drivers to load in 12.04.. I wish help was a little easier to get but that's what I get I guess for trying an unstable platform.. Thanks to all that tried to help I hope I don't need to go back to slow Windows

---

### Post by Yellow Pasque on 2013-02-22
It has nothing to do with fglrx or video driver (fglrx/Catalyst does not support a GPU as old as yours).

A system should NEVER overheat, even when under full load, or else the cooling is inadequate. It's possible that dust has built up inside the laptop, so if it's not too difficult to open the laptop and check, that is highly recommended.

---

### Post by genterminl on 2013-02-22
I agree with Temüjin.  However, a can of compressed air aimed into any vents can often clear out lots of dust without having to disassemble anything.

Also, although I have not read the entire thread - are you sure the fan(s) are working correctly?  Have to tried installing any monitoring software?  (xosview or gkrellm for general monitoring, lmsensors to actually monitor temperatures and fans)  Do you really know if the overheat is the CPU or GPU?

---

### Post by jackofall1232 on 2013-02-22
> **genterminl said:**
> I agree with Temüjin.  However, a can of compressed air aimed into any vents can often clear out lots of dust without having to disassemble anything.

Also, although I have not read the entire thread - are you sure the fan(s) are working correctly?  Have to tried installing any monitoring software?  (xosview or gkrellm for general monitoring, lmsensors to actually monitor temperatures and fans)  Do you really know if the overheat is the CPU or GPU?
Yes thanks guys it is deff a software problem.. not a dust problem or a thermal paste problem .. My laptop was running just fine under windows I have built every one of my desktops and I understand the importance of maintenance and air flow. I said I was new to Ubuntu not new to owning a computer. Thanks anyway

---

### Post by Yellow Pasque on 2013-02-22
Let me repeat: Overheating is never a software problem. Ubuntu/Linux may put more load on the CPU (especially watching Flash videos), but your system should not overheat or it is not cooled properly...

---

### Post by jackofall1232 on 2013-02-22
> **Temüjin said:**
> Let me repeat: Overheating is never a software problem. Ubuntu/Linux may put more load on the CPU (especially watching Flash videos), but your system should not overheat or it is not cooled properly...

Software can overheat your system for instance if your fan speeds are not correct because the drivers are wrong. and an easy way of troubleshooting that is by monitoring your core temp. In windows vista and windows 7 my core very rarely gets above 65c and only so warm because it is an AMD which tend to run higher than intel. When I installed UBUNTU 12.10 my core temp idle is 60-65 and  under a full load(eg.Flash Vids) It would get 80+ before fans would kick into high gear. and at 90c it shuts down. I know everything wants you to say it is a hardware issue (that would be an easy fix) because in most PC running windows it would be most likely hardware failure or air blockage. I may not know Linux like the rest of you but I am not an idiot. I can troubleshoot some. So If it "never" can be a software issue, How come I don't have this problem when running Windows? How come the very time my computer decides to have this problem is when I installed UBUNTU? When I re-installed windows vista on the machine all the problems with overheating just went away and then when I put a fresh install of UBUNTU on the Machine I start having the overheating problem again? Are you trying to say it is just coincidence? I mean it wont be anything to re-grease and re-seat the CPU but I feel there is another underlying problem not just maybe a thermal grease breakdown. I have not done any thing to block flow I keep all of my computers nice and clean and free of obstructions. that is why I don't understand your logic. Linux is very well capable of controlling graphics and making them overclock which can cause heat and Linux can control fan speeds where slow fan speeds and Full bore processing combined can surely overheat a machine. especially a laptop that is already challenged for airflow. 
Thanks again.

---

### Post by fibster on 2013-02-22
Your absolutely correct, I have a dual boot windows 7 and Ubuntu,
exact same problem. I cant watch flash in full screen, my laptop ( amd ) overheats and shuts down. I have tried many things but to no avail. Has to be in the kernel modules but I am clueless also. I feel your pain.

---

### Post by ersatzsplatt on 2013-02-22
there are different components in your system many of which may have different power management features.  some people are trying to help you guess which one is causing your problem for you.  others seem to be unaware of the low level software that does facilitate cooling and (more directly) power management.
fan control has been mentioned -- there may be specific drivers for turning up the air on heat condition.
power control of your video chip has been mentioned.  this could be another factor.
power control (maybe related to firmware) for other components, such as your wireless network device maybe be a factor.
cpu power management is what I would suspect first.  you might want to try:
lscpu
... possibly cat /proc/cpuinfo (maybe more information that you wanted)
then search for linux/ubuntu "power management" features for that cpu.

In the end there is a simple equation of power consumption vs. heat dissipation.  If your hardware is going to some kind of shutoff mode because the heat is too high, you are either using more power than is expected for the system design or (less likely) not dissipating it as well as expected.

Where I probably haven't solved your problem completely here, it at least gives you some things to look at.  The answer is there somewhere, even if it is not as direct as you would like.

Good luck and please share any successes.

---

### Post by jackofall1232 on 2013-02-22
> **fibster said:**
> Your absolutely correct, I have a dual boot windows 7 and Ubuntu,
exact same problem. I cant watch flash in full screen, my laptop ( amd ) overheats and shuts down. I have tried many things but to no avail. Has to be in the kernel modules but I am clueless also. I feel your pain.

Well I am sorry I wish I could keep UBUNTU I tried it like 5 years ago and liked it that's why I decided to try it again but it is looking like my crappy Dell just is not getting along with UBUNTU. I want to learn Linux but I am finding UBUNTU to buggy for my old laptop and my un-knowledgeable self . It is hard to get any real answers alot of "try this" boom just corupted ubuntu  re-install. I am thinking of trying the new mint to see if I can get any better results. Thanks for everyone that tried to help. My final thought is that it has to do with : 
EE) Failed to load module "fglrx"

a lot of other research I have looked over on the web seems to substantiate  my claim . As of now UBUNTU knows it is a bug and there is no known FIX and the only workaround is generic drivers. And the generic drivers are what I attribute the problem to.. at least on my particular model. 

Temüjin Thank you for your input  but I feel we have reached an impasse on this subject. I understand your view if there is better cooling the software should not overheat the system but I don't have any hardware upgrades that should warrant a cooling system upgrade. Im not running a gaming pc. it is stock with the exception I have 2gb ram instead of 1gb. The only cooling upgrade I might need to do is freshen the thermal paste or cut a hole in the bottom of the laptop..lol .. Thank you for your help though

> **ersatzsplatt said:**
> there are different components in your system many of which may have different power management features.  some people are trying to help you guess which one is causing your problem for you.  others seem to be unaware of the low level software that does facilitate cooling and (more directly) power management.
fan control has been mentioned -- there may be specific drivers for turning up the air on heat condition.
power control of your video chip has been mentioned.  this could be another factor.
power control (maybe related to firmware) for other components, such as your wireless network device maybe be a factor.
cpu power management is what I would suspect first.  you might want to try:
lscpu
... possibly cat /proc/cpuinfo (maybe more information that you wanted)
then search for linux/ubuntu "power management" features for that cpu.

In the end there is a simple equation of power consumption vs. heat dissipation.  If your hardware is going to some kind of shutoff mode because the heat is too high, you are either using more power than is expected for the system design or (less likely) not dissipating it as well as expected.

Where I probably haven't solved your problem completely here, it at least gives you some things to look at.  The answer is there somewhere, even if it is not as direct as you would like.

Good luck and please share any successes.

All of what you have mentioned I have looked at and the best I could come up with is that it is a bug and has been reported before. as of today 2/22/13 there is no fix that I could find for this bug only a workaround for display using generic drivers. UBUNTU 12.10 cant load ATI catalyst on my machine. it will partially load but it will put my graphics in low resolution mode and I cant get ubuntu to load after reboot it comes up with a recovery console and then soft bricks.

---

### Post by csillva on 2013-02-22
> **jackofall1232 said:**
> All of what you have mentioned I have looked at and the best I could come up with is that it is a bug and has been reported before. as of today 2/22/13 there is no fix that I could find for this bug only a workaround for display using generic drivers. UBUNTU 12.10 cant load ATI catalyst on my machine. it will partially load but it will put my graphics in low resolution mode and I cant get ubuntu to load after reboot it comes up with a recovery console and then soft bricks.

Sorry if I missed it, but what instructions are you following? What bug do you think is affecting you?

---

### Post by Yellow Pasque on 2013-02-22
It's possible that the fan could be running too slow with a buggy BIOS, but most people notice this audibly and mention it (especially when they have another OS to compare it to). So you should try and compare what you hear when the system gets hot running Windows with what you hear running Ubuntu.

> My final thought is that it has to do with :
(EE) Failed to load module "fglrx"

That's not a bug; it's a misleading warning. Even my RadeonHD 4550 says that when I use the open-source driver. I also had a laptop with a RadeonHD 4250 that did run warmer with the open-source driver, but it wouldn't overheat unless the vent was blocked.

---

### Post by csillva on 2013-02-22
> **Temüjin said:**
> It's possible that the fan could be running too slow with a buggy BIOS, but most people notice this audibly and mention it (especially when they have another OS to compare it to). So you should try and compare what you hear when the system gets hot running Windows with what you hear running Ubuntu.


That's not a bug; it's a misleading warning. Even my RadeonHD 4550 says that when I use the open-source driver. I also had a laptop with a RadeonHD 4250 that did run warmer with the open-source driver, but it wouldn't overheat unless the vent was blocked.

We get it. You think it's hardware. But when he reboots into Windows he doesn't have this problem, which means it's not bios and it's not hardware. It's likely a driver issues, less likely to be a bug, or possibly some strange interaction with unity his hardware. First choice in my book is driver issue, and I always start with video card. Next we'll check to make sure his cpu is frequency scaling, that the governor is ondemand, last we'll see if it's a problem with unity. 

Hardware and bios are off the table because dual-booting windows = no overheating problems.

---

### Post by Yellow Pasque on 2013-02-22
> Hardware and bios are off the table because dual-booting windows = no overheating problems.
Just because a BIOS is tested and compliant with Windows doesn't mean it follows the actual ACPI standard...

> Next we'll check to make sure his cpu is frequency scaling, that the governor is ondemand
Again, even if a system runs at full load for a continued period of time, it shouldn't overheat. If it's possible to overheat it, then the cooling is simply insufficient.

---

### Post by csillva on 2013-02-22
> **Temüjin said:**
> Jeven if a system runs at full load for a continued period of time, it shouldn't overheat. If it's possible to overheat it, then the cooling is simply insufficient.

Fine, let's just assume you're right and it's a design flaw. What do we do now? Exactly the same thing I suggested above: .. let's see if we can make sure everything is running as cool as possible to avoid it. Check Video driver. Cpu frequency scaling. Correct governor. No strange interactions with Unity.

---

### Post by jackofall1232 on 2013-02-22
> **Temüjin said:**
> It's possible that the fan could be running too slow with a buggy BIOS, but most people notice this audibly and mention it (especially when they have another OS to compare it to). So you should try and compare what you hear when the system gets hot running Windows with what you hear running Ubuntu.


That's not a bug; it's a misleading warning. Even my RadeonHD 4550 says that when I use the open-source driver. I also had a laptop with a RadeonHD 4250 that did run warmer with the open-source driver, but it wouldn't overheat unless the vent was blocked.
well that is your machine running on open source drivers Mine does not like the drivers provided by ubuntu. If you look around I am not the only one with this problem.

I don't know but if it isn't a bug people sure want it fixed.. [https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer)

---

### Post by csillva on 2013-02-22
Jack, what instructions are you following to try and install your graphics driver? Have you properly identified what your video card is yet? It was listed in the lspci output on earlier on.

---

### Post by jackofall1232 on 2013-02-22
> **csillva said:**
> Fine, let's just assume you're right and it's a design flaw. What do we do now? Exactly the same thing I suggested above: .. let's see if we can make sure everything is running as cool as possible to avoid it. Check Video driver. Cpu frequency scaling. Correct governor. No strange interactions with Unity.

csillva I thank you very much for trying to help. I am not a big fan of dells anyway but I think mine is just one of those few out there that are going to keep having problems. I had problems with wireless Broadcom drivers also. 
I tried changeing to 12.04 and the problems were worse I lost all internet wired and wireless. So I decided to try Mint 14 and see if I have any luck there so far it seems to be running right and not overheating.and I have internet using it. . I hope this thread will stay open for someone else having the same problem to might be able to solve it for others. Thank you very much for your help again folks.

---

### Post by Yellow Pasque on 2013-02-22
EDIT: forget it

---

### Post by jackofall1232 on 2013-02-23
> **Temüjin said:**
> EDIT: forget it

Ok here is more proof it is software. after installing mint Idle sitting at 51c with a load I only got as high as 67c  so IDK Good luck all in figuring this one out. Thanks for trying.

---

### Post by mörgæs on 2013-02-23
I have a Dell with the same graphics card. 

Running Ubuntu is hopeless, but it works fine with a standard Lubuntu 12.10. 

Old Dells are easy to disassemble, so removing the fan and checking for dust is an easy task (but you know that already). It's not enough to blast canned air in here and there.

Also it's easy to upgrade the BIOS, if necessary. Which BIOS are you using?

---

### Post by lcruz007 on 2013-02-23
> **jackofall1232 said:**
> Ok here is more proof it is software. after installing mint Idle sitting at 51c with a load I only got as high as 67c  so IDK Good luck all in figuring this one out. Thanks for trying.

Jack, 

Apparently it's a problem with the drivers of the ATI Radeon graphics card. Read this tutorial and try it: [http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/]("http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/")

I have tried it myself, and my laptop is running cooler, faster, my CPUs are OK, and the maximum temperature it reaches is 80 C (Before the minimum temperature was 90C) even with Youtube and a lot of other websites and apps running. Here is a screenshot:

[IMG]http://oi46.tinypic.com/saxo2x.jpg[/IMG]

---

### Post by jackofall1232 on 2013-02-23
> **lcruz007 said:**
> Jack, 

Apparently it's a problem with the drivers of the ATI Radeon graphics card. Read this tutorial and try it: [http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/]("http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/")

I have tried it myself, and my laptop is running cooler, faster, my CPUs are OK, and the maximum temperature it reaches is 80 C (Before the minimum temperature was 90C) even with Youtube and a lot of other websites and apps running. Here is a screenshot:


lcruz you are the man! This worked pretty good. works for mint 14 too. I knew it wasn't hardware issue or a dust issue . running hulu I am getting only 76c max and I can live with that. AMD runs hot anyway. Mark this one solved Thanks to lCruz.

my machine seems to respond better too.. bonus.!!! you rock!

---

### Post by lcruz007 on 2013-02-23
> **jackofall1232 said:**
> lcruz you are the man! This worked pretty good. works for mint 14 too. I knew it wasn't hardware issue or a dust issue . running hulu I am getting only 76c max and I can live with that. AMD runs hot anyway. Mark this one solved Thanks to lCruz.

Awesome! I am glad I could help. :)

---

### Post by lobosuelto on 2013-03-09
> **jackofall1232 said:**
> lcruz you are the man! This worked pretty good. works for mint 14 too. I knew it wasn't hardware issue or a dust issue . running hulu I am getting only 76c max and I can live with that. AMD runs hot anyway. Mark this one solved Thanks to lCruz.

Hey guys, I&#7743; having the sane problem here, trying to open the link provided but seems to be broken. Can anyone update this?

> **jackofall1232 said:**
> lcruz you are the man! This worked pretty good. works for mint 14 too. I knew it wasn't hardware issue or a dust issue . running hulu I am getting only 76c max and I can live with that. AMD runs hot anyway. Mark this one solved Thanks to lCruz.

Hey guys, I&#7743; having the same problem here, trying to open the link provided ([http://cisight.com/install-amd-radeo...-1110-oneiric/]("http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/")) but seems to be broken. Can anyone update this?

---

### Post by lcruz007 on 2013-04-21
lobosuelto,

The link works for me, are you sure it doesn't work for you? Try copying and pasting it to your browser: cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric

---

### Post by rrich1974 on 2013-04-22
i really dont understand, the link says about installing fglrx for hd6xxx but the man above told us that it has a pretty old mobility radeon 200M on dell inspiron 1501.

still, i am surprised because the open-source radeon driver works pretty good on my x1270.

---

