---
title: "Startup Problem"
date: 2015-05-14
forum: General Help
---

### Post by afrancis-ozonline on 2015-05-14
Since upgrading from 14.10 to 15.04 I keep getting the following message after booting:
" 0.7508221 ACPI PCC probe failed Starting version 219 "             
The number changes each time I boot but the message is always the same.
I have tried Recovery Mode but the problem persists.
Is the a fix for this?

---

### Post by iojedaperez on 2015-05-14
That message isnt related to the problem of the pc not booting. It seems you or the installer forgot to do a grub-update to reflect the new changes on boot. You should do a boot with a live cd and do a repair of the grub installation. If you dont know how you can follow this guide [http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)

---

### Post by afrancis-ozonline on 2015-05-18
Don't have a live cd I updated from 14.10 via Update Manager.

---

### Post by Vladlenin5000 on 2015-05-18
Just download the ISO and burn it to a USB flash (2GB minimum recommended).

---

### Post by afrancis-ozonline on 2015-05-20
OK so I downloaded Live CD and booted from it. The first thing I noticed was that a similar message came up namely: "[4.185343] ACPI probe failed" then a whole heap of other garbage saying unable to mount etc. then lit booted into CD went to try ubuntu but couldn't follow the instructions regarding finding the mount path for root partition. So I downloaded BOOT REPAIR and ran that, after it finished it said if I still had problems, which I have, I should post the following URL to this forum:
[http://paste.ubuntu.com/11238314](http://paste.ubuntu.com/11238314)
Does this make any sense?

---

### Post by Vladlenin5000 on 2015-05-20
No, it doesn't, because the link is wrong. Please check.

---

### Post by afrancis-ozonline on 2015-05-20
Pretty sure the link is not wrong. Anyway I perhaps should have mentioned in the first place that after some fiddling I can usually get into Ubuntu. I just tried the command "sudo fdisk -l" and this is the output:

Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0001a18b


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 237766655 237764608 113.4G 83 Linux
/dev/sda2       237768702 250068991  12300290   5.9G  5 Extended
/dev/sda5       237768704 250068991  12300288   5.9G 82 Linux swap / Solaris

Does this help identify the root partition?

---

### Post by Vladlenin5000 on 2015-05-21
What is the problem exactly? The error message? You can ignore it.

---

### Post by afrancis-ozonline on 2015-05-21
The exact problem is this: When I turn on the computer instead of booting into Ubuntu after a few seconds a grey screen appears with options for Ubuntu- Advanced Options- and 2 Memory Tests. If I do nothing then a black screen appears with white text which says "[ 0.7500481 ACPI PCC Probe failed. Starting version 219" then nothing else happens. If when the grey screen appears  and I arrow down to advanced options and click on recovery mode then it runs through the recovery and on completion I can hit return on Resume Normal Boot then the Ubuntu 15.04 screen appears as normal and I can login as usual. I really want things back to the normal boot without problems.
Thanks.

---

### Post by Vladlenin5000 on 2015-05-21
When you can login as usual - using an older kernel via recovery - is when you should perform a full update/upgrade. That most certainly will correct what currently is preventing you to login graphically with the current kernel you have.

---

### Post by afrancis-ozonline on 2015-05-22
OK so I tried the following commands in Terminal:
sudo apt-get  update
sudo apt-get upgrade
do -release -upgrade -d
Then it appeared do do a complete upgrade. At the end it read:
"The upgrade has completed but there were errors during the upgrade process" a Bug Report also popped up during the process and I clicked on repaort.
When I did a restart the familiar grey screen appeared and when I hit return on Ubuntu the also familiar black screen appeared with the message " [ 0.751601 ] ACPI probe failed", another restart and on the grey screen arrowing down to Recovery mode and running got me back to my Desktop. I then received the message " Sorry, a problem occurred while installing software. Package: Modemmanager when I clicked on Details it said Modemmanager 1.4.8-1 failed to install.

---

### Post by afrancis-ozonline on 2015-05-23
Tried "sudo apt-get update && apt-get upgrade" and the final lines of text said:
E: Could not open lock file /var/lib/dpkg/lock-open(l3:permission denied
E: Unable to lock the administration directory (var/lib/dpkg/) are you root
Nothing seems to have changed.

---

### Post by Vladlenin5000 on 2015-05-23
```
sudo apt-get update && **sudo** apt-get upgrade
```
 ;)

Both require "sudo", hence the permission denied error message.

---

### Post by afrancis-ozonline on 2015-05-24
Tried " sudo apt-get update && apt-get upgrade" and the only thing that changed is now i appear to have 15.10 on my hard drive, but to get into 15.04 I still have to go through going down to "Advanced options for Ubuntu" on the grey screen and then go through "Repair broken packaged" and "Update grub etc." before it will boot into 15.04. If I just hit return on "Ubuntu" on the grey screen a black screen comes up with the message: " [ 07514211 ACPI PCC Probe failed"

---

### Post by Vladlenin5000 on 2015-05-24
Wasn't having 15.10 your goal from the start?
That's what this command is for:```
do-release-upgrade [COLOR=#ff0000]-d[/COLOR]
```where "-d" stands for "development" as in the release yet to come, i.e., 15.10.
If that wasn't your goal, now it's too late, I'm afraid. TBH, I did notice the command when you posted but commented only about the other mistake, assuming that you knew what were you doing.

---

### Post by afrancis-ozonline on 2015-05-27
My goal was to have Ubuntu boot as normal which still doesn't happen.

---

### Post by Vladlenin5000 on 2015-05-27
It won't happen now, I'm afraid. I told you to do a full update but in the same version: It means the apt-get sequence update/upgrade/dist-upgrade only. The command you added, commented in post #15, upgraded to the development version thus deepening and expanding your original problem.

I suggest you boot a live session, do your backups (if you haven't already) and install from the scratch.

---

### Post by alikazmi-2040 on 2015-05-27
Which graphics card and driver are/were you using?

---

### Post by afrancis-ozonline on 2015-05-29
My graphics card is a NVIDIA GeForce GTS450.

---

### Post by Daliolores on 2015-07-20
```
sudo dpkg --configure -a
```

should solve the "modemmanager" thing after the upgrade.


then you could use

```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get upgrade && sudo apt-get install -f && sudo apt-get autoremove
```

to check everything is working properly.

---

