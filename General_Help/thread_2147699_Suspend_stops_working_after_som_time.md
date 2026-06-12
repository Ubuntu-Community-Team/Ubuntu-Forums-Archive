---
title: "Suspend stops working after som time"
date: 2013-05-22
forum: General Help
---

### Post by Morphyxx on 2013-05-22
Hello.

I'm using Ubuntu 12.04 and it works perfectly except when i suspend the computer.
If I return from suspended within a small amount of time say an hour it works just it is supposed to goes back to Ubuntu.
But if i wait longer than an hour the power led just blinks once and the computer turns off. I also have to press the power-button twice after this to be able to turn the computer on.

I'm dual-booting with Windows 8 and they are on different hard-drives.
I have a swap space at 1GB on the same hard-drive as Ubuntu.
My motherboard is: Asus SABERTOOTH P67

Does anyone know what the problem might be and if there exists a solution for it?

---

### Post by rtimai on 2013-08-07
Morphyxx, sorry you didn't get a timely response. This problem seems to occur with only a small number of hardware components. I recently tried the solution below after YEARS of avoiding 'suspend' -- same symptoms as you, 'resume' fails only after an extended period -- and FINALLY I can now suspend for hours and resume successfully. If you have similar video hardware, you might try this.

MY HARDWARE (use lspci to confirm your video card model)
:~$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4225/4250]

The fix is posted at
[http://askubuntu.com/questions/24048/suspend-fails-reboot-on-resume-and-no-hibernate-option](http://askubuntu.com/questions/24048/suspend-fails-reboot-on-resume-and-no-hibernate-option)

To fix resume-from-suspend failure with the open source xf86-video-ati (radeon) driver:
    gksu gedit /etc/default/grub &

Change the line:
GRUB_CMDLINE_LINUX=""
  to:
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs"

    sudo update-grub

NOTE: There is a different solution if you are running the proprietary ATI Catalyst video driver. See the link above. This is what worked on my system running the Open Source driver. BTW before this, I had to disconnect the power cord and take the battery out to reset before my HP dv6-3012he would wake up.

HTH, YMMV.

---

### Post by rtimai on 2013-08-08
FOLLOW-UP FAILURE
After multiple successful suspend-resume tests, there are still some instances when the HP dv6 does not resume. Resume succeeds when Suspend is forced from the Shutdown menu or by closing the laptop lid. When Suspend is triggered by Idle time-out, on Resume the HD spins up, CPU begins to heat up, but fails with black screen and unresponsive keyboard. So, this issue has been "improved" but NOT resolved by the acpi_sleep=nonvs option.

---

