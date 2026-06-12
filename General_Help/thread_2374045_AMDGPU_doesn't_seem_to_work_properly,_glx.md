---
title: "AMDGPU doesn't seem to work properly, glx"
date: 2017-10-12
forum: General Help
---

### Post by khoriam on 2017-10-12
Hello there again. My previous topic was [there]("https://ubuntuforums.org/showthread.php?t=2373879&page=3&highlight=firmware") (marked as [SOLVED] because of changes in my question), I tried to isntall fglrx for my laptop with R5 M435 graphics adapter. Most errors I faced there were solved (like the cpu firmware bug and so on) after I changed the .iso burning software from windows unetbootin for ubuntu's startup disk creator. However, few problems appeared. 
At first, my system crashed when I was installing updates for my laptop. System was dead and resisted my REISUB with the on command "preparing to unpack .../libpulsedsp". It was absolutely dead, had to hardreset. Then initframs appeared. 

There were these mistakes:
su_fw: mixing new and old firmware.
[drm:si_init[radeon]] ERROR Failed to load firmware
radeon 0000.01.00.0: fatal error during GPU init
amdgpu 0000:01:00.0: si_mc: Failed to load firmware "radeon/si... something"
amdgpu 0000:01:00.0: Failed to load mc firmware!
[drn:amdgpu_device_init [amdgpu]] error, sw_init of ip block...
and so on. There may be some mistakes due to blurry images. 

Could cure it with fsck, but not fully. It refused to load the DE, when I tried to startx it wrote me "fatal server error": couldn not create lock file in /tmp/.tX0-lock. Please consult the The X.Org....... xinit giving up, xauth - error in locking authority file /home/user/.Xauthority
Nomodest in grub gave nothing, it hanged on "loading kernel, loading ramdisk"

But as a result I got loaded xubuntu almost without any graphical interace. Like, there were no even icons around. Started from installing amdgpu, there were errors with libpulsedsp, had to fix dpkg and run install with -f because of unmet dependencies. Then the instal went smoothly, I rebooted ubuntu and one of my gpus started working (maybe it was the R5 m230 one because of some desktop appearance change).

Each boot/reboot/shutdown shows [this]("https://imgur.com/a/frOb6") message in non-graphic interface (system works normally, except steam and so on, appears only when under mentioned cis icrumstances)
Wonder what does the "[drm:amdgpu_fill_buffer [amdgpu]] ERROR Trying to clear memory with ring turned off." message mean. 
Also, this message appears ONLY when kernel is set to 4.10 (inxi is down there)

Then, I tried to test it by launching steam, which gave me the "[COLOR=#000000]OpenGL GLX extension not supported by display." error.
[/COLOR]glxinfo said: 
name of display: :0.0 
Error: couldn't find RGB GLX visual or fbconfig

inxi -G with 4.8 kernel
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Device 98e4
Card-2: Advanced Micro Devices [AMD/ATI] Jet PRO [Radeon R5 M230]
Display Server: X.Org 1.19.3 drivers: ati,radeon (unloaded: fbdev,vesa,amdgpu)
Resolution: 1366x768@60.00hz
GLX Renderer: N/A GLX Version: N/A

inxi -G with 4.10 kernel
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Device 98e4
Card-2: Advanced Micro Devices [AMD/ATI] Jet PRO [Radeon R5 M230]
Display Server: X.Org 1.19.3 drivers: ati,amdgpu (unloaded: fbdev,vesa,radeon)
Resolution: 1366x768@60.00hz
GLX Renderer: N/A GLX Version: N/A



[URL="https://pastebin.com/hB6NZi91"]inxi -Fxz 4.8 kernel
[/URL]
[inxi -Fxz 4.10 kernel]("https://pastebin.com/d3NdZzyb")


[x.Org log (cat /var/log/Xorg.0.log 4.10 kernel]("https://pastebin.com/UMqa4gGN")

[dmesg 4.10 kernel]("https://pastebin.com/YxT54YCg")

[journalctl -b 4.10 kernel]("https://pastebin.com/n9D2iR58")

[lspci -k 4.10 kernel]("https://pastebin.com/aqiT1UJM")


echo IGD | sudo tee /sys/kernel/debug/vgaswitcheroo/switch gives IGD for both kernels

sudo cat /sys/kernel/debug/vgaswitcheroo/switch 4.8 gives 
0: DIS : : DynOff:0000:01:00.0
1: IGD :+: Pwr:0000:00:01.0

whereas for 4.10
0:IGD:+: Pwr:0000:00:01.0
1: DIS: : DynPwr:0000:01:00.0

How can I use my second card? AMDGPU-PRO was installed through the amd site.
What do I do? Would be grateful for advices.

Xubuntu 16.04.2 LTS.

---

### Post by khoriam on 2017-10-13
Any help, please? Installed 16.04.3 LTS and 17.40 AMD driver afterwards, the problem PERSISTS, there is "ring" after and before the system start/end.
glxinfo says name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

---

### Post by Yellow Pasque on 2017-10-13
This is a difficult configuration. You have two AMD GPU's. The integrated GPU is GCN 3rd generation (Volcanic Islands) and the discrete graphics is GCN 1st Generation (Southern Islands)

First off, I would stop trying to use proprietary drivers of any kind. fglrx/Catalyst doesn't support the integrated graphics (and it won't install on modern versions of Ubuntu anyway). AMDGPU-Pro doesn't support the discrete card. So I believe proprietary drivers are a dead end for this configuration.

