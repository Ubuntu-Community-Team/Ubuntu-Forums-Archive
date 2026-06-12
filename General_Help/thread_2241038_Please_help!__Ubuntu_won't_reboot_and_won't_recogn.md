---
title: "Please help!  Ubuntu won't reboot and won't recognize USB or CD-ROM drives in GRUB 2"
date: 2014-08-23
forum: General Help
---

### Post by rickparsons73 on 2014-08-23
Hi,

I am a relative newcomer to the world of Linux and Ubuntu, but I love(d) it when it was working.  I never had any problems until very recently.  I noticed that the last few attempts of (automatic) updating components would fail.  I thought I would reboot the machine and see if that helped (everything was still working as normal).  I rebooted and the GRUB 2 screen popped up (first time I had seen this).  It had a few options to choose from:

[LIST=1]
[*]Ubuntu
[*]Advanced options for Ubuntu
[*]memory test (memtest86+)
[*]memory test (memtest86+, serial console 115200)
[/LIST]

I initially chose #1.  The screen went black, with the cursor in the top left corner, then a massive amount of info went scrolling up the screen.  None of it made any sense to me.  When the scrolling stopped, the cursor remained at the bottom of the screen, but nothing happened from that point.  I waited about 20 minutes to see if anything was going to happen, but no.

I forced the shutdown of the machine and then turned it back on.  Once the computer went through its initial processes, I was brought back to the GRUB 2 menu.  This time I tried option #2 and chose one of the recovery modes, with the same result as when I chose option #1.

Started all over again, and this time chose the command prompt when I reached the GRUB 2 menu.  I did some googling of possible fixes on my other computer and found a few that involved rebooting from ISO files, etc.  I was in the middle of trying one when I realized that my machine wasn't recognizing my USB flash drive.  It also didn't recognize my external HD (also connected via USB), nor my DVD/CD-ROM drive.  Needless to say, any recovery option that required accessing external files was a waste.

Can anyone help me out here?  I'd really like to find a way to access my external drive/USB, and ultimately, suggestions on how to get up and running again would be greatly appreciated.  I've attached a photo of the screen that the system hangs on every time I try rebooting, in the hopes that someone else can make sense of the information shown on it.

I'm running Ubuntu on an HP Pavilion m9250f, with all of the stock components that came with it, other than I added a couple of internal hard drives (for a total of three).  8GB of RAM; nVidia GeForce 8600 GT graphics card; on board sound.  The system came loaded with Windows Vista before I replaced it with Ubuntu.

Thanks!

Rick

---

### Post by lah7 on 2014-08-24
Hi Rick. Welcome to the forums! As far as I'm aware, GRUB2 doesn't provide options for booting into external media without being configured to do so (it's not an automatic detection thing, it's simply a bootloader for the hard drive after all)

At the moment, it sounds like an update had drastically failed to a point the system is missing or holds broken packages, which is why your system will now kernel panic on every start-up.

In the *"Advanced Options for Ubuntu"* option, what's listed? Booting the system with an older listed kernel **might** work (in event it's a new kernel that failed to fully install) but there is a chance this may still kernel panic every time.

_To access your data:_ The easiest way is to use a live session. Insert your USB drive or disc containing Ubuntu and hold a specific key while your system turns on (such as **F12**, **ESC** or **F8**, depending on the manufacturer) which will load up your BIOS's boot menu and choose the relevant device to boot from. Alternately, you can access BIOS setup (**F2** or **DEL** usually) to change the boot order. The live session will boot to a fresh desktop allowing you to browse/copy your files to another drive. Note that anything saved inside the session itself will be lost when powered off.

This also is an opportunity to provide some logs here if you'd us to help you fix the start-up problem.
In the live session, ensure your hard drive is mounted (containing the problematic Ubuntu installation) and provide a copy of **/var/log/boot.log **and **/var/log/dmesg **(ensuring this isn't the one generated from the live session)

---

### Post by grahammechanical on 2014-08-24
We do not normally see the Grub boot menu when Ubuntu is the only OS on the machine. Unless we press the shift key during the very early stages of the boot process to specifically bring up the Grub boot menu.

The recovery menu gives us an option called Grub - Update Grub bootloader. Have you tried that? Pay attention to the on screen printout. It will show what OS (including Linux kernels) are being detected and needed to be put in the Grub boot menu. It might force Grub to re-write the location of the Linux kernels and the configuration files. That might help.

In all of this we are missing the point that you have made about the last few updates failing. Why did they fail? At the recovery mode menu we can select Network. That will establish a network (internet) connection. Then when we are back at the recovery menu we can select Root - root shell prompt and run these two commands. Again note the on screen printout of error messages. They will give a clue as to why Ubuntu has failed to update. Which was the original problem.

```
apt-get update
apt-get upgrade
```

Regards.

---

