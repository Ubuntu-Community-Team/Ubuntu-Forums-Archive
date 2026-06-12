---
title: "Bios Recovery"
date: 2019-04-13
forum: General Help
---

### Post by wildmanne39 on 2019-04-13
Two months ago and again this morning I resumed my laptop and it failed, I had to do REISUB and upon restart both times the laptop did a bios recovery that took about five minutes to complete, is there a way to find out what is causing this to happen?

---

### Post by oldfred on 2019-04-13
What laptop?
UEFI or BIOS?

Generally installed system & UEFI/BIOS are not related. But with UEFI, now system can update some parameters. And a few Linux systems now support full UEFI upgrade.
But if BIOS, I do not understand a BIOS recovery. I have a system with dual BIOS/UEFI, but never have seen it do anything automatically.

---

### Post by wildmanne39 on 2019-04-13
HP Pavilion:
```
Manufacturer: HP
	Product Name: HP Pavilion Notebook 
	Version:  
	Serial Number: 5CD624B9S6
	UUID: 36444335-3432-3942-5336-EC8EB5432E26
	Wake-up Type: Power Switch
	SKU Number: N9E13UA#ABA
	Family: 103C_5335KV G=N L=CON B=HP S=PAV

```
I hope that helps, the sticker with the model number is wore off, it is about two and a half years old and only been used for about a year and a half.

Some times when I suspend the laptop but not often I get a blank screen and use REISUB to restart the laptop and the two times this happened it was under these circumstances.

Windows and Ubuntu both uses UEFI, the screen clearly says bios recovery is in progress, seems that there has been a failure when this happens, should the log file show such an occurrence after the laptop is booted back up? I am wondering if it is failing.