The next thing I would do is get a live USB of Xubuntu 17.10 and boot with "radeon.si_support=0 radeon.cik_support=0 amdgpu.si_support=1 amdgpu.cik_support=1" added to the kernel command line. This should force both GPU's to use the amdgpu kernel module, and hopefully, it will solve the issue of mixing new and old firmware. See what this command gives as output:
```
xrandr --listproviders
```

---

### Post by khoriam on 2017-10-13
How do I run it with such settings? And thanks for reply, I'm actually in some kind of amd-despair already because of it.

16.04.3
xrandr
Providers: number : 1
Provider 0: id: 0x44 cap: 0x0 crtcs: 2 outputs: 3 associated providers: 0 name:Unknown AMD Radeon GPU @ pci:0000:00:01.0

I don't know whether I've done it right (used E in grub, then added the commands) ((nah it was wrong, got the same after clean live launch. I don't know how to launch with mentioned commands))
Providers: number : 2
Provider 0: id: 0x74 cap: 0x9, Source Output, Sink Offload crtcs: 2 outputs: 3 associated providers: 1 name:Unknown AMD Radeon GPU @ pci:0000:00:01.0
Provider 1: id: 0x3f cap: 0x4, Source Offload crtcs: 0 outputs: 0 associated providers: 1 name:HAINAN @ pci:0000:01:00.0

---

### Post by khoriam on 2017-10-14
Installed 17.10 with amdgpu - "can't open display"

---

### Post by entw on 2017-10-14
Why are you so desperately trying to bite your own tail?
I think radeonsi is more than enough in this situation.

> **khoriam said:**
> I don't know how to launch with mentioned commands
These are kernel parameters and supposed to be added to /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="radeon.si_support=0 radeon.cik_support=0 amdgpu.si_support=1 amdgpu.cik_support=1 quiet splash"
```
And you have to run `sudo update-grub` after that.

---

### Post by khoriam on 2017-10-14
Yup,I did it - nothing changed. With the default I won't be able to play video games older than 2010. The problem is - I wanna switch from win to xubuntu but cause of games I can't do it.
And what is radeonsi about? Is it the default one? Anyway, how do I install it so I can play some more demanding videogames? Thank you.

---

### Post by Yellow Pasque on 2017-10-14
Looking at logs, I see a lot of errors involving AMD-Vi. If you see an option to disable AMD-Vi in your BIOS/EFI, try disabling it.
The only other idea I have is to boot with "iommu=soft" in GRUB line.

> And what is radeonsi about? Is it the default one?

It is the name of the 3D driver used for AMD GPU's. It is the default and already installed.

---

### Post by khoriam on 2017-10-14
> **Temüjin said:**
> If you see an option to disable AMD-Vi in your BIOS/EFI, try disabling it.
It is the name of the 3D driver used for AMD GPU's. It is the default and already installed.
Nope, I don't have such option in bios. Does this driver trigger my dedicated gpu while gaming?

---

### Post by Yellow Pasque on 2017-10-14
GPU switching is not automatic. Use DRI_PRIME=1 to run something on the discrete GPU.
```
glxinfo | grep string      #this should give info on integrated GPU
DRI_PRIME=1 glxinfo | grep string      #this should give info on discrete
```

---

### Post by khoriam on 2017-10-14
Hell, it worked. I can't believe the answer was that both close and far from me. Thanks to all of you, guys. You solved my week-long butthurt. Gonna check it in steam games.
How do I say "thanks" or raise the rep?

---

### Post by khoriam on 2017-10-14
The other problem - the whole system started freezing. After the freezing occurrence bios time gets reseted, and when I launch windows it checks \\?\ SystemRestore. Don't know if I should do the clean reinstall, and where the problem comes from.

---

### Post by Yellow Pasque on 2017-10-14
Did the freezing just start when using DRI_PRIME?  Are you able to monitor temps:?
```
sensors
```

> How do I say "thanks" or raise the rep? 
You already said thanks. This forum had the ability to mark a post as helpful years ago, but they got rid of it (because it slowed down database access IIRC).

---

### Post by khoriam on 2017-10-14
Freezing starts randomly, especially when I launch steaf/terminal/firefox. Wiped ubuntu and grub, gonna make a full clean install

---

### Post by Yellow Pasque on 2017-10-14
You may want to run memtest too. [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

---

### Post by khoriam on 2017-10-14
I doubt its memory cuz it worked fine before I had purged the oibaf's drivers (I had both oibaf and mesa). Laptop is new but will run it just to be safe

---

