---
title: "Confirm in terminal if encrypted swap is being used"
date: 2013-08-06
forum: General Help
---

### Post by IbsUser on 2013-08-06
Hi,

What's the command line to confirm if my encrypted swap is being used correctly?

I have an encrypted /home and /swap and my Gparted also shows that /dev/sda5 is unknown too. /dev/sda5 is my swap too.

I'm using Lubuntu 13.04 32 bits and I asked to encrypt /home on installation.

My hardware is a Core 2 Duo T7300 @2Ghz, 3Gb of RAM. On manual partition I created /swap with 3Gb too.

From the output below I guess encrypted swap is active and in use:
```
sudo cryptsetup status /dev/mapper/cryptswap1
/dev/mapper/cryptswap1 is active and is in use.
  type:    PLAIN
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda5
  offset:  0 sectors
  size:    6291456 sectors
  mode:    read/write

```

However, from the outputs below I see there's no swap used:
```
cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/dm-0              partition    3145724    0    -1


```

```
sudo swapon -s
Filename                Type        Size    Used    Priority
/dev/mapper/cryptswap1  partition    3145724    0    -1

```

```
free -m
total       usado      livre    compart.  buffers     em cache
Mem:          3021       1600       1420          0         77       1034
-/+ buffers/cache:        488       2532
Swap:         3071          0       3071

```

Excerpt output from /fstab confirms encrypted swap is setup there:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# swap was on /dev/sda5 during installation
#UUID=ae171f3c-6163-4ca5-acfc-148d75751be8 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

My Conky reports swap usage is always 0%.

Htop reports 0 swap usage too while running Chromium-browser, Movie on VLC, Music on Audacious, Conky on background, LibreOffice Calc open with a spreadsheet, Pidgin, Leafpad, PCManFM, and Wine running Foxit Reader:
[IMG]http://i.imgur.com/HgfXVsj.png[/IMG]

The application gnome-disks shows 2 different informations:
1) /dev/sd5 is linux swap but content is unknown too, the same as GParted.

2) /dev/mapper/cryptswap1 is displayed as other devices, content is swap version 2, and it's in use according to gnome-disks.

However, the other outputs above are always 0 (zero).

And I have already read the following docs but I'm still not sure why my swap usage is always zero:

1) [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

2) [https://help.ubuntu.com/community/EncryptedFilesystems](https://help.ubuntu.com/community/EncryptedFilesystems)

3) [http://askubuntu.com/questions/17216/how-can-i-determine-if-just-the-private-folder-is-encrypted-or-the-whole-home-d](http://askubuntu.com/questions/17216/how-can-i-determine-if-just-the-private-folder-is-encrypted-or-the-whole-home-d)

Let me know if you need more info.

Thank you!

---

### Post by oldfred on 2013-08-06
I have 4GB of RAM and almost never use swap. With 3GB I think you might occasionally use some swap but it depends on how many active apps you load at once. 

My 64bit version installed on my laptop with only 1.5GB of RAM uses swap if I open more than a couple of large apps (screen goes gray for a second or two), but my normal use does not use much swap even with 1.5GB.

---

### Post by Bucky Ball on 2013-08-06
*Thread moved to **General Help**.*

A heads up. You do yourself no favours hijacking a thread that had all of twenty four hours action ten months ago and has been dead since. You do yourself no favours hijacking threads, period. 

Improve your chances of help, avoid confusion, be fair to the original poster, and post new threads in the appropriate sub-forums regarding your issues. Thanks. ;)

Good luck,
BB

PS: You can change the title of this thread for the next half hour by editing the first post and clicking 'Go Advanced'. If you miss that and can't change, let me know on the thread and I will change it for you. ;)

---