[https://support.hp.com/us-en/document/c04773111](https://support.hp.com/us-en/document/c04773111)

Thanks for your reply oldfred!

---

### Post by VMC on 2019-04-13
BIOS recovery sounds like a battery issue. I'm sure that's not the problem or you would have recovery if you powered off over night and tried again the next morning. 
When you say resumed, are you hybernating?

---

### Post by oldfred on 2019-04-13
I have seen some threads where users had issues recovering from suspend.

Have you updated UEFI from HP?
Some with HP have said UEFI update resolved some issues. Not sure if your issue or not.

[https://ubuntuforums.org/showthread.php?t=2395562](https://ubuntuforums.org/showthread.php?t=2395562)
[https://ubuntuforums.org/showthread.php?t=2410514](https://ubuntuforums.org/showthread.php?t=2410514)

Based on SKU:
[https://support.hp.com/us-en/document/c04773111](https://support.hp.com/us-en/document/c04773111)

---

### Post by wildmanne39 on 2019-04-13
> **VMC said:**
> BIOS recovery sounds like a battery issue. I'm sure that's not the problem or you would have recovery if you powered off over night and tried again the next morning. 
When you say resumed, are you hybernating?

I looked at the file that controls what the lid does and the lid action is still commented but I believe it is just suspending the laptop, the usb ports still work when the lid is closed.

Edit:

Oldfred I did upgrade the UEFI a few months ago if I remember correctly but I will check and make sure.

---

### Post by wildmanne39 on 2019-04-20
This has happened two more times since my last post, I upgraded the bios, but I know I did once before also, it looks like to me even though the update is showing successful I do not believe it is.

---

### Post by oldfred on 2019-04-21
This should show BIOS version you have.

sudo dmidecode --type bios

BIOS updates used to always reset everything.
With UEFI only some settings are updated.
But my motherboard has so many settings I have to keep a list. Only a few are required to make system work, but others seem to help, so I do those also.

---

### Post by Kris_M on 2019-04-21
install a new cmos battery?

---

### Post by wildmanne39 on 2019-04-21
Thanks oldfred, as I thought the bios upgrade did not stick I ran it again when the computer reboots it says purging the bios image and never installs the latest update.

Kris_M I do not think that is the issue, this has been happening with the laptop plugged in so as long as it is on cord power that would not be the cause would it? the hp site shows this issue but says to update the bios and see if that fixes the issue which I cannot get mine to update.

---

### Post by Kris_M on 2019-04-21
> **wildmanne39 said:**
> Thanks oldfred, as I thought the bios upgrade did not stick I ran it again when the computer reboots it says purging the bios image and never installs the latest update.

Kris_M I do not think that is the issue, this has been happening with the laptop plugged in so as long as it is on cord power that would not be the cause would it? the hp site shows this issue but says to update the bios and see if that fixes the issue which I cannot get mine to update.

Shouldn't, but then again...  dunno...

---

### Post by wildmanne39 on 2019-06-30
I am still having this issue, today I went into the system setup and there is an option to upgrade the bios from their, so I tried I received an error message that the checksum file is missing, corrupted or in a different file, I saw options to choose different files to try but I was afraid I would bork my system, from memory the options were, efi, boot, microsoft, windows, ubuntu, I am guessing it is in boot or efi, I am posting the output of:
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.6G     0  3.6G   0% /dev
tmpfs           749M  1.9M  747M   1% /run
/dev/sda5        78G   14G   61G  19% /
tmpfs           3.7G   96M  3.6G   3% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.7G     0  3.7G   0% /sys/fs/cgroup
/dev/loop0       35M   35M     0 100% /snap/gtk-common-themes/1122
/dev/loop1       89M   89M     0 100% /snap/core/7270
/dev/loop2       15M   15M     0 100% /snap/gnome-characters/288
/dev/loop3       54M   54M     0 100% /snap/core18/1013
/dev/loop4      2.0M  2.0M     0 100% /snap/fast/4
/dev/loop6      152M  152M     0 100% /snap/gnome-3-28-1804/55
/dev/loop7       54M   54M     0 100% /snap/core18/970
/dev/loop8      4.2M  4.2M     0 100% /snap/gnome-calculator/406
/dev/loop9       36M   36M     0 100% /snap/gtk-common-themes/1269
/dev/loop11     3.8M  3.8M     0 100% /snap/gnome-system-monitor/91
/dev/loop10     1.0M  1.0M     0 100% /snap/gnome-logs/61
/dev/loop13     2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop12     4.2M  4.2M     0 100% /snap/gnome-calculator/352
/dev/loop5       89M   89M     0 100% /snap/core/7169
/dev/loop14     8.5M  8.5M     0 100% /snap/canonical-livepatch/77
/dev/loop18      15M   15M     0 100% /snap/gnome-logs/45
/dev/loop19     8.5M  8.5M     0 100% /snap/canonical-livepatch/81
/dev/loop21     1.0M  1.0M     0 100% /snap/gnome-logs/57
/dev/loop22      15M   15M     0 100% /snap/gnome-characters/284
/dev/loop16     141M  141M     0 100% /snap/gnome-3-26-1604/86
/dev/loop23     152M  152M     0 100% /snap/gnome-3-28-1804/59
/dev/loop20     141M  141M     0 100% /snap/gnome-3-26-1604/88
/dev/loop15     3.8M  3.8M     0 100% /snap/gnome-system-monitor/87
/dev/loop17      36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/sda6       367G   75G  274G  22% /home
/dev/sda1       256M   72M  185M  28% /boot/efi
tmpfs           749M   80K  749M   1% /run/user/1000

``` 
I am thinking the file is here:
```
/dev/sda1       256M   72M  185M  28% /boot/efi
```
All input is appreciated.

Thanks

---

### Post by oldfred on 2019-06-30
My motherboard can update from within UEFI and can only read a FAT32 partition for update files. So when I download an update file to UEFI/BIOS, I save it into my ESP, since it is FAT32. Then I can read update file from that partition.

If UEFI only partially updated, you would not be able to boot at all and system would be broken. So either update not really done, or it is one of the newer dual BIOS that has a backup.

But not sure what else to suggest.

---

### Post by wildmanne39 on 2019-07-01
From what I have seen the update is removed at the end instead of being installed, I am just not sure where to go from here, every time the lid gets closed on my laptop or it freezes which is very rare that it freezes it starts the bios recovery again, my cat likes to close the lid, use to I could close it and the laptop resumed without issue so I am not sure what changed, thanks for your input oldfred.

---

