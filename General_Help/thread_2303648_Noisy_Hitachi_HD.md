---
title: "Noisy Hitachi HD"
date: 2015-11-20
forum: General Help
---

### Post by ra7411 on 2015-11-20
I've got a 2tb Hitachi that's annoyingly noisy. It's only 2 months old and has been noisy from the start, it passes tests ok, so I don't think the HD is defective.

Can anything be done to quiet it down?

I'm using Ub 14.04.

---

### Post by mikewhatever on 2015-11-20
You can use **sudo hdparm -M 128 /dev/sdX** to quiet it. 
To check the current value see the output of **sudo hdparm -I /dev/sdX | grep Acoustic**.
Check out 'man hdparm' for more info.

---

### Post by ra7411 on 2015-11-20
> **mikewhatever said:**
> You can use **sudo hdparm -M 128 /dev/sdx** to quiet it. 

I tried it and got:

ra@raub:~$ sudo hdparm -M 128 /dev/sda
[sudo] password for ra: 


/dev/sda:
 setting acoustic management to 128
 HDIO_DRIVE_CMD:ACOUSTIC failed: Input/output error
 acoustic      = not supported
ra@raub:~$ 

Do I need to install something?

---

### Post by mikewhatever on 2015-11-20
How about you try something like this:

```

sudo hdparm -B 192 -M 128 /dev/sda

```

Some HDD do not support acoustic management when the power management is set to '-B 254', which usually is the default.

---

### Post by ra7411 on 2015-11-20
> **mikewhatever said:**
> How about you try something like this:

```

sudo hdparm -B 192 -M 128 /dev/sda

```

Some HDD do not support acoustic management when the power management is set to '-B 254', which usually is the default.

Here's what that gave:

ra@raub:~$ sudo hdparm -B 192 -M 128 /dev/sda
[sudo] password for ra: 


/dev/sda:
 setting Advanced Power Management level to 0xc0 (192)
 setting acoustic management to 128
 HDIO_DRIVE_CMD:ACOUSTIC failed: Input/output error
 APM_level	= off
 acoustic      = not supported
ra@raub:~$

---

### Post by tgalati4 on 2015-11-20
Read the reviews on the web for your specific model of disk drive.  Perhaps it is noisy by design and if others complain about it, then there may not be much you can do about it.

Are you using it for the operating system or is it just hosting static data?  If it is just hosting data on a separate partition, then perhaps you can spin it down with an *hdparm* command.

---

### Post by mikewhatever on 2015-11-20
Yea, looks like the firmware doesn't support acoustic management. Too bad.

---

