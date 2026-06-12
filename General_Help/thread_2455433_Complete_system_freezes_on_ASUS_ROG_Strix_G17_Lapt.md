---
title: "Complete system freezes on ASUS ROG Strix G17 Laptop"
date: 2020-12-19
forum: General Help
---

### Post by 0x7ab7 on 2020-12-19
Hello,
I recently purchased an ASUS ROG Strix G17 laptop and installed Kubuntu 20.04 on it. Most things worked out of the box, though I did have to install asus-nb-ctrl in order to be able to modify the LED options on the keyboard and get the volume buttons to work properly.

The laptop seems to run smoothly and I'm currently using the proprietary NVIDIA drivers (450).

The problem: Occasionally the entire system freezes. Sometimes it happens when I have the laptop closed and I open it up to find it will not respond to anything...other times it happens while I'm using it and watching a youtube video or checking my e-mail. When the freeze happens, the audio will repeat the last second or so for maybe 10 seconds, then stop completely...no input will work, I'm unable to switch to a terminal with ctrl+alt+f2, and unable to quit X with ctrl+alt+backspace. I installed sshd to see if I could SSH in during one of these freezes, and I am unable to login, it will appear as offline. To fix this, I need to hard shut off the laptop and back on again.

These freezes usually happen once every few days, and the applications I'm using always seem to differ. I have tried looking through the logs but I can't see anything happening when the freezes occur, and any suggestions/help of what to look for would be greatly appreciated.

Thank you.

---

### Post by 0x7ab7 on 2021-01-14
My apologies if this isn't allowed, but I'm still having this issue so I'm bumping the post.

---

### Post by ActionParsnip on 2021-01-14
Check RAM health as a good start
Makes sure you have the latest BIOS
Check air vents are clear

---

### Post by mastablasta on 2021-01-14
CPU is intel? Psensor can measure temp, but i doubt this is the issue here. it likely has something to do with power management or memory allocation.  

what kernel are you using? 

this will give the data or you can find it in ksysinfo:
uname -a

---

### Post by 0x7ab7 on 2021-01-14
> **mastablasta said:**
> CPU is intel? Psensor can measure temp, but i doubt this is the issue here. it likely has something to do with power management or memory allocation.  

what kernel are you using? 

this will give the data or you can find it in ksysinfo:
uname -a

CPU is intel. Temperature doesn't appear to be problem, vents are fine, nothing is overheating. I will check RAM when I reboot next.

output of uname -a is:

