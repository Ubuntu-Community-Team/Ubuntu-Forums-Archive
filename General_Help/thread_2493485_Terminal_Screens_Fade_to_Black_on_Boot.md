---
title: "Terminal Screens Fade to Black on Boot"
date: 2023-12-17
forum: General Help
---

### Post by sdsurfer on 2023-12-17
MSI B560M Pro-VDH
Intel 17-11700K
Ubuntu 20.04, 22.04, Unity 23.10
Observed both with onboard integrated graphics and   Nvidia card (removed)
Using integrated graphics
Benq monitor connected to HDMI, Dell monitor on VGA port (graphics card removed)

Going through a bit of a nightmare right now that involves a lot of reinstalling, so I'm seeing this across install usb's of Ubuntu 20.04, 22.04 and Unity 23.10, as well as disk boot of those systems.

As you boot the monitor usually switches from terminal output to a splash screen and back a couple times. When monitor output switches to a terminal screen, the monitor fades to black, making it impossible to monitor the boot.  It **may** even be loading the GUI fine but the monitor stays black, CTRL+ALT+F1 does nothing. It also does this on attempted start ups from those systems, so I've no idea if the GUI is booting or not. It is blocking my efforts to solve my issues, the system could be loading fine just not displaying.

Because it's doing this with all three install disks AND on the boot I suspect it might be something in the BIOS or hardware, although I'm seeing nothing in the BIOS.

Has anyone seen anything like this? I've googled my googler off, not seeing anything like it.

---

### Post by MAFoElffen on 2023-12-17
No. I haven't.

What happens if you try to start the installer from the "Safe Graphics" startup option?

If, at the Grub2 Menu, what happens if you press the <E> key to get into an Edit Mode, then arrow down to the line that starts with the word "linux" and delete "quite splash" from that line. Then press the keys <Cntrl><X> to boot? Where does that end at?

Same, but replace the wors "quiet splash" with the word "recovery" > <Cntrl><X> > "network" option > "root" option...

---

### Post by sdsurfer on 2023-12-18
Thank you, been searching around and no one seems to have seen this and it's driving me bonkers. That being the case, I think it might be something in my specific environment, but don't know where to look. There's definitely nothing in the MSI BIOS, ATM it's running off the integrated graphics but saw it when I had a problematic card in the machine. 

As an example, just now I did a restart and held shift to get to the grub menu (only one system installed now.) as I was deciding whether to select Advanced Options, the screen faded to black.

AND . . . the GUI never booted. Or maybe it did but because the monitor is black, I just can't see it. In this state CTRL+ALT F1 or F5 has no effect. On hard shutdown (because keyboard doesn't do anything) and startup it booted right into 22.04.

> **MAFoElffen said:**
> 
What happens if you try to start the installer from the "Safe Graphics" startup option?

I've run the installer so many times I can't swear in court, but one thing I remember is once doing stuff in there (fix packages, etc) I would "resume" and it would do it after hitting resume. The monitor starts to output boot stuff and it fades and fades . . . to black, can't see what it's doing.

>  If, at the Grub2 Menu, what happens if you press the <E> key to get into an Edit Mode, then arrow down to the line that starts with the word "linux" and delete "quite splash" from that line. Then press the keys <Cntrl><X> to boot? Where does that end at?

I'm not fast enough I guess. 
- Start
- Hold shift
- Goes to grub menu
- E
- In the 3-5 seconds I spent locating the line you mentioned . . . monitor faded to black.

I'll keep trying on this, I'm not that familiar with modifying grub but will give it a shot.

---

### Post by MAFoElffen on 2023-12-18
[s]Is this on a latop or Desktop. If desktop,[/s] EDIT: Reread the first post
> 
MSI B560M Pro-VDH

What is the make and model of the display?

This sounds sort of like a eco-power setting gone awry.

EDIT: I since happening on many Distros/versions (not just one) and the behavior does not seem to change or mattter between them... Maybe a UEFI ACPI BIOS setting or a power saving setting in the display?

---

### Post by sdsurfer on 2023-12-19
Thanks again, this is exactly what I was thinking as I'd never seen it before. 

> **MAFoElffen said:**
> [s]What is the make and model of the display?

Dual Benq XL2411-B, but while I was having trouble I was using the i7-11700K integrated graphics with a crappy old HP  monitor connected to the VGA port. Result same, I could see it happen on all three monitors.

The Benq's do indeed have a eco setting, but they were originally set to Movie (has at least 10 options here, none of them made a difference.)

> Maybe a UEFI ACPI BIOS setting

I dug around in there . . . the only thing I saw in the MSI BIOS was an option for GPU detection, PEG or IDG. ACPI settings on page 14, no love there.
[https://download.msi.com/archive/mnu_exe/mb/Intel600BIOS.pdf](https://download.msi.com/archive/mnu_exe/mb/Intel600BIOS.pdf)

However I regret to say I've done the worst thing you can do trying to debug an issue: changed the environment AND hardware. Reinstalled 22.04 on a different partition and threw in a cheap-ish XFS Radeon RX580 card and this problem is no longer present. Apologies to anyone arriving here looking for a solution, but maybe what's here will help you find one.
[SIZE=4][B]
Final thoughts:[/B][/SIZE]

Using FireFox as an example. You know how you're in FF (or any browser) and you come to some site that is so heavy on the client and the window fades to gray, becomes unresponsive, then finally clears? Another example is the screen fadeout in the GUI when your monitor-off settings have reached their time. The effect is exactly like that, except I don't know why it would affect the terminal output on boot, especially considering a system with an i7 and 64 GB/RAM should handle it.

Without full details, I was working with a disk that I think has passed it's prime. Very slow, installs failed, so I left it connected and installed on a different drive, but the process was still slow. I unplugged this drive and everything started to run more quickly. My thought is that is was SO slow the system went into the same "fadeout mode" mentioned above waiting  for this hard drive. Recycle time!

---

