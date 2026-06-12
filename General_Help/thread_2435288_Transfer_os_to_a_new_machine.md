---
title: "Transfer o/s to a new machine?"
date: 2020-01-18
forum: General Help
---

### Post by ra7411 on 2020-01-18
[COLOR=#000000][FONT=Arial]I'm going to be building a new computer in a few days and would like to avoid reinstalling  the operating system (Ub 1804), and the numerous apps that I have.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The new one is going to be a Ryzen 3 3200 cpu - the old one is an AMD cpu 4 + years old.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]This is a desktop  and the only driver incompatibility should be graphics, or will the mobo be a problem too?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]My guess is that  on the new machine, after plugging in the SSD drive that has the o/s on it,  then booting up with the install  usb, there should be a way to:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]- make the UUID number of the ssd compatible for the new machine[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- fix GRUB[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- get rid of the old graphics driver[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- install a new one for the Ryzen CPU.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I've already updated the o/s kernel  to 5.3.0-26.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Is this feasible or should I just go ahead and and do a new install?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Thanks[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by aljames2 on 2020-01-18
My answer may not be the best as I am a relatively new migrant from Windows to Ubuntu, so maybe get another opinion or two.  I would reinstall on the new hardware, that's me.  All the new hardware including the Mobo will be using new drivers/firmware.  There may be ways to do what you are asking.  However, the short time it takes to install Ubuntu and it's applications seems trivial compared to Windows.  Have backups of all your data and configuration files if any before starting.  But again let others chime in.

---

### Post by TheFu on 2020-01-18
Uninstall any proprietary GPU driver.  Pull the disk and install it in the other box.  Should work fine assuming the same boot method is used - UEFI/Legacy BIOS.  I've done exactly that with BIOS booting systems at least 20 times.

UEFI might complicate things.  I always use a new machine as a way to test my backup/recovery processes. When else do we have that chance with effectively zero risk?  Also, if the machine is smoking or stolen and all you have are the backups, then any replacement machine will be completely different hardware.  Backups that cannot be restored to different hardware aren't really all that useful, are they?

---

### Post by ra7411 on 2020-01-21
> **TheFu said:**
> Uninstall any proprietary GPU driver.  Pull the disk and install it in the other box.  Should work fine assuming the same boot method is used - UEFI/Legacy BIOS.  I've done exactly that with BIOS booting systems at least 20 times.

UEFI might complicate things.  I always use a new machine as a way to test my backup/recovery processes. When else do we have that chance with effectively zero risk?  Also, if the machine is smoking or stolen and all you have are the backups, then any replacement machine will be completely different hardware.  Backups that cannot be restored to different hardware aren't really all that useful, are they?

I thought there was 1/20 chance factor of it working that easily, but I tried it since there was nothing to lose.

I got the new hardware set up an hour ago, plugged the ssd with o/s in, booted up and just like magic -  IT WORKED.

The audio isn't perfect - a lot of squeaky background. I'll probably have to update the bios which I'm looking forward to about as much as a dental visit, but what the hell - so far, so good.

THANKS

---

### Post by TheFu on 2020-01-21
Do an apt update/upgrade cycle. That should pull any new CPU firmware.

I'm a little disappointed you didn't go with the backup --> restore method.  Everyone needs that plan. Storage devices fail all-the-time, without warning.

Anyways, please mark this thread "SOLVED" ----> Thread Tools button near the top.

---