[FONT=monospace][COLOR=#000000]Linux Covid 5.4.0-60-generic #67-Ubuntu SMP Tue Jan 5 18:31:36 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]


Edit: How can I check RAM/memory? The memtest option doesn't show up in grub, I'm assuming because of UEFI

[/FONT]

---

### Post by mastablasta on 2021-01-15
memtest should be also available on live DVD/USB boot. maybe you are just now showing all the options in grub? by default only previous kernel is shown and i think you need to press something for the rest to show up.

what nvidia chip is it?

i assume, the optimus is used with nvidia chip and you have a dual intel/nvidia GPU configuration? 
i
 don't know how memory allocation works with these. but as i udnerstand it nvidia has it's own RAM and intel GPU uses ram from motherboard. on AMD the memory could sometimes be allocated wrongly to GPU, which would cause strange behaviour. a workarroudn was to issue a grub command. I believe this was corrected with latest kernel. and you are using the original one (default LTS). you could try to upgrade kernel to HWE kernel and see if that helps. you might need to reinstall nvidia drivers after that. 
read more about it here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

to do it you just issue one command (copy &paste): 
```
[COLOR=#333333][FONT=monospace]sudo apt-get install --install-recommends linux-generic-hwe-20.04[/FONT][/COLOR]
```

you could also load experimental versions of kernel, but i would advise against it at the moment. if you go that way make sure you have reverse instruction printed or available on another device-.

if new kernel makes it worse, you can move back to the old one by installing linux-generic and then removing the HWE kernel from grub. here is a quick how to for 18.04 version. procedure would be similar here:
[https://askubuntu.com/questions/1170524/downgrading-18-04-kernel-5-0-to-the-original-kernel-that-came-with-18-04](https://askubuntu.com/questions/1170524/downgrading-18-04-kernel-5-0-to-the-original-kernel-that-came-with-18-04)


here is detailed experience by user that had to move to older kernel to be able to load nvidia legacy drivers, that lost support in the newer version:
> [COLOR=#000000][FONT=arial]So what I did was purge all nvidia stuff [sudo apt-get remove --purge '^nvidia-.*][/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Installed 5.4 Kernel [sudo apt install linux-generic][/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Ran [sudo grub-mkconfig | grep -E 'submenu |menuentry '] to identify old Kernel so to start at grub.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Updated /etc/default/grub [GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 5.4.0-60-generic"] Grub menu now defaulted to advanced with the old Kernel highlighted for boot[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]From command line reinstalled [sudo apt install nvidia-340] but created errors, specifically could not overwrite files in /usr/lib/x86_64-linux-gnu/[libGL.so.1 and libGLESv2.so.2.distrib] I simply deleted them[/FONT][/COLOR]

FYI - i used HWE kernel on my kids PC to get latest LTS kernel to 18.04 version. because some of the components he bought were new, so i wanted to avoid any potential driver issue (in linux most drivers are in kernel).  worked like a charm.


finally, make sure you are using xorg session (in case ubuntu doesn't default to it) and not wayland. nvidia drivers still need the old xorg. i believe in ubuntu this can be changed /checked on login screen.

---

### Post by 0x7ab7 on 2021-01-15
> **mastablasta said:**
> memtest should be also available on live DVD/USB boot. maybe you are just now showing all the options in grub? by default only previous kernel is shown and i think you need to press something for the rest to show up.

what nvidia chip is it?

i assume, the optimus is used with nvidia chip and you have a dual intel/nvidia GPU configuration? 
i
 don't know how memory allocation works with these. but as i udnerstand it nvidia has it's own RAM and intel GPU uses ram from motherboard. on AMD the memory could sometimes be allocated wrongly to GPU, which would cause strange behaviour. a workarroudn was to issue a grub command. I believe this was corrected with latest kernel. and you are using the original one (default LTS). you could try to upgrade kernel to HWE kernel and see if that helps. you might need to reinstall nvidia drivers after that. 
read more about it here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

to do it you just issue one command (copy &paste): 
```
[COLOR=#333333][FONT=monospace]sudo apt-get install --install-recommends linux-generic-hwe-20.04[/FONT][/COLOR]
```

you could also load experimental versions of kernel, but i would advise against it at the moment. if you go that way make sure you have reverse instruction printed or available on another device-.

if new kernel makes it worse, you can move back to the old one by installing linux-generic and then removing the HWE kernel from grub. here is a quick how to for 18.04 version. procedure would be similar here:
[https://askubuntu.com/questions/1170524/downgrading-18-04-kernel-5-0-to-the-original-kernel-that-came-with-18-04](https://askubuntu.com/questions/1170524/downgrading-18-04-kernel-5-0-to-the-original-kernel-that-came-with-18-04)


here is detailed experience by user that had to move to older kernel to be able to load nvidia legacy drivers, that lost support in the newer version:


FYI - i used HWE kernel on my kids PC to get latest LTS kernel to 18.04 version. because some of the components he bought were new, so i wanted to avoid any potential driver issue (in linux most drivers are in kernel).  worked like a charm.


finally, make sure you are using xorg session (in case ubuntu doesn't default to it) and not wayland. nvidia drivers still need the old xorg. i believe in ubuntu this can be changed /checked on login screen.

[FONT=monospace][COLOR=#000000]01:00.0 VGA compatible controller: NVIDIA Corporation TU106 [GeForce RTX 2060] (rev a1)[/COLOR]

is my nVidia chip. I'm going to try moving over to hwe kernel as you suggested! Thank you so much for all your help so far, I really appreciate it.[/FONT]

---