### Post by IbsUser on 2013-08-07
@Bucky Ball, sorry, I did not mean to hijack a thread. I really thought my issue is the same of the thread at [http://ubuntuforums.org/showthread.php?t=2057849](http://ubuntuforums.org/showthread.php?t=2057849). By luck I'm even using the same partition /dev/sda5 as swap.

Anyway, from comment #4 of the thread #2057849, and my outputs above together with the docs I listed above I still believe there might be a problem with my encrypted swap. 

Once I had already disabled encrypted swap  following the instructions from comments #8 and #9 of the thread [http://ubuntuforums.org/showthread.php?t=1454029](http://ubuntuforums.org/showthread.php?t=1454029) and after 3 or 4 days without rebooting my laptop, the OS started to use something like less than 1% of swap.

I'll leave the laptop with no reboots until the end of this week to monitor via htop how the swap usage goes and I'll report here then.

Thank you and sorry if I make any mistakes before.

Best regards!

---

### Post by Bucky Ball on 2013-08-07
All good. Mine shows exactly the same. Swap not being used. That's normal. Although, with all that going on on your machine, one might expect a tickle of activity ...

Generally there's nothing.

---

### Post by IbsUser on 2013-08-08
Hi,

After 1 day and 16 hours with no reboot, the encrypted swap is still 0 but now there's one small sign it may be working properly. 

Check the image below showing some output of htop:

[IMG]http://i.imgur.com/eBHsyWn.png[/IMG]

I'll keep monitoring for the next 2 or 3 days until I'm really sure that encrypted swap will show some usage different than zero. Next report in 2 or 3 days.

I know Lubuntu is extremelly fast and it has low footprint on RAM and CPU even on a daily usage running LibreOffice, Pidgin, Chromium-browser, Firefox, Audacious, Leafpad, PCManFM, Wine running Foxit Reader, Evince, and some stuff in the background such as Conky, Synapse, and Zeitgeist.

But I think it's strange some applications do not detect encrypted swap correctly. By now I know the following applications cannot detect the encrypted swap correctly:
1) Gparted: reports partition unknown;

2)```
sudo fdisk -l
```reports "Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table"

---

### Post by sudodus on 2013-08-08
Cryptswap looks good to me according to what you post, but I understand that you want to use it and check that it really works properly. You can reduce the available RAM with the [FONT=courier new]**mem=xxxM**[/FONT] boot option, where xxx is the number of MB RAM you allow the process to use:

Less RAM --> more swapping.

I used this method to test the installers with low RAM, and it should be possible to use for you now. Add the boot option in the grub entry (do it live by typing 'e' in the grub menu and add it after 'quiet splash' (if you have those default boot options).

Good luck :-)

Edit: I think ```
sudo parted -l
``` will recognize cryptswap.

---

### Post by IbsUser on 2013-08-08
Thank you for your suggestion sudodus! Worked like a charm.

I've reduced RAM to 512M and cryptswap started to be used when playing videos. 

The output of htop is showed below:
[IMG]http://i.imgur.com/RJB9Bpr.png[/IMG]

And the other output also confirms that cryptswap is detected as Linux swap:
```
sudo parted -l
Modelo: ATA ST500LM012 HN-M5 (scsi)
Disco /dev/sda: 500GB
Tamanho de setor (lógico / Físico): 512B/4096B
Tabela de Partição: msdos

Número  Início  Fim    Tamanho  Tipo      Sistema de arquivos  Sinalizador
 1      1049kB  106MB  105MB    primary   ntfs                 boot
 2      106MB   221GB  221GB    primary   ntfs
 3      221GB   243GB  21,5GB   primary   ext4
 4      243GB   500GB  257GB    extended
 5      243GB   246GB  3221MB   logical
 6      246GB   500GB  254GB    logical   ext4

Modelo: Mapeador de dispositivos Linux (crypt) (dm)
Disco /dev/mapper/cryptswap1: 3221MB
Tamanho de setor (lógico / Físico): 512B/4096B
Tabela de Partição: loop

Número  Início  Fim     Tamanho  Sistema de arquivos  Sinalizador
 1      0,00B   3221MB  3221MB   linux-swap(v1)

```

Some friendly links for some fellow that finds this thread useful and also needs to reduce RAM by changing boot arguments:
[http://ubuntuforums.org/showthread.php?t=1465554](http://ubuntuforums.org/showthread.php?t=1465554)
and
[http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html](http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html)

Best regards.

---

