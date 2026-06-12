---
title: "PC won't power-off nor reboot"
date: 2020-05-22
forum: General Help
---

### Post by satimis on 2020-05-22
Hi all,

It is just discovered that PC won't poweroff or reboot

This is the PC for daily working

OS - Ubuntu 18.04

Just discovered;
1. shutdown - the PC won't poweroff
2. reboot - won't reboot
3. press computer hard-reset key without response.

$ sudo lshw```

SCSI .....                       

```
hanging

$ hardinfo
see attached file - screenshot_hardinfo
SCSI                        

Please advise how to fix these problems which seem coming from Ubuntu 18.04

Thanks

Regards
satimis

---

### Post by Rex Bouwense on 2020-05-22
See my reply to [https://ubuntuforums.org/showthread.php?t=2443930](https://ubuntuforums.org/showthread.php?t=2443930).  Appears to be the same problem.

---

### Post by satimis on 2020-05-23
> **Rex Bouwense said:**
> See my reply to [https://ubuntuforums.org/showthread.php?t=2443930](https://ubuntuforums.org/showthread.php?t=2443930).  
Appears to be the same problem.
Hi,

Thanks for your link.

That is ONLY a temporary solution.

We are NOT alone encountering this problem.  Please see following link;
Ubuntu 18.04 stuck at shutdown
[https://askubuntu.com/questions/1029068/ubuntu-18-04-stuck-at-shutdown](https://askubuntu.com/questions/1029068/ubuntu-18-04-stuck-at-shutdown)

Their solutions couldn't work for me

Regards
satimis

---

### Post by ajgreeny on 2020-05-23
You do not show which kernel you're using  at present but if it is 5.3.0-53 that may well be your problem, many users with ryzen hardware  having had this same problem.

Why do you say their solutions can not work for you?

---

### Post by satimis on 2020-05-23
> **ajgreeny said:**
> You do not show which kernel you're using  at present but if it is 5.3.0-53 that may well be your problem, many users with ryzen hardware  having had this same problem.

Why do you say their solutions can not work for you?
Currently I'm running kernel 5.3.0-53 with problem on both "poweroff" and "reboot".  If running kernel 5.3.0-51 both "poweroff" and "reboot" work without problem.

I have tried following suggestions on that link on kernel 5.3.0-53
1)
sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_rev_override=1 nouveau.modeset=0"

sudo update-grub

2)
sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noacpi"

sudo update-grub


The problem on both "poweroff" and "reboot" remained.

Regards

---

### Post by ajgreeny on 2020-05-23
So why not just use the older kernel instead of the new one?

---

